<template>
  <div class="container">
    <div class="calc">
      <div class="display">
        <div class="expression">
          {{ expression }}
        </div>
        <div class="result">
          {{ result }}
        </div>
      </div>
      <div class="top-row-grid">
        <div class="operator" @click="clear">C</div>
        <div class="operator" @click="del">DEL</div>
      </div>
      <div class="operators-grid">
        <div class="operator" @click="buttonClick"> + </div>
        <div class="operator" @click="buttonClick"> ^ </div>
        <div class="operator" @click="buttonClick"> - </div>
        <div class="operator" @click="buttonClick">(</div>
        <div class="operator" @click="buttonClick">/</div>
        <div class="operator" @click="buttonClick">)</div>
        <div class="operator" @click="buttonClick">*</div>
      </div>
      <div class="numbers-grid">
        <div class="numbers-grid-m" @click="buttonClick">1</div>
        <div class="numbers-grid-m" @click="buttonClick">2</div>
        <div class="numbers-grid-m" @click="buttonClick">3</div>
        <div class="numbers-grid-m" @click="buttonClick">4</div>
        <div class="numbers-grid-m" @click="buttonClick">5</div>
        <div class="numbers-grid-m" @click="buttonClick">6</div>
        <div class="numbers-grid-m" @click="buttonClick">7</div>
        <div class="numbers-grid-m" @click="buttonClick">8</div>
        <div class="numbers-grid-m" @click="buttonClick">9</div>
        <div class="numbers-grid-m" @click="buttonClick">.</div>
        <div class="numbers-grid-m" @click="buttonClick">0</div>
        <div class="numbers-grid-m" @click="eval">=</div>
      </div>
    </div>
  </div>

</template>


<script>

  import {Parser} from "expr-eval";


  export default {
    name: "calculator",
    data() {
      return {
        expression: '22 + 23',
        result: '= 55'
      }
    },
    methods: {
      buttonClick(event) {
        console.log(`${event.currentTarget.innerHTML} clicked`)
        console.log(event.currentTarget.innerHTML)
        this.expression += event.currentTarget.innerHTML
      },
      clear(event) {
        console.log(`${event.currentTarget.innerHTML} clicked`)
        console.log(event.currentTarget.innerHTML)
        this.expression = ""
        this.result = ""
      },
      eval(event) {
        console.log(`${event.currentTarget.innerHTML} clicked`)
        let result = `= ${Parser.evaluate(this.expression)}`
        console.log(result);
        this.result = result;
      },
      del(event) {
        console.log(`${event.currentTarget.innerHTML} clicked`)
        this.expression = this.expression.slice(0, -1)
        console.log(result);
      }
    }
  }

</script>
<style scoped>
  .display {
    overflow-x: hidden;

    display: grid;
    grid-template-rows: 1fr 1fr;

    grid-column-start: 1;
    grid-column-end: 3;

    font-size: 12pt;
    margin: 5px;
    height: 50px;
    background: white;
    border-radius: 10px 10px;
  }

  .expression {
    line-height: 18pt;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    margin: 0 20px;
  }

  .result {
    display: flex;
    justify-content: flex-end;
    align-items: center;
    margin: 0 20px;
    font-size: small;
    color: green;
  }

  .container {
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .calc {
    display: grid;
    background: #d8f7d8;
    border-radius: 10px 10px;
  }

  .top-row-grid {
    grid-column-start: 1;
    grid-column-end: 1;
    grid-row-start: 2;
    grid-row-end: 2;
    display: grid;
    grid-template-rows: 1fr;
    grid-template-columns: 1fr 1fr 1fr;
  }

  .operators-grid {
    grid-column-start: 2;
    grid-column-end: 2;
    grid-row-start: 3;
    grid-row-end: 3;
    display: grid;
    grid-template-rows: 1fr 1fr 1fr 1fr;
    grid-template-columns: 1fr 1fr;
  }

  .operator {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 50px;
    width: 50px;
    margin: 5px;
    background: #c1c7d7;
    border-radius: 10px 10px;
    user-select: none;
  }

  .numbers-grid {
    grid-row-start: 3;
    grid-row-end: 3;
    display: grid;
    grid-template-rows: 1fr 1fr 1fr;
    grid-template-columns: 1fr 1fr 1fr;
  }

  .numbers-grid-m {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 50px;
    width: 50px;
    margin: 5px;
    background: #a2d7a7;
    border-radius: 10px 10px;
    user-select: none;
  }
</style>
