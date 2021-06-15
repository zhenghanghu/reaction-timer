<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
      click me 
  </div>
</template>

<script>
export default {
    props: ['delay'],
    data(){
        return {
            showBlock: false,
            reactionTime: 0,
            startTime: 0
        }
    },
    methods: {
        stopTimer(){
            this.reactionTime = Date.now() - this.startTime;
            this.$emit('end', this.reactionTime);
        }
    },
    mounted(){
        setTimeout(()=>{
            this.showBlock = true;
            this.startTime = Date.now();
        },this.delay)
    },
}
</script>

<style>
    .block{
        width: 400px;
        border-radius: 20px;
        background:  #0faf87;
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
    }
</style>