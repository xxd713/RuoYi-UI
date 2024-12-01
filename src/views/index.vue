<template>
  <div>
    <el-container>
      <!--      侧边栏-->
      <el-aside>
        <el-row>
          <el-col>
            <el-input
              placeholder="请输入设备型号"
              v-model="filterText">
            </el-input>
            <el-tree
              class="filter-tree"
              :data="data"
              :props="defaultProps"
              default-expand-all
              :filter-node-method="filterNode"
              ref="tree">
            </el-tree>
          </el-col>
        </el-row>
      </el-aside>
      <el-container>
        <el-header>
          <el-card shadow="never" align="center">
            设备名AMBKP02
          </el-card>
        </el-header>
        <el-main>
          <el-row :gutter="2">
            <el-col :span="5">
              <el-tag>设备状态</el-tag>
            </el-col>
            <el-col :span="5">
              <el-tag>EAP状态</el-tag>
            </el-col>
            <el-col :span="5">
              <el-tag></el-tag>
            </el-col>
            <el-col :span="5">
              <el-tag>这是显示的文字</el-tag>
            </el-col>
            <el-col :span="4">
              <el-tag>报警预设</el-tag>
            </el-col>
          </el-row>
        </el-main>
        <el-footer>Footer</el-footer>
      </el-container>
    </el-container>
  </div>
</template>

<script>
export default {
  name: "Index",
  watch: {
    filterText(val) {
      this.$refs.tree.filter(val);
    }
  },
  methods: {
    filterNode(value, data) {
      if (!value) return true;
      return data.label.indexOf(value) !== -1;
    }
  },
  data() {
    return {
      filterText: '',
      data: [{
        id: 1,
        label: '一级 1',
        children: [{
          id: 4,
          label: '二级 1-1',
          children: [{
            id: 9,
            label: '三级 1-1-1'
          }, {
            id: 10,
            label: '三级 1-1-2'
          }]
        }]
      }, {
        id: 2,
        label: '一级 2',
        children: [{
          id: 5,
          label: '二级 2-1'
        }, {
          id: 6,
          label: '二级 2-2'
        }]
      }, {
        id: 3,
        label: '一级 3',
        children: [{
          id: 7,
          label: '二级 3-1'
        }, {
          id: 8,
          label: '二级 3-2'
        }]
      }],
      defaultProps: {
        children: 'children',
        label: 'label'
      }
    };
  }
};
</script>

<style scoped lang="scss">
.el-card {
  margin: 0 auto;
}

.el-tag {
  width: 100%;
  text-align: center;
  font-size: 14px;
  color: #515a6e;
  height: 40px;
  line-height: 40px;
}
</style>

