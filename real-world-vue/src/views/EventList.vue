<template>
    <div>
        <h1>Events Listing</h1>
        <EventCard v-for="event in events" :event="event" :key="event.id" />
    </div>
</template>

<script>
import EventCard from '@/components/EventCard.vue';
import EventService from '@/services/EventService.js';

export default {
    components: {
        EventCard
    },
    data() {
        return {
            events: null
        };
    },
    created() {
        EventService.getEvents()
            .then(response => {
                this.events = response.data;
            })
            .catch(error => {
                console.log('There was an error : ', error.response);
            });
    }
};
</script>