<template>
   <div 
    v-bind:style="{backgroundColor: currentColor}" 
    class="cell"  @click="draw" 
    @mouseover="hovered">
       <!-- {{`${this.row},${this.col}`}} -->
   </div>
</template>

<script>

export default {
    name: 'Cell',
    props: {
        row: Number,
        col: Number,
    },
    data(){
       return {
        currentColor:'#fff',
       }
    },
    methods:{
        draw:function(){
            if(this.currentColor == '#fff'){
                this.currentColor = '#'+Math.floor(Math.random()*16777215).toString(16);
            } else {
                this.currentColor = '#fff'
            }
        },
        hovered: function(){
            this.$emit("hovered",this.row,this.col)
        }
    }
}
</script>
<style scoped>
.cell{
    height: 100%;  
    width:100%;
    overflow: hidden;
    /* background-color: #ff0; */
}
</style>
