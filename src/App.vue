<template>
  <h1>Wholesome Wahrheit oder Pflicht</h1>
  <p>Wie Wahrheit oder Pflicht - nur ohne sexuelle, grenzüberschreitende oder allgemein belastende Fragen!</p>
  <button @click="reroll()">NEUER PROMPT</button>
  <p id="prompt" v-if="prompt.text != ''"><b>{{prompt.type == "truth" ? "Wahrheit: " : "Pflicht: "}}</b>{{prompt.text}}</p>
</template>

<script>

export default {
  name: 'App',
  components: {
  },
  data() {
    return {
      prompt: {
        text: "",
        type: "dare"
      },
      prompts: {
        truth: [
          "Was ist eine Sache, die du an der Person links neben dir magst?",
        ],
        dare: [
          "Umarme alle, die umarmt werden wollen!",
        ]
      }
    }
  },
  methods: {
    reroll(){
      let promptType = Math.floor(Math.random() * 2) ? "truth" : "dare";
      let prompts = this.$data.prompts[promptType];
      this.$data.prompt.text = prompts[Math.floor(Math.random() * prompts.length)];
      this.$data.prompt.type = promptType;
    }
  },
}
</script>

<style lang="scss">
@import '@fontsource/poppins/400.css';
@import '@fontsource/poppins/600.css';
@import '@fontsource/poppins/800.css';

body{
  background-color: #b7ebc7;
  margin: 2rem;
}
#app {
  background-color: #e9f6ed;
  box-shadow: 0px .5rem 1.5rem -.5rem #78bb8d;
  font-family: "Poppins", Avenir, Helvetica, Arial, sans-serif;
  font-size: 1rem;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #000000;
  border-radius: 1rem;
  padding: 1rem;
  max-width: 500px;
  margin: auto;
}
button{
  padding: .5rem;
  background-color: #b7ebc7;
  color: #000000;
  font-weight: 900;
  border: 0px transparent none;
  border-radius: .5rem;
  font-size: 1rem;
  cursor: pointer;
  transition: 120ms;
  &:hover{
    background-color: #93daa8;
  }
  &:active{
    background-color: #75c88e;
  }
}
b{
  font-weight: 600;
}
#prompt{
  padding: 1rem;
  background: #d0f6db;
  box-shadow: 0px 8px 16px -8px #78bb8d inset;
  border-radius: 1rem;
  margin-bottom: 0px;
}
</style>
