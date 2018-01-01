<template>
  <div id="app">
    <div class="video"></div>
    <div class="tab">
      <div class="tab-item active">测试一</div>
      <div class="tab-item">测试二</div>
      <div class="tab-item">测试三</div>
    </div>
    <section class="chat">
      <article class="chat-list" v-for="(index, item) in arclist">{{index}}</article>
    </section>
    <div class="chat-input">
      <textarea name="" id="" class="chat-text" @focus="scrollContent" @blur="clearSrcoll" ref="textinput"></textarea>
      <button @click="t" class="btn">提交</button>
    </div>
  </div>
</template>

<script>
/* eslint-disable no-new */
export default {
  name: 'app',
  data: () => {
    return {
      interval: 0,
      arclist: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    }
  },
  methods: {
    scrollContent () {
      this.interval = setInterval(() => {
        this.scrollToEnd()
      }, 500)
    },
    scrollToEnd () {
      document.body.scrollTop = document.body.scrollHeight
    },
    clearSrcoll () {
      clearInterval(this.interval)
    },
    t () {
      console.log(this.$refs.textinput.value)
      this.arclist.push(this.$refs.textinput.value)
      this.$refs.textinput.value = ''
    }
  },
  mounted () {
    // console.log(this.$refs.onfocus = () => {
    //   console.log(this)
    // })
  }
}
</script>

<style>
*{margin:0;padding:0;}
html, body {height:100%;width: 100%;-webkit-overflow-scrolling : touch;-webkit-apperance:normal;-webkit-appearance:none;}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height:100%;
  width:100%;
  display: flex;
  flex:1;
  flex-direction: column;
}

.video{
  height:4rem;
  background:#438bca;
}
.tab{
  height:.78rem;
  display: flex;
  flex-direction: row;
}
.tab .tab-item{
  display: flex;
  flex:1;
  font-size:.2rem;
  align-items: center;
  justify-content: center;
  font-size: .32rem
}
.tab .active{
  border-bottom:2px solid #F56C6C;
}
.chat{display: flex;flex:1;flex-direction: column;overflow-y: auto;}
.chat .chat-list{margin-top:.2rem;}

.chat-input{
  height:.78rem;
  border-top:1px solid #e6e6e6;
  display: flex;
  flex-direction: row;
  align-items: center;
    padding: 0 .12rem;
}
.chat-input .chat-text{
  border:none;
  outline: none;
  -webkit-appearance:none;
    -webkit-tap-highlight-color: transparent;
      border: 1px solid #E6E6E6;
    height: .4rem;
    border-radius: .1rem;
    display:flex;
    flex:1;
    resize: none;
    padding:.1rem .1rem;
    font-size:.34rem;
}

.chat-input .btn{    
  border:none;
  width: 1.2rem;
    background: #F56C6C;
    border: none;
    height: .62rem;
    border-radius: .1rem;
    margin-left: .12rem;color:#fff;font-size:.2rem;}
</style>
