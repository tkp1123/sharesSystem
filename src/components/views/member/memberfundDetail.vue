<template>
  <div>
    <el-card class="box-card">
      <el-page-header @back="goBack" content="会员资金明细"></el-page-header>
      <el-row :gutter="30">
        <el-form :inline="true" :model="formInline" class="demo-form-inline">
          <el-form-item label="会员手机号">
            <el-input
              v-model="formInline.mobile"
              placeholder="会员手机号"
            ></el-input>
          </el-form-item>
          <el-form-item label="会员名称">
            <el-input
              v-model="formInline.name"
              placeholder="会员名称"
            ></el-input>
          </el-form-item>
          <el-form-item label="单号">
            <el-input
              v-model="formInline.orderId"
              placeholder="单号"
            ></el-input>
          </el-form-item>
          <el-form-item>
            <el-button type="primary" @click="onSubmit">查询</el-button>
            <el-button type="primary" @click="onReset">重置</el-button>
          </el-form-item>
        </el-form>
      </el-row>
      <el-row>
        <el-table :data="tableData" border stripe style="width: 100%">
          <el-table-column prop="holdOrderId" label="单号"></el-table-column>
          <el-table-column prop="summary" label="摘要"></el-table-column>
          <el-table-column prop="amount" label="金额"></el-table-column>
          <el-table-column prop="cumulative" label="累计金额"></el-table-column>
          <el-table-column
            prop="createdTime"
            label="创建时间"
          ></el-table-column>
          <el-table-column
            prop="updatedTime"
            label="更新时间"
          ></el-table-column>
        </el-table>
        <el-row>
          <el-pagination
            @size-change="handleSizeChange"
            @current-change="handleCurrentChange"
            :current-page="currentPage4"
            :page-sizes="[100, 200, 300, 400]"
            :page-size="100"
            layout="total, sizes, prev, pager, next, jumper"
            :total="400"
          ></el-pagination>
        </el-row>
      </el-row>
    </el-card>
  </div>
</template>
<script>
export default {
  //会员资金明细
  name: 'memberfundDetail',
  data() {
    return {
      queryInfo: '',
      currentPage1: 5,
      currentPage2: 5,
      currentPage3: 5,
      currentPage4: 4,
      formInline: {
        mobile: '',
        name: '',
        orderId: '',
      },
      tableData: [
        {
          holdOrderId: '12323534232654456',
          summary: '头寸分润',
          amount: 12.34,
          cumulative: 0,
          createdTime: '2020-10-11',
          updatedTime: '2020-10-12',
        },
        {
          holdOrderId: '12323534232654456',
          summary: '头寸分润',
          amount: 12.34,
          cumulative: 24.68,
          createdTime: '2020-10-11',
          updatedTime: '2020-10-12',
        },
        {
          holdOrderId: '12323534232654456',
          summary: '头寸分润',
          amount: 12.34,
          cumulative: 37.02,
          createdTime: '2020-10-11',
          updatedTime: '2020-10-12',
        },
        {
          holdOrderId: '12323534232654456',
          summary: '头寸分润',
          amount: 12.34,
          cumulative: 49.36,
          createdTime: '2020-10-11',
          updatedTime: '2020-10-12',
        },
        {
          holdOrderId: '12323534232654456',
          summary: '头寸分润',
          amount: 12.34,
          cumulative: 61.7,
          createdTime: '2020-10-11',
          updatedTime: '2020-10-12',
        },
      ],
    }
  },
  methods: {
    handleSizeChange(val) {
      console.log(`每页 ${val} 条`)
    },
    handleCurrentChange(val) {
      console.log(`当前页: ${val}`)
    },
    onSubmit() {
      console.log(this.formInline)
    },
    onReset() {
      this.formInline.name = ''
      this.formInline.mobile = ''
      this.formInline.orderId = ''
    },
    goBack() {
      console.log('go back')
    },
  },
}
</script>
<style lang="less" scoped>
.el-table {
  margin-top: 15px;
  font-size: 14px;
}
.el-pagination {
  padding-top: 20px;
}
.demo-form-inline {
  padding-left: 15px;
}
.el-page-header {
  padding: 0 20px 30px 0;
}
</style>