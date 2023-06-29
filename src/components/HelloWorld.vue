<template>
  <div>
    <form @submit="submitForm">
      <label for="name">Name:</label>
      <input type="text" id="name" v-model="user.name" required />

      <label for="email">Email:</label>
      <input type="email" id="email" v-model="user.email" required />

      <label for="phone">Phone:</label>
      <input type="tel" id="phone" v-model="user.phone" required />

      <button type="submit">Submit</button>
    </form>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      user: {
        name: "",
        email: "",
        phone: "",
      },
    };
  },
  methods: {
    submitForm() {
      axios
        .post("https://example.com/api", this.user)
        .then((response) => {
          console.log(response.data);
          // Handle success
        })
        .catch((error) => {
          console.error(error);
          // Handle error
        });
    },
  },
};
</script>