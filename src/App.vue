<template>
  <div id="app">
    <div class="form">
      <input class="input" :value="username" @input="updateUsername" />
      <input class="input" :value="password" @input="updatePassword" />
      <button class="submit" @click="submit">Sign up</button>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'app',
  data() {
    return {
      username: '',
      password: '',
    };
  },
  methods: {
    updateUsername(event) {
      this.username = event.target.value;
    },
    updatePassword(event) {
      this.password = event.target.value;
    },
    async submit() {
      // probably add some other business logic here :)
      await axios.post('https://jsonplaceholder.typicode.com/users', {
        username: this.username,
        password: this.password,
      });
      alert('User created');
    },
  },
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.input {
  padding: 10px;
  font-size: 12px;
  outline: none;
  margin: 10px 0;
}

.form {
  display: flex;
  flex-direction: column;
  width: 30vw;
  margin: auto;
}

.submit {
  padding: 10px;
  border: none;
  background: #00aced;
  color: #fff;
  font-size: 15px;
}
</style>
