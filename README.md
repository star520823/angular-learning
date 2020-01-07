# angular-learning

根据官方文档加深学习angular

# 1、初始化项目

## 1、创建工程(less)

```
ng new xxx --style less
```

## 2、引入ng-zorro-antd

```
ng add ng-zorro-antd --theme
```

## 3、引入jquery

```
npm install --save jquery
npm install @types/jquery --save-dev
angular.json 文件里面添加jquery对应的js依赖。"./node_modules/jquery/dist/jquery.min.js"
tsconfig.app.json文件的types属性中添加"jquery"
```

## 4、引入bootstrap

```
npm install --save bootstrap
npm install @types/bootstrap --save-dev
angular.json 文件里面添加jquery对应的js依赖。"./node_modules/jquery/dist/bootstrap.min.js"
angular.json 文件里面添加jquery对应的css。"./node_modules/bootstrap/dist/css/bootstrap.min.css"
```

## 5、引入echarts

### 1、第一种方式

```
npm install --save echarts
npm install @types/echarts --save-dev
angular.json 文件里面添加jquery对应的js依赖。"./node_modules/echarts/dist/echarts.min.js"
```

```html
<div id="main" style="width:400px;height:300px;"></div>
```

```typescript
ngOnInit(): void {
    const myChart = echarts.init(document.getElementById('main') as HTMLDivElement);
    const option = {
      title: {
        text: 'ECharts 入门示例'
      },
      tooltip: {},
      legend: {
        data: ['销量']
      },
      xAxis: {
        data: ['衬衫', '羊毛衫', '雪纺衫', '裤子', '高跟鞋', '袜子']
      },
      yAxis: {},
      series: [{
        name: '销量',
        type: 'bar',
        data: [5, 20, 36, 10, 10, 20]
      }]
    };
    // 使用刚指定的配置项和数据显示图表。
    myChart.setOption(option);
  }
```

### 2、第二种方式:包含第一种方式的导入

```
npm install --save echarts
npm install ngx-echarts --save
npm install @types/echarts --save-dev
angular.json 文件里面添加jquery对应的js依赖。"./node_modules/echarts/dist/echarts.min.js"
app.module.ts中引入NgxEchartsModule，import { NgxEchartsModule } from 'ngx-echarts';
```

```typescript
chartOption = {
    title: {
      text: '堆叠区域图'
    },
    tooltip: {
      trigger: 'axis'
    },
    legend: {
      data: ['邮件营销', '联盟广告', '视频广告', '直接访问', '搜索引擎']
    },
    toolbox: {
      feature: {
        saveAsImage: {}
      }
    },
    grid: {
      left: '3%',
      right: '4%',
      bottom: '3%',
      containLabel: true
    },
    xAxis: [
      {
        type: 'category',
        boundaryGap: false,
        data: ['周一', '周二', '周三', '周四', '周五', '周六', '周日']
      }
    ],
    yAxis: [
      {
        type: 'value'
      }
    ],
    series: [
      {
        name: '邮件营销',
        type: 'line',
        stack: '总量',
        areaStyle: { normal: {} },
        data: [120, 132, 101, 134, 90, 230, 210]
      },
      {
        name: '联盟广告',
        type: 'line',
        stack: '总量',
        areaStyle: { normal: {} },
        data: [220, 182, 191, 234, 290, 330, 310]
      },
      {
        name: '视频广告',
        type: 'line',
        stack: '总量',
        areaStyle: { normal: {} },
        data: [150, 232, 201, 154, 190, 330, 410]
      },
      {
        name: '直接访问',
        type: 'line',
        stack: '总量',
        areaStyle: { normal: {} },
        data: [320, 332, 301, 334, 390, 330, 320]
      },
      {
        name: '搜索引擎',
        type: 'line',
        stack: '总量',
        label: {
          normal: {
            show: true,
            position: 'top'
          }
        },
        areaStyle: { normal: {} },
        data: [820, 932, 901, 934, 1290, 1330, 1320]
      }
    ]
  }；
```

```html
<div echarts [options]="chartOption" class="demo-chart"></div>
```

```css
.demo-chart{
    position: relative;
    width: 400px;
    height: 400px;
}
```

