<template>
  <div class="hello">
    <h1>Dad Jokes</h1>
    <p>{{ joke }}</p>

    <button @click="getJoke()">Get random joke</button>
  </div>
</template>

<script>
import axios from  'axios';
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      joke: 'I need a random joke....'
    }
  },
  methods: {
    getJoke() {
      axios.get('https://icanhazdadjoke.com', {
        headers: {'Accept': 'application/json'},
        responseType: 'json'
      })
      .then((resp) => {
        this.joke = resp.data.joke;
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
