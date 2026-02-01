# D014 鸟类知识图谱问答系统vue+django+neo4j (python实现）问答系统LTP实现全源码

> 完整项目收费，可联系QQ: 81040295 微信: mmdsj186011 注明从git来的，谢谢！
也可以关注我的B站： 麦麦大数据 https://space.bilibili.com/1583208775
> 

up主B站：  **麦麦大数据**
关注B站，有好处！

编号:  D014
**可以定制其他数据**
## 视频

[video(video-dsJgEDwh-1758356465967)(type-bilibili)(url-https://player.bilibili.com/player.html?aid=916836245)(image-https://i-blog.csdnimg.cn/img_convert/693f55a5230cfcfb476316649155dee1.jpeg)(title-vue+django 鸟类知识图谱问答系统)]
## 1 系统简介
系统简介：本系统是一个基于Vue.js、Django、MySQL和Neo4j构建的鸟类知识图谱可视化与问答系统，其核心功能围绕鸟类知识的展示、检索和问答展开。主要包括知识图谱功能，允许用户浏览和理解鸟类之间的生物学概念关系；模糊检索功能，支持用户通过关键词进行不精确查询；问答系统，提供关于鸟类分类（如科、目、纲）和分布地区的信息。同时，系统还包含用户管理模块，包括登录、注册、修改个人信息、头像和密码等功能，确保用户个性化和安全的使用体验。
## 2 功能设计
该系统采用典型的B/S架构模式，用户通过浏览器访问由Vue.js构建的前端界面。前端利用Vuex进行状态管理，Vue Router处理路由导航，并使用Echarts等图表库实现数据可视化。前端通过RESTful API与Django后端交互，后端处理业务逻辑并与MySQL数据库进行结构化数据存储，同时利用Neo4j存储和查询鸟类知识图谱的非结构化数据，为问答系统提供支持。此外，系统包含数据爬虫和预处理模块，负责抓取和整理鸟类数据，构建知识图谱并通过数据融合技术确保数据的一致性和准确性，全面支撑系统功能。
### 2.1系统架构图
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/c90b19e5c1514e668a4bb3a4516b64fd.png)
### 2.2 功能模块图
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/573469a835394f5d9b5f10505b908f93.png)
## 3 功能展示
### 3.1 登录 & 注册
登录界面背景是一个视频，展示和本文系统主题相匹配的内容，登录和注册界面在一个界面下，通过按钮来切换，注册界面输入用户名和密码，会检查这个用户是否存在，登录界面则要检查用户名是否存在以及用户名密码是否正确：![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/535062d42b37424da14760b08085a247.png)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/329b7f87c3994cc6995364834e377901.png)
### 3.2 主页
如果通过校验，则可以进入主页，在主页是一个左侧菜单，右侧操作面板的布局，右上角是登录用户的头像和退出按钮：
### 3.3 知识图谱
neo4j 界面展示知识图谱：
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/a6e445cd152b4ed9976b6d6c45c77fbd.png)
本利用echarts实现的知识图谱可视化：
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/7a25245dbb064d05bb744a6e7ccd6197.png)
支持输入关键词进行知识图谱的检索，从而展示子图：
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/7a2093ac86d745468dd5b1b06a5bd39a.png)
### 3.4 智能问答
基于LTP+neo4j知识图谱的问答系统，可以问各类问题：
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/12929921197a4a3f9ad43bacdbfbe3ca.png)

### 3.5 个人设置
个人设置方面包含了**用户信息修改**、**密码修改**功能。
用户信息修改中可以上传头像，完成用户的头像个性化设置，也可以修改用户其他信息。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/d126f2b90b4342749d770ad445ae5cd3.png)
修改密码需要输入用户旧密码和新密码，验证旧密码成功后，就可以完成密码修改。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/0a4f7221636f4d63ba06148fb307cb96.png)
## 4程序代码
### 4.1 代码说明
代码介绍：
数据结构：代码中定义了一个层级化的鸟类分类数据结构，展示了鸟纲下的雁形目、鸡形目等分类，直至具体物种如家鸭和Ringneck Pheasant。
可视化配置：使用ECharts的树状图（tree）组件，实现了鸟类分类的层级展示。配置包括图表标题、节点样式、标签位置、交互功能（如展开/收缩）和动画效果。
交互功能：用户可以点击节点进行展开或收缩操作，查看不同层级的分类信息。图表支持缩放和平移，方便用户浏览大规模的分类树。
样式定制：节点使用空心圆圈样式，标签文字清晰易读，整体布局美观。
动态加载：图表在组件挂载时自动初始化和渲染，数据可根据实际需求动态替换或扩展。
### 4.2 流程图
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/bc91e104fe494d8da431f99a96c116eb.png)


### 4.3 代码实例
```python
// 在Vue组件中
<template>
  <div id="bird-taxonomy" style="width: 100%; height: 600px;"></div>
</template>

<script>
import * as echarts from 'echarts'

export default {
  mounted() {
    // 初始化图表
    const chart = echarts.init(document.getElementById('bird-taxonomy'))
    
    // 定义鸟类分类数据
    const data = {
      name: '鸟纲',
      children: [{
        name: '雁形目',
        children: [{
          name: '鸭科',
          children: [{
            name: '家鸭'
          }]
        }]
      }, {
        name: '鸡形目',
        children: [{
          name: '雉科',
          children: [{
            name: 'Ringneck Pheasant'
          }]
        }]
      }]
    }

    // 配置图表
    const option = {
      title: {
        text: '鸟类生物学分类',
        subtext: '知识图谱展示'
      },
      series: [{
        type: 'tree',
        data: [data],
        layout: 'dendrogram',
        symbol: 'emptyCircle',
        symbolSize: 20,
        label: {
          position: 'inside',
          fontSize: 12
        },
        expandAndCollapse: true,
        animation: true
      }]
    }

    chart.setOption(option)
  }
}
</script>

```

---
## 联系方式
