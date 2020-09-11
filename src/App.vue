<template>
  <div id="app">
    <!-- 头部 -->
    <el-container class="container">
    <el-header height="56px" class="header"> 
      <div class="title">
        {{title}}
      </div>
    </el-header>
    <el-container>
      <!-- 左侧 -->
      <el-aside width="200px" class="left-aside">
        <!-- 左侧导航 -->
        <el-menu
          @select="currenthandler"
          default-active="1"
          class="el-menu-vertical-demo">
          <!-- 导航1 -->
          <el-menu-item index="1">
            <i class="el-icon-s-home"></i>
            <span slot="title">总览</span>
          </el-menu-item>
          <!-- 导航2 -->
          <el-menu-item index="2">
            <i class="el-icon-s-custom"></i>
            <span slot="title">顾客管理</span>
          </el-menu-item>
          <!-- 导航3 -->
            <el-menu-item index="3">
            <i class="el-icon-menu"></i>
            <span slot="title">栏目管理</span>
          </el-menu-item>
          <!-- 导航4 -->
            <el-menu-item index="4">
            <i class="el-icon-s-goods"></i>
            <span slot="title">产品管理</span>
          </el-menu-item>
          <!-- 导航5 -->
            <el-menu-item index="5">
            <i class="el-icon-s-operation"></i>
            <span slot="title">订单管理</span>
          </el-menu-item>
        </el-menu>
        <!-- /左侧导航 -->
      </el-aside>
      <!-- 右侧 -->
      <el-main>
        <component v-bind:is="currentViews"></component>
      </el-main>
    </el-container>
  </el-container>
  </div>
</template>

<script>
import Customer from './views/Customer'
import Product from './views/Product'
import Categry from './views/Categry'
export default {
  name: 'app',
  data() {
    return {
      title:"E洁家政服务平台",
      currentViews:"Customer"
    }
  },
  components: {
   Customer,
   Product,
    Categry
  },
  methods: {
    currenthandler(index){
      switch(index){
        case "1":
          this.currentViews="";
          break;
        case "2":
          this.currentViews="Customer"
          break;
        case "3":
          this.currentViews="Categry"
          break;
        case "4":
          this.currentViews="Product"
          break;
        case "5":
          this.currentViews=""
          break;
      }
    }
  },
}
</script>

<style>
.container{
  position: absolute;
  width: 100%;
  top:0;
  bottom: 0;
}
.container>.header{
  background-color: #30619e;
  color: #ffff;
  
}
.header>.title{
  line-height: 56px;
  font-size: 18px;
  font-weight: 500;
  }
  .left-aside{
    border-right: 1px solid #efefef;
  }
</style>
