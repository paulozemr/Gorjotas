<script>
export default {
  data() {
    return {
      valorConta: 0,
      Gorjeta: 15,
      numPessoas: 1,
    };
  },
  methods: {
    calcular() { 
      const valorConta = this.valorConta;
      const Gorjeta = this.Gorjeta;
      const numPessoas = this.numPessoas;
      let valorGorjeta = 0;
      let valorTotal = {};

      valorGorjeta = valorConta * (Gorjeta / 100);
      valorTotal = (valorConta + valorGorjeta) / numPessoas;

      valorTotal = Math.round(valorTotal * 100) / 100;
      valorTotal = valorTotal.toFixed(2);

      console.log(valorTotal);

      document.getElementById("resultado").innerHTML = valorTotal;
    },
  },
};
</script>

<template>
  <div class="main">
    <h1>
      <i><strong>"Quick-Tip"</strong></i>
    </h1>

    <form>
      <label>
        <p>Qual o preço do jantar?</p>
        <input type="number" v-model="valorConta" id="valorConta" />
      </label>

      <label>
        <p>Qual a gorjeta?</p>
        <select v-model="Gorjeta" id="valorGorjeta">
          <option value="30">Excelente!</option>
          <option value="25">Otimo!</option>
          <option value="20">Bacana!</option>
          <option value="15">Na Media</option>
          <option value="10">Ruim</option>
          <option value="5">Horroroso</option>
        </select>
        <p>Porcentagem da gorjeta</p>
        <input id="mostratip" type="number" disabled v-model="Gorjeta" />
      </label>

      <label>
        <p>Quantas pessoas vão dividir a conta?</p>
        <input v-model="numPessoas" type="number" id="numPessoas" />
      </label>

      <label>
        <p>Calcular:</p>
        <button type="button" @click="calcular">
          R$:<span id="resultado">0.00</span>
        </button>
      </label>
    </form>
  </div>
</template>

<style scoped>
.main {
  position: absolute;
  top: 50%;
  color: black;
  left: 50%;
  transform: translate(-50%, -50%);
  text-align: center;
  padding: 25px;
  border-radius: 2px;
  box-shadow: rgba(50, 50, 93, 0.25) 0px 50px 100px -20px,
    rgba(0, 0, 0, 0.3) 0px 30px 60px -30px, rgba(10, 37, 64, 0.35) 0px -2px 6px 0px inset;
  border: solid;
  animation: borda-gay 5s infinite;
}
@keyframes borda-gay {
 0% {
    color: red;
  }
  50% {
    color: blue;
  }
  100% {
    color: red;
  }
}
h1 {
  font-size: 50px;
  animation: color-change 1s infinite;
}
@keyframes color-change {
  0% {
    color: red;
  }
  50% {
    color: blue;
  }
  100% {
    color: red;
  }
}
input,
select {
  margin-bottom: 30px;
}

input,
select,
button {
  width: 250px;
  height: 25px;
  font-size: 18px;
  border: 1px black solid;
  border-radius: 2px;
  text-align: center;
  transition: 0.25s;
  cursor: pointer;
}

button {
  background-color: #32a838;
  height: 50px;
  font-size: 24px;
  margin-bottom: 10px;
}

button:hover {
  background-color: #32a838;
}

#mostratip {
  width: 40px;
  margin-bottom: 10px;
  height: 40px;
}
</style>
