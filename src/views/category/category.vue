<template>
  <div class="category-page page">
    <div class="page-content">

      <!--&lt;!&ndash;主体&ndash;&gt;-->
      <!--<div class="col-main">-->
        <!--&lt;!&ndash;文章列表&ndash;&gt;-->
        <!--<article-list></article-list>-->
      <!--</div>-->

      <!--&lt;!&ndash;侧边栏&ndash;&gt;-->
      <!--<my-aside></my-aside>-->

      <el-row class="page-content">
        <el-col :xs="24" :sm="17" class="col-main"><article-list :articleListParams="articleListParams"></article-list></el-col>
        <el-col :xs="24" :sm="7"> <keep-alive><my-aside></my-aside></keep-alive></el-col>
      </el-row>
    </div>
  </div>
</template>
<script>
  import myAside from '../../components/myAside/myAside.vue'
  import articleList from '../../components/articleList/articleList.vue'
  import {bus} from '../../main.js'

  export default {
    data() {
      return {
        articleListParams: {
          listType: '分类',
          pageNo: 1,
          pageSize: 5,
          categoryType: 1,
          tagType: 0
        }
      }
    },
    created() {
      bus.$on('currentPage', (page) => {
        console.log('目录列表当前页' + page)
      })
    },
    components: {
      myAside,
      articleList
    }
  }
</script>
<style lang="scss">
</style>
