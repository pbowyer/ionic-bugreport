<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-title>Inbox</ion-title>
      </ion-toolbar>
    </ion-header>
    
    <ion-content :fullscreen="true">
      <ion-refresher slot="fixed" @ionRefresh="refresh($event)">
        <ion-refresher-content></ion-refresher-content>
      </ion-refresher>
      
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Inbox</ion-title>
        </ion-toolbar>
      </ion-header>
      
      <ion-item lines="full">
      <ion-label position="stacked">DOB</ion-label>
      <ion-datetime
        presentation="date"
        prefer-wheel="true"
        required="true"
      ></ion-datetime>
    </ion-item>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonItem, IonLabel, IonDatetime, IonContent, IonHeader, IonList, IonPage, IonRefresher, IonRefresherContent, IonTitle, IonToolbar } from '@ionic/vue';
import MessageListItem from '@/components/MessageListItem.vue';
import { defineComponent } from 'vue';
import { getMessages } from '@/data/messages';

export default defineComponent({
  name: 'HomePage',
  data() {
    return {
      messages: getMessages()
    }
  },
  methods: {
    refresh: (ev: CustomEvent) => {
      setTimeout(() => {
        ev.detail.complete();
      }, 3000);
    }
  },
  components: {
    IonItem,
    IonLabel,
    IonDatetime,
    IonContent,
    IonHeader,
    //IonList,
    IonPage,
    IonRefresher,
    IonRefresherContent,
    IonTitle,
    IonToolbar,
    //MessageListItem
  },
});
</script>
