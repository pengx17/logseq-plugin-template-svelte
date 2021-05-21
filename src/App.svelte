<script lang="ts">
  let inner: Element;
  let show = true;

  logseq.on("ui:visible:changed", async ({ visible }) => {
    show = visible;
  });

  const clickOutside = (e: Event) => {
    if (!inner.contains(e.target as any)) {
      window.logseq.hideMainUI();
    }
  };
</script>

{#if show}
  <main on:click={clickOutside}>
    <div bind:this={inner} class="inner" />
  </main>
{/if}

<style>
  main {
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    position: fixed;
    padding: 10vh 5vw;
    backdrop-filter: saturate(0.8) blur(10px);
  }
</style>
