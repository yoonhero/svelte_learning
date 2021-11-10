<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  export let name;
  export let points;
  let showControls = false;

  const addPoint = () => points++;
  const removePoint = () => points--;
  const toggleControls = () => (showControls = !showControls);
  const onDelete = () => dispatch("removeplayer", name);
</script>

<div class="card">
  <h1>
    {name}
    <button class="btn btn-sm" on:click={toggleControls}>
      {#if showControls}-{:else}+{/if}
    </button>

    <button class="btn btn-danger" on:click={onDelete}>x</button>
  </h1>
  <h3>{points}</h3>
  {#if showControls}
    <button class="btn" on:click={addPoint}>+1</button>
    <button class="btn btn-dark" on:click={removePoint}>-1</button>

    <input type="number " bind:value={points} />
  {/if}
</div>

<style>
  h1 {
    color: #204f6e;
  }

  h3 {
    margin-bottom: 10px;
  }
</style>
