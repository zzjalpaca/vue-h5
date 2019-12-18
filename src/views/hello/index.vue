<template>
  <div>
    <div>点赞数：{{supportNum}}</div>
    <div>反对数：{{againstNum}}</div>
    <div v-for="item in listData" :key="item.id">
      <div>{{item.name}}</div>
      <div>{{item.status}}</div>
      <van-radio-group v-model="item.status">
        <van-radio name="1" checked-color="#07c160" @click="support(item.id, item.status)">赞成</van-radio>
        <van-radio name="0" checked-color="#07c160" @click="against(item.id, item.status)">反对</van-radio>
      </van-radio-group>
    </div>

  </div>
</template>

<script>
import Vue from 'vue';
import { RadioGroup, Radio } from 'vant';

Vue.use(RadioGroup);
Vue.use(Radio);
export default {
  data() {
    return {
      supportNum: 0,
      againstNum: 0,
      radio: '1',
      listData: [
        {
          id: 1,
          name: '庆余年',
          status: '1'
        },
        {
          id: 2,
          name: '庆余年11',
          status: '1'
        },
        {
          id: 3,
          name: '庆余年12',
          status: '1'
        },
        {
          id: 4,
          name: '庆余年13',
          status: '1'
        }
      ]
    }
  },
  mounted() {
    this.getNum()
  },
  methods: {
    support(id, status) {
      this.getNum()
    },
    against(id, status) {
      this.getNum()
    },
    getNum() {
      let supportData = this.listData.filter(item => item.status === '1')
      this.supportNum = supportData.length
      this.againstNum = this.listData.length - this.supportNum
    }
  },
}
</script>

<style lang="less" scoped>

</style>
