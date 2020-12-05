<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld :message="message"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'app',
  data: function () {
    return {
      message: 'Loading...'
    }
  },
  components: {
    HelloWorld
  },
  methods:  {
    getData: async function () {
      try {
        let data = await (await fetch('api')).json()
        this.message = data.message
      } catch (err) {
        this.message = err.message
      }
    }
  },
  mounted: function () {
    this.getData()
  }
}
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
</style>
