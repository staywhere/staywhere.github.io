<template>
  <div class="level-bread">
    <el-breadcrumb separator="/">
      <el-breadcrumb-item v-for="item in realList" :key="item.index" :to="item.path">{{item.name}}</el-breadcrumb-item>
    </el-breadcrumb>
  </div>
</template>

<script>
export default {
  name: "lelve-bread",
  created() {
    this.getRoutePath();
  },
  data() {
    return {
      realList: []
    };
  },
  methods: {
    getRoutePath() {
      this.realList = this.$route.meta.routeList;
    }
  },
  beforeRouteEnter(to, from, next) {
    next(vm => {
      vm.realList = to.meta.routeList;
    });
  }
  // watch:{
  //   $route:function(newV,oldV) {
  //     this.realList =newV.meta.routeList;
  //   }
  // }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang='scss' scoped>
</style>
