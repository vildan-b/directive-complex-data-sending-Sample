<template>
  <div class="container">
    <div class="col-md-6 col-md-offset-3">
      <h3>directive complex data sending Sample </h3>
      <button v-custom-on:click="clicked"class="btn btn-success">Click </button>
    <div class="customOn" v-custom-on:mouseleave="mouseleave" v-custom-on:mousemove="mousemove" ></div>
    </div>
  </div>
</template>

<script>
export default {
  directives : {
    customOn: {
      bind(el, binding){
        const type = binding.arg; 
        const fn= binding.value;

        el.addEventListener(type, fn);
        el.onclick = function(){
          binding.value();
        }

      }
    }
  },
  methods:{
    clicked(){
      alert("tiklandi...");
    },
      mousemove(){
        console.log("mousemove")
      },
       mouseleave(){
        console.log("mouseleave")
      }
  }
}
</script>

<style>
.customOn {
  width: 100px;
  height: 100px;
  border: 1px dashed #666;
}
</style>
