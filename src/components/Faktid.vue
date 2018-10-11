<template>
  <div>
    <h1>Numbri faktid</h1>
    <p>Huvitavad faktid iga numbri kohta</p>
    <input type="number" min="0" v-model="number">
    <input type="number" v-model="inc">
    <p>{{ data }}</p>
    <ul>
      <li></li>
    </ul>
  </div>
</template>

<script>
const axios = require ('axios')
export default {
  name: 'Faktid',
  data () {
    return {
      data: '',
      number: 0,
      inc:0,
      counter: '',
    }
  },
  methods: {
      //number () {}  on ka method
      getFact() {
        if (this.number !== '' && this.inc !== '') {
      let url = `http://numbersapi.com/`;
      let secondUrl = `${url}${this.number}..${parseInt(this.number) + parseInt(this.inc)}`;
      
      axios.get(secondUrl)
      .then(response => {
        this.data = response.data
      })
      .catch(error => {
          console.log(error)
      })
      }
      }
  },
  watch: { /*kutsub esile*/
    number() {
      this.getFact()
    },
   
    inc() {
      this.getFact()
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    
</style>
