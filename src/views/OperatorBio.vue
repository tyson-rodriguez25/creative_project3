<template>
<div class="Bio">
  <router-link v-for="operator in operators" :key="operator.operator" :to="'/operatorbio/' + operator.operator">
  <OperatorList>
  <img :src="'/images/Operators/' + operator.image">
  <h1>{{operator.operator}}</h1>
  <h2>{{operator.role}}</h2>
  <h2>{{operator.name}}</h2>
  <h2>{{operator.gadget}}</h2>
  <h3>Bio</h3>
  <p>{{operator.Bio}}</p>
  </OperatorList>
  </router-link>
</div>
</template>

<script>
import OperatorList from "../components/OperatorList.vue"
export default {
  name: 'Bio',
  computed: {
    products() {
      return OperatorList.shuffle(this.$root.$data.operators);
    }
  },
  components: {
    OperatorList
  },
  props: {
    operatorList: String
  },
  data() {
  return {
    random: 0,
  }
  },
  created() {
    this.operator = this.$root.$data.operator.find(operator => operator.id === parseInt(this.$route.params.id));
    this.random =
      Math.floor(Math.random() * 90) + 10;
  }
}
</script>

<style>
.Bio img {
  width: 40%;
}
</style>
