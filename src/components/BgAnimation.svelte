<script>
  import { onMount } from 'svelte';
  import { gsap } from 'gsap';
  import { ScrollTrigger } from 'gsap/ScrollTrigger';
  
  gsap.registerPlugin(ScrollTrigger);

  let showBackground = true;

  onMount(() => {
    if (window.innerWidth < 720) {
      showBackground = false;
      return;
    };
    const tl = gsap.timeline({
      scrollTrigger: {
        trigger: 'body',
        start: 'top top',
        end: '1000px',
        scrub: true,
        markers: false,
      },
    });
    tl.to('.background-container', {
      opacity: 0,
    });
  });
</script>

{#if showBackground}
<div class="background-container"></div>
{/if}

<style>
  .background-container {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100vh;
    background-image: url('../images/monorawg-bg.webp');
    background-position: center center;
    background-repeat: no-repeat;
    background-size: cover;
    z-index: -1;
    opacity: 1;
  }
</style>