<script>
import { afterUpdate } from 'svelte';

import { polarplot } from '../polarplot.js';

export let boat;

let container;
let plot;

afterUpdate(() => {
    if (!plot) {
        plot = polarplot(container);
    }
    plot.render(boat);
});
</script>

<div bind:this={container} />
<svelte:window on:resize={() => plot && plot.resize()} />
