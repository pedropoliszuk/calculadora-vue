<script setup>
  import { reactive } from "vue";

  const estado = reactive({ 
    operacao: "multiplicacao",
    numero1: 0,
    numero2: 0,
  });

  const multiplicacao = ({numero1, numero2}) => {
    return numero1 * numero2;
  };

  const divisao = ({numero1, numero2}) => {
    return numero1 / numero2;
  };

  const adicao = ({numero1, numero2}) => {
    return numero1 + numero2;
  };

  const subtracao = ({numero1, numero2}) => {
    return numero1 - numero2;
  };

  const conta = () => {
    const { numero1, numero2, operacao } = estado;
    
    if (numero1 !== null && numero2 !== null && numero1 !== 0 && numero2 !== 0) {
      switch (operacao) {
        case "multiplicacao":
          return multiplicacao({numero1, numero2});
        case "divisao":
          return divisao({numero1, numero2});
        case "adicao":
          return adicao({numero1, numero2});
        case "subtracao":
          return subtracao({numero1, numero2});
        default:
          return null;
      } 
    } else {
        return null;
      }
  };
</script>

<template>
  <div class="container">
    <header class="p-5 mb-4 mt-4">
      <h1>Calculadora</h1>
      <p>Digite os números e escolha a operação</p>
    </header>
    <form>
      <div class="row d-flex align-items-center">
        <div class="col d-flex gap-2">
          <input @input="estado.numero1 = Number($event.target.value)" class="form-control" type="number">
          <input @input="estado.numero2 = Number($event.target.value)" class="form-control" type="number">
        </div>
        <div class="col">
          <select @change="estado.operacao = $event.target.value" class="form-control text-center">
            <option value="adicao">Adição</option>
            <option value="subtracao">Subtração</option>
            <option value="multiplicacao">Multiplicação</option>
            <option value="divisao">Divisão</option>
          </select>
        </div>
      </div>
      <h3 class="mt-4">O resultado é {{ conta() }}</h3>
    </form>
  </div>
</template>

<style scoped>

</style>
