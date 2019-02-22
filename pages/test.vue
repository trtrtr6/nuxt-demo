<template>
  <section class="container">
    <div>
      <h1>{{test}}</h1>
      <nuxt-link to="./">标签导航到首页</nuxt-link>
      <nuxt-link to="test?title=ceshi">test?title=ceshi</nuxt-link>
      <button @click="navto">编程式导航到首页</button>
      <button @click="btn1">测试</button>
    </div>
  </section>
</template>

<script>
import axios from 'axios'
export default {
  async asyncData (context) {
    const query = context.query 
    // console.log(context)
    // console.log(query)
    const r = await axios.get(`/api/json`)
    console.log(r)
    return {
      test:query.title
    }
  },
  data(){
    return {
      title:'testtdsjfsdjk'
    }
  },
  head () {
    return {
      title: this.title,
      meta: [
        { hid: 'description', name: 'description', content: 'My custom description' }
      ]
    }
  },
  methods:{
    navto(){
      this.$router.push('/')
    },
    btn1(){
      this.test="测试"
    }
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
