<template>
  <div class="chat-app">
    <conversation :contact="selectedContact" :messages="messages" />
    <contactList :contacts="contacts" />
  </div>
</template>
 
   
<script>
import Conversation from "./Conversation";
import ContactList from "./ContactList";

export default {
  props: {
    user: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      selectedContact: null,
      messages: [],
      contacts: []
    };
  },
  mounted() {
    console.log(this.user);
    axios.get("/contacts").then(response => {
      console.log(response.data);
      this.contacts = response.data;
    });
  },
  components: { Conversation, ContactList }
};
</script>
