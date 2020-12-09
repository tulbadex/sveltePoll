<script>
    // There is easy way to unsubscribe to the store
    // import { onMount, onDestroy } from 'svelte';
    import {blur, fade, fly, scale, slide} from 'svelte/transition';
    import {flip} from 'svelte/animate';
    import PollStore from '../stores/PollStore.js';
    import PollDetails from './PollDetails.svelte';
    
    // export let polls = [];

    /* const unsub = PollStore.subscribe(data => {
        polls = data;
    });

    onDestroy( () => {
        console.log();
        unsub();
    }); */
</script>

<div class="poll-list">
    {#each $PollStore as poll (poll.id)}
        <div in:fade out:scale|local animate:flip={{ duration: 500}}>
            <PollDetails {poll} /> 
            <!-- on:vote -->
        </div>
    {/each}
</div>

<style>
    .poll-list{
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-gap: 20px;
    }
</style>