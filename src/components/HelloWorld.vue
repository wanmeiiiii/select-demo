<template>
  <div class="hello">
    <select class="select" @click="showSelectBox">
      <option class="option" selected>{{ select }}</option>
    </select>
    <div class="selectBox selectBoxShow" v-show="selectShowAble">
      <div class="selectBoxHeader">
        <div
          :class="{head: true,headColor:pullGetOptions.length === item }"
          v-for="item in count"
          :key="item"
          @click="changeGetOptionsList(item)"
        >{{ item }}</div>
      </div>
      <div class="selectBoxMain">
        <ul>
          <li v-for="item in getOptions" :key="item.value" @click="liShow(item)">{{ item.label }}</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      select: '',
      selectShowAble: false,
      getOptions: [],
      // 上tab栏存储显示的数组及对应层级
      pullGetOptions: [],
      selectArr: [],
      count: 5,
      options: [
        {
          value: 'zhinan',
          label: '指南',
          children: [
            {
              value: 'shejiyuanze',
              label: '设计原则',
              children: [
                {
                  value: 'yizhi',
                  label: '一致',
                  children: [
                    {
                      value: 'yizhi',
                      label: '一致',
                      children: [
                        {
                          value: 'yizhi',
                          label: '一致'
                        },
                        {
                          value: 'fankui',
                          label: '反馈'
                        },
                        {
                          value: 'xiaolv',
                          label: '效率'
                        },
                        {
                          value: 'kekong',
                          label: '可控'
                        }
                      ]
                    }
                  ]
                },
                {
                  value: 'fankui',
                  label: '反馈'
                },
                {
                  value: 'xiaolv',
                  label: '效率'
                },
                {
                  value: 'kekong',
                  label: '可控'
                }
              ]
            },
            {
              value: 'daohang',
              label: '导航',
              children: [
                {
                  value: 'cexiangdaohang',
                  label: '侧向导航'
                },
                {
                  value: 'dingbudaohang',
                  label: '顶部导航'
                }
              ]
            }
          ]
        },
        {
          value: 'zujian',
          label: '组件',
          children: [
            {
              value: 'basic',
              label: 'Basic',
              children: [
                {
                  value: 'layout',
                  label: 'Layout 布局'
                },
                {
                  value: 'color',
                  label: 'Color 色彩'
                },
                {
                  value: 'typography',
                  label: 'Typography 字体'
                },
                {
                  value: 'icon',
                  label: 'Icon 图标'
                },
                {
                  value: 'button',
                  label: 'Button 按钮'
                }
              ]
            },
            {
              value: 'form',
              label: 'Form',
              children: [
                {
                  value: 'radio',
                  label: 'Radio 单选框'
                },
                {
                  value: 'checkbox',
                  label: 'Checkbox 多选框'
                },
                {
                  value: 'input',
                  label: 'Input 输入框'
                },
                {
                  value: 'input-number',
                  label: 'InputNumber 计数器'
                },
                {
                  value: 'select',
                  label: 'Select 选择器'
                },
                {
                  value: 'cascader',
                  label: 'Cascader 级联选择器'
                },
                {
                  value: 'switch',
                  label: 'Switch 开关'
                },
                {
                  value: 'slider',
                  label: 'Slider 滑块'
                },
                {
                  value: 'time-picker',
                  label: 'TimePicker 时间选择器'
                },
                {
                  value: 'date-picker',
                  label: 'DatePicker 日期选择器'
                },
                {
                  value: 'datetime-picker',
                  label: 'DateTimePicker 日期时间选择器'
                },
                {
                  value: 'upload',
                  label: 'Upload 上传'
                },
                {
                  value: 'rate',
                  label: 'Rate 评分'
                },
                {
                  value: 'form',
                  label: 'Form 表单'
                }
              ]
            },
            {
              value: 'data',
              label: 'Data',
              children: [
                {
                  value: 'table',
                  label: 'Table 表格'
                },
                {
                  value: 'tag',
                  label: 'Tag 标签'
                },
                {
                  value: 'progress',
                  label: 'Progress 进度条'
                },
                {
                  value: 'tree',
                  label: 'Tree 树形控件'
                },
                {
                  value: 'pagination',
                  label: 'Pagination 分页'
                },
                {
                  value: 'badge',
                  label: 'Badge 标记'
                }
              ]
            },
            {
              value: 'notice',
              label: 'Notice',
              children: [
                {
                  value: 'alert',
                  label: 'Alert 警告'
                },
                {
                  value: 'loading',
                  label: 'Loading 加载'
                },
                {
                  value: 'message',
                  label: 'Message 消息提示'
                },
                {
                  value: 'message-box',
                  label: 'MessageBox 弹框'
                },
                {
                  value: 'notification',
                  label: 'Notification 通知'
                }
              ]
            },
            {
              value: 'navigation',
              label: 'Navigation',
              children: [
                {
                  value: 'menu',
                  label: 'NavMenu 导航菜单'
                },
                {
                  value: 'tabs',
                  label: 'Tabs 标签页'
                },
                {
                  value: 'breadcrumb',
                  label: 'Breadcrumb 面包屑'
                },
                {
                  value: 'dropdown',
                  label: 'Dropdown 下拉菜单'
                },
                {
                  value: 'steps',
                  label: 'Steps 步骤条'
                }
              ]
            },
            {
              value: 'others',
              label: 'Others',
              children: [
                {
                  value: 'dialog',
                  label: 'Dialog 对话框'
                },
                {
                  value: 'tooltip',
                  label: 'Tooltip 文字提示'
                },
                {
                  value: 'popover',
                  label: 'Popover 弹出框'
                },
                {
                  value: 'card',
                  label: 'Card 卡片'
                },
                {
                  value: 'carousel',
                  label: 'Carousel 走马灯'
                },
                {
                  value: 'collapse',
                  label: 'Collapse 折叠面板'
                }
              ]
            }
          ]
        },
        {
          value: 'ziyuan',
          label: '资源',
          children: [
            {
              value: 'axure',
              label: 'Axure Components'
            },
            {
              value: 'sketch',
              label: 'Sketch Templates'
            },
            {
              value: 'jiaohu',
              label: '组件交互文档'
            }
          ]
        }
      ]
    }
  },
  created () {
    this.getOptionsList(this.options)
    this.pullGetOptions.push(this.getOptions)
  },

  methods: {
    getOptionsList (arr) {
      this.getOptions = arr
    },
    // 显现下拉框
    showSelectBox () {
      this.selectShowAble = !this.selectShowAble
    },
    // 盒子切换
    liShow (item) {
      // 去除selectArr中的空白字符串
      this.selectArr = this.selectArr.filter(item => item !== '')
      if (this.selectArr.length < this.count) {
        // 如果两个数组的长度相等(相当于用户在原先一个没有children的选项里,想选择另一个选项)
        if (this.selectArr.length === this.pullGetOptions.length) {
          this.selectArr.splice(this.pullGetOptions.length - 1)
        }
        if (item.children) {
          this.getOptionsList(item.children)
          this.pullGetOptions.push(this.getOptions)
        } else {
          this.selectArr.length = this.count
          // 关闭下拉盒子
          this.selectShowAble = false
        }
        this.selectArr.push(item.label)
      } else if ((this.selectArr.length = this.count)) {
        // 改变该层级中的选项
        this.selectArr.splice(this.selectArr.length - 1, 1, item.label)
        // 关闭下拉盒子
        this.selectShowAble = false
      }
    },
    // 上tap点击事件
    changeGetOptionsList (item) {
      this.pullGetOptions.splice(item)
      this.getOptions = this.pullGetOptions[this.pullGetOptions.length - 1]
      this.selectArr.splice(item - 1)
    }
  },
  watch: {
    selectArr (newVal) {
      this.select = newVal.filter(item => item !== '').join('/')
    },
    // 如果该级只有一条对象,则默认选中该项,且跳转到下一层级
    getOptions (newVal) {
      if (newVal.length === 1) {
        this.liShow(newVal[0])
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
ul {
  list-style: none;
  padding: 0;
  li {
    height: 30px;
    line-height: 30px;
    margin-left: 10px;
    font-size: 14px;
    border-bottom: 1px solid #000;
  }
}
.select {
  width: 300px;
  height: 30px;
  .option {
    display: none !important;
  }
}
.selectBox {
  width: 300px;
  height: 500px;
  background-color: red;
  z-index: 999;
  .selectBoxHeader {
    height: 40px;
    line-height: 40px;
    text-align: center;
    background-color: blue;
    .head {
      width: (1/5) * 100%;
      height: 40px;
      border: 1px solid #000;
      box-sizing: border-box;
      float: left;
      &.headColor {
        background-color: yellow;
      }
    }
  }
}
</style>
