# HTML

#### 1.常见的语义化标签

```html
/* 语义化标签有利于SEO */
<header><header/>   //头部
<footer><footer/>   //尾部
<aside><aside/>     //两侧
<article><article/> //文章
<section><section/> //文章里的段落
<nav><nav/>			//导航栏
```

#### 2.HTML5 新特新

- audio video canvas标签
- session、localStorage本地存储
- websocket
- drag API
- location API
- web-work  web-service
- 创建cache mainfest文件实现离线缓存
- 增强表单

#### 3.script 标签中 defer 和 async 的区别

​	两者都是异步加载脚本的方法，让主线程在加载html和css的时候异步加载脚本，区别是带有defer标签的脚本会先加载然后等待主线程加载完后立即执行脚本，而async是当脚本加载完后会夺回主线程执行权立即执行脚本，所以defer脚本一定是按顺序执行，async不一定是按顺序执行，哪个脚本先加载完就先执行哪个脚本。

#### 4.标签上 title 与 alt 属性的区别是什么

​	当用户鼠标放到元素上停滞时会显示一个title内容的tips，当元素加载失败的时候显示alt的内容。

#### 5.iframe 是什么,有什么优缺点

​	ifream可以在网页中内嵌网页，优点是可以内嵌多个页面，并且有需要改动的地方去相应的项目去修改即可，缺点是不利于SEO、会阻塞主页面的onload事件，ifream和主页会共享网页的连接池。

#### 6.href 与 src 的区别

​	href表示当前文档和资源建立关系，src用于将资源下载到文档之中。

#### 7.什么是 BFC

​	BFC(块级格式上下文)是一个独立渲染的区域，规定了内部行块盒的布局方式，BFC内的元素不会影响到外面元素。

​	BFC可以防止外边距重叠、清除浮动、解决高度坍塌问题。

​	BFC的形成条件有：

- float不为none
- display：inline-block、flex、grid、table
- position为absolute或fixed
- overflow不为visible
- 根元素

#### 8.DOCTYPE(⽂档类型) 的作⽤

​	用来告诉浏览器以什么方式来解析文档，有两种模式：

- 标准模式（浏览器使用W3C的标准解析渲染页面。在标准模式中，浏览器以其支持的最高标准呈现页面）

- 怪异模式（浏览器使用自己的怪异模式解析渲染页面。在怪异模式中，页面以一种比较宽松的向后兼容的方式显示）

#### 9.常⽤的 meta 标签有哪些

```html
//描述html的编码格式
<meta charset="UTF-8" > 
//页面关键词
<meta name="keywords" content="关键词"/>
//页面描述
<meta name="description" content="页面描述内容" />
//页面重定向
<meta http-equiv="refresh" content="0;url=" />
//适配移动端，可以控制视口的大小和比例
<meta 
	name="viewport"
	content="width=device-width //视口宽度与设备一致
	initial-scale=1   //初始缩放比例为1
	user-scalable=no  //用户不能放大或缩小网页
	maximum-scale=1  // 兼容 iOS10 不支持 user-scalable,导致用户仍可缩放
	minimum-scale=1"
/>
```

#### 10.行盒块盒有哪些，区别是什么

​	行盒按水平顺序排列，行盒不能设置宽高，宽高由内容撑开

```html
//行盒
<span><span/>
<i><i/>
<input><input/>
<a><a/>
<img><img/>
<b><b/>
<em><em/>
```

​	块盒独占一行，默认按照垂直放下一次排列

```html
//块盒
<div><div/>
<p><p/>
<ul><ul/>
<ol><ol/>
<li><li/>
<h1><h1/>
...
<h6><h6/>
<table><table/>
<thead><thead/>
<tbody><tbody/>
<th><th/>
<tr><tr/>
<td><td/>
```

#### 11.空元素是什么，有哪些

​	空元素指的不能有子元素并且没有闭合标签的元素

```html
<img>
<input>
<link>
<meta>
<br>
```

#### 12.web worker 是什么

​	web worker是运行在浏览器后台的一个独立线程，可以唤起该线程来实现浏览器多线程执行脚本，但是该线程和主线程的全局上线文不是一样的，worker线程没有window对象不能操作dom，document对象也不存在。

​	worker线程和主线程通信方式如下：

```js
//main.js
const myWorker = new Worker(./worker.js);
//监听message事件获取worker线程发送的消息
window.addEventListener('message',(e)=>{
    console.log(e.data);
})
//调用postMessage方法向worker线程发送消息
myWorker.postMessage("hello worker");

//worker.js
//监听message事件获取主线程发送的消息
self.onmessage = (e)=>{
	console.log(e.data);
}
//调用postMessage方法向主线程发送消息
self.postMessage("hello main");
```

#### 13.HTML5 的离线储存怎么使用

​	使用HTML5的离线存储需要在html标签上添加mainfest属性引用缓存清单文件，项目中添加mainfest文件 

```html
//index.html
<html mainfest="/mainfest.appcache">
```

```
CACHE MAINFEST

/* 要缓存的文件 */
CACHE:
index.html

/* 其它文件要求在线 */
NETWORK:

/* 某个文件无法下载时 使用的备用文件 */
FALLBACK:
index.html fallback.html
```

#### 14.title 与 h1 的区别、b 与 strong 的区别、i 与 em 的区别

- title标签可以改变页面标题名称，h1是语义化标签表示一级标签。
- b元素定义粗体文字，strong元素表示强调文本。
- i元素定义斜体文字，em元素表示强调文本。

#### 15.label 的作用是什么？如何使用？

​	label标签用来定义input标签的标注

```html
//单选框
<input type="radio" name="input" value="A">
<label for="input">A</label>
<input type="radio" name="input" value="B">
<label for="input">B</label>
```

#### 15.Canvas 和 SVG 的区别

- Canvas是位图依赖分辨率，逐帧渲染，每次渲染完成后就不会被浏览器关注，绘制的图形不会出现在DOM当中。
- SVG是矢量图不依赖分辨率，不会因为放大失真，绘制的图形会出现在DOM当中。

#### 16.head 标签有什么作用，其中什么标签必不可少

​	head标签内用来放置文档头部信息如meta配置元信息，资源链接link标签，以及文档标题title标签，其中title标签必不可少

#### 17.浏览器乱码的原因是什么？如何解决？(GBK 和 UTF-8)

​	乱码的原因是网页源代码的编码格式是GBK但是内容中的中文是UTF-8编码，解决办法是使用编辑器编辑网页内容。

#### 18.渐进增强和优雅降级之间的区别

- 渐进增强指先根据低版本浏览器来开发功能然后向着高版本浏览器来升级。
- 优雅降级指先根据高版本浏览器来开发功能然后向低版本浏览器进行兼容。

#### 19.说一下 HTML5 drag API

```html
<div class="box" 
     draggable="true" //设置元素可拖拽
     ondragstart="drag(event)" //开始拖动触发的事件
     ondrop="drop(event)" //放下触发的事件
     ondragover="allowDrop(event)" //拖住移动触发的事件
> 
</div>
<script>
    function allowDrop(ev) {
        //默认无法把元素拖拽到另一个元素上，调用该方法阻止默认事件发生
        event.preventDefault();
    }
    function drag(ev) {
        //setData可以设置一个被拖拽的的数据类型和值
        ev.dataTransfer.setData("text", ev.target.id);
    }
    function drop(ev) {
        //getData可以获取到setData传过来的值
        var data = ev.dataTransfer.getData("text");
    }
</script>
```

# CSS

#### 1.盒模型

​	盒模型由内容(content) + 边框(border) + 内边距(padding) + 外边距(margin)组成，盒模型分为标准盒模型和IE盒模型

- 标准盒模型 box-sizing:content-box; 盒子的宽高：内容+内边距+外边距+边框。（会大于设置内容的宽高）
- IE盒模型 box-sizing:border-box; 盒子宽高：设置内容的宽高。（会和设置内容的宽高一致）

#### 2.flex 常用属性

```css
/* 容器属性 */
// 元素设置为flex容器
display:flex;
// 主轴排列方向
flex-direction: row;
// 主轴对齐方式
justify-content: center;
// 交叉轴对齐方式
align-items: center;
// 多根交叉轴对齐方式
align-content: center;
// 项目换行方式
flex-wrap: wrap;

/* 项目属性 */
//项目排列的顺序 越小越靠前
order:0;
//项目放大比例，默认为0，表示项目存在剩余空间也不放大
flex-grow:1;
//项目缩小比例，默认为1，表示项目空间不足会缩小
flex-shrink:0;
//定义项目在分配多余空间之前所占据的空间
flex-basis:350px;
//组合属性,由flex-grow和flex-shrink和flex-basis组合 默认值0 1 auto后面两个属性可选
flex:1;
//项目与其它项目不一样的对齐方式，可以覆盖align-items属性
align-self:start;
```

#### 3.position 属性

```css
//相对定位 根据自身定位
position:relative;
//绝对定位 基于最近的祖先元素为非static定位的元素定位，若没有找到则基于body元素定位
position:absolute;
//固定定位 基于视口定位
position:fixed;
//静态定位 不以任何方式定位
position:static;
//粘性定位 根据用户滚动条进行定位
position:sticky;

//四种方向偏移值
top:100px;
left:150px;
bottom:200px;
right:300px;
//定位元素重叠时的层级,越大越靠前
z-index:999;
```

#### 4.transition 和 animation

- transition是过渡

  ```css
  .box{
      //过渡作用的属性
        transition-property: width;
      //过渡持续时间
        transition-duration: 2s;
      //过渡速度曲线
        transition-timing-function: linear;
      //过渡延迟时间
        transition-delay: 1s;
  }
  ```

- animation是动画

  ```css
  // 设置关键帧
  @keyfreams example{
  	//代表开始(0%)
  	from{
  		background-color:red;
  	}
  	//代表完成(100%)
  	to{
  		background-color:blue;
  	}
  	/* 也可以用百分比值来设置
      25%{ background-color:pink;} 
  	*/
  }
  .box{
  	//使用关键帧
  	animation-name:example;
  	//设置动画持续时间
  	animation-duration:4s;
  	//设置动画开始的延迟时间
  	animation-delay:3s;
  	//设置动画运行次数  可以设置infinite表示无限运行
  	animation-iteration-count: 3;
  	/*动画运行方向 
  		normal 默认值 正常播放 
  		reverse 反方向播放 
  		alternate 先向前然后向后播放 
  		alternate-reverse 先向后然后向前播放
  	*/
  	animation-direction：reverse;
  	//动画运行曲线
  	animation-timing-function:ease;
  	//动画的填充模式(设置动画开始前和结束后能影响元素)
  	animation-fill-mode: forwards;
  }
  ```

#### 5.CSS3 中有哪些新特性

- transition
- animation
- flex、grid布局
- border-radius
- transform、translate
- 渐变、阴影
- 媒体查询
- CSS变量

#### 6.隐藏元素的方法有哪些

- display:none;
- visibility:hidden;
- opacity:0;
- overflow:hidden;
- 使用定位和translate将元素移除可视区

#### 7.盒子水平垂直居中方法

```css
//行盒
span{
    text-align: center;
    line-height: 10px; //行高为元素自身高度
}
//块盒
.parent{
    width: 250px;
    height: 250px;
    background-color: red;
    position: relative;
}
.child{
    width: 50px;
    height: 50px;
    background-color: pink;
    position: absolute;
    margin: auto;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
}
//其他方式
.parent{
    display: flex;
    justify-content: center;
    align-items: center;
}
```

#### 8.CSS 选择器和优先级

​	!important > 内联样式 > id选择器 > class选择器 > 元素选择器 > 通配符选择器

```css
//通配符选择器
*{}
//id选择器
#id{}
//class选择器
.class{}
//元素选择器
div{}
//后代选择器
div p{}
//子元素选择器
div > p{}
//相邻兄弟选择器
div + p{}
//通用兄弟选择器
div ~ p{}
```

#### 9.link 与 @import 的区别

- link是html的样式引入方式，是同步加载，兼容性好
- @import是css的样式引入方式,要等待页面加载完才会加载，低版本浏览器不兼容

#### 10.rgba 和 opacity 的透明效果有什么不同

​	rgba的透明只会作用到该元素上，opacity会让子元素也变成透明

#### 11.display:none 和 visibility:hidden 的区别

​	两者都是隐藏元素,display:none的元素不会占据空间所以会导致浏览器重新布局并进行回流，visibility:hidden的元素仍然占据空间所以只会造成浏览器的重绘。

> ps:两者隐藏元素后都无法触发事件

#### 12.画一条 0.5px 的直线

```css
.line{
	height: 1px;
    width: 20px;
    background-color: blue;
    transform: scale(.5);
}
```

#### 13.calc, support, media 各自的含义及用法

- calc函数用来动态计算css属性值
- support用来检测浏览器是否支持CSS某个属性
- media针对不同的设备编写不同的样式代码

#### 14.css 中的布局单位有哪些 区别又是什么

- px 逻辑像素
- em 相对于元素文字大小
- rem 相对于根元素的字体大小
- % 相对于父元素的百分比
- vh 相对于视口百分比高度
- vw 相对于视口百分比宽度

#### 15.如何用 css 画一个三角形

```css
.triangle{
    width: 0;
    height: 0;
    border: 20px solid transparent;
    border-bottom-color: red;
}
```

#### 16.伪类和伪元素的区别

​	伪类用于设置元素的特殊状态，伪元素给元素设置一个虚拟元素，不存在DOM当中。

```css
//常用伪类
div:link{}
div:visited{}
div:hover{}
div:active{}
div:focus{}
div:first-child{}
div:nth-child{}
//常用伪元素
div::before{}
div::after{}
```

#### 17.CSS 中可继承与不可继承属性有哪些

- 可继承：font-family、font-weight、font-size、line-height、color、text-align、text-decoration、letter-spacing、word-spacing、visibility、cursor、outline
- 不可继承：width、height、background、display、margin、border、padding、position、float

#### 18.display 有哪些属性，作用是什么

- display:none;隐藏元素
- display:block;块盒
- display:inline;行盒
- display:inline-block;行块盒
- display:flex;弹性盒子
- display:grid;网格布局

#### 19.为什么有时候⽤ translate 来改变位置⽽不是定位

​	translate直接通过GPU渲染不会造成回流和重绘，性能更好

#### 20.li 与 li 之间有看不见的空白间隔是什么原因引起的？如何解决？

​	由于代码之间的空格导致的空白间隙，解决办法有让li标签之间不留空格，但是这种做法代码可读性差不推荐，推荐做法是把父元素的font-size设为0再设置li的font-size就可以解决空白间隙问题。

#### 21.常见的图片格式及使用场景

- PNG：无损压缩，支持透明，适合logo/icon/透明图
- JPG：有损压缩，尺寸小，色彩丰富，适合渐变图
- SVG：矢量图，不会失真，支持动画，适合图表
- GIF：支持动画，无兼容性问题，文件小，适合icon/logo/动图
- WEBP：文件小，支持有损、无损压缩、支持动画，适合兼容webp格式的app和webview
- base64：把图片转换成一串字符串代替图片地址，可以不需要额外消费一个http来请求图片

#### 22.css 雪碧图

​	将多张图合并到一张图当中，通过修改background-position属性来截取其中要使用的图片,雪碧图的优点是可以减少代码体积，使用多张图片只需要获取一张雪碧图即可

#### 23.什么是物理像素，逻辑像素和像素密度

> 像素密度(DPR) = 物理像素（对线长度换算成英寸）/ 逻辑像素（css中经常写的px）

物理像素是指设备屏幕实际拥有的像素点，屏幕的基本单元

逻辑像素是设备独立像素，表示计算机坐标系统中的一个点

像素密度表示物理像素和逻辑像素的比例关系

#### 24.对 line-height 的理解及其赋值方式

​	块盒设置行高无效，行盒的高度不是文字撑开的，这个高度是行高，行高是两行文字基线之间的距离，line-height可以赋为绝对值100px，也可以给纯数字表示比例，还可以设置百分比

![img](https://ask.qcloudimg.com/draft/6436516/y8kx5ssfxs.png)

#### 25.CSS 优化和提高性能的方法有哪些

- 压缩CSS
- 避免使用@import
- 使用雪碧图
- 值为0的属性不要带px
- 避免选择器多重嵌套
- id和class选择器只用其一
- 避免重复样式
- 不使用css变量

#### 26.CSS 预处理器有哪些，有什么作用

​	sass、less、stylus、postcss

​	作用：代码嵌套、定义样式变量、样式继承、mixin、函数...

#### 27.对媒体查询的理解

​	可以针对不同的设备定制不同的样式，适合用在需要响应式布局的项目当中

#### 28.如何判断元素是否到达可视区域

```js
//获取DOM元素
const box = document.querySelector('.box');
//获取视口高度
const viewProtHeight = window.innerHeight;
//获取DOM元素距离顶部的距离
const boxOffsetTop = box.offsetTop;
//监听滚动条事件
window.addEventListener('scroll',()=>{
    //获取滚动条垂直移动的距离
    const scrollTop = document.documentElement.scrollTop;
    //视口高度+滚动条移动距离判断元素是否在可视区域
    const result = scrollTop + viewProtHeight >= boxOffsetTop ? "在视口" : "不在视口";
    console.log(result);
})
```

#### 29.z-index 属性在什么情况下会失效

​	当元素没有设置position属性为非static值的时候会失效

#### 30.CSS3 中的 transform 有哪些属性

- scale 放大缩小元素
- translate XYZ轴移动元素
- rotate 旋转元素
- skew XY轴倾斜角度

#### 31.实现两栏、三栏布局

```html
//flex两栏  三栏同理 在main后面加个aside
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<meta http-equiv="X-UA-Compatible" content="IE=edge">
	<title>Document</title>
	<style>
		*{
			padding: 0;
			margin: 0;
		}
		html,body{
			width: 100%;
			height: 100%;
		}
		.body{
			width: 100%;
			height: 100%;
			display: flex;
		}
		.aside{
			width: 200px;
			height: 100%;
			background-color: rgb(0, 38, 255);
		}
		.main{
			flex: 1;
			height: 100%;
			background-color: rgb(0, 255, 13);
		}
	</style>
</head>
<body>
	<div class="body">
		<div class="aside"></div>
		<div class="main"></div>
	</div>
</body>
</html>
```

#### 32.响应式布局的解决方案

- 使用媒体查询针对不同的设备写多套样式
- 百分比布局，所有元素单位都使用百分比
- rem布局，所有元素单位都使用rem，然后修改根元素大小
- 视口单位布局，元素都使用vw、vh单位，和百分比布局相似

#### 33.如何解决 1px 问题？

​	1px的问题是指pc端的1px在移动端上显示可能变粗或者变细，原因是像素密度，pc端的1px在移动端可能是2px

- 伪元素 + CSS3缩放：给元素添加伪元素先放大200%然后用scale缩小0.5倍
- viewport + rem：配置meta标签的viewport属性然后使用rem布局

#### 34.float 属性怎么使用，如何清除浮动

```css
//使用浮动
float:left; //right
//清除浮动 
//1.给浮动的父元素添加clear类名
.clear::after{
	content:"";
	clear:both;
	display:block;
}
//2.给父元素固定高度
.parent{
	height:400px
}
//3.手动在父元素内末尾添加一个清除元素
.box{
	clear:both;
	display:block;
}
```

#### 35.什么是外边距重叠，怎么解决(重叠只会出现在垂直方向)

​	当垂直方向两个元素设置了外边距，相邻的两个边距会进行重叠，重叠距离以最大的边距为准，解决办法是将两个元素放在非同一个BFC当中

#### 36.设置小于 12px 的字体

​	使用transform: scale(n)来缩小元素大小

# JS

#### 1.JS 的数据类型

- 基本类型：number、string、boolean、undefined
- 引用类型：object(function、array、null)
- 新增：symbol、bigint

#### 2. JS 检测数据类型的方法有哪些

- typeof
- instanceof  (只能检测对象)
- constructor
- Object.prototype.toString.call()

#### 3.作用域和作用域链

​	作用域分为全局作用域、函数作用域、ES6块级作用域，在函数作用域中可以访问上层函数和全局作用域，反之不行，当在某个作用域中使用变量或方法的时候但是在该作用域中找不到就会去自己上层作用域查找，直到找到为止，这种链式查找也叫作用域链

#### 4.原型和原型链

​	每个函数都有一个prototype属性，它是一个对象，对于普通函数来说该属性没有什么作用，但是如果把该函数作为构造函数使用时，prototype属性就会变成实例的原型对象，所有实例都会继承原型对象上的属性和方法。由于原型对象也是对象它也有自己的原型，所以这样就形成了一条原型链，当获取实例上的方法没有找到的时候就会沿着原型链查找

#### 5.闭包

​	在函数中返回一个内层函数给外部使用会产生闭包，由于闭包原因内层函数保存了外层函数的作用域并返回到了外部，所以外层函数执行完后作用域不会被销毁，因此闭包也可以做到在外部访问函数内部作用域，由于闭包会导致外层函数的作用域无法释放所以也会造成内存泄漏，闭包的用途是创建私有化变量

#### 6.EventLoop

​	JS的事件循环分为宏任务、微任务、同步任务，JS会先执行同步任务，如果遇到了宏任务就会把该任务放到宏任务队列，遇到微任务就会把该任务放到微任务队列，同步任务执行完成后会把微任务队列中所有的任务依次执行完成，然后再从宏任务队列中取出一个宏任务执行，执行完后再去微任务队列执行所有任务，如此反复...

- 微任务:Promise.then()、Process.nextTick(Node环境)、MutationObserver(监听DOM变化的API)
- 宏任务:setTimeout、setInterval 、DOM操作、script代码、用户交互、网络请求

#### 7.new 运算符的实现机制

```js
//手写New
function myNew(fn,...args){
	//创建一个空对象，并且原型指向构造函数的原型
	let obj = Object.create(fn.prototype);
	//改变构造函数this指向,并且执行一次构造函数
	let res = fn.apply(obj,args);
	//判断构造函数是否返回一个对象
	if(res instanceof Object){
		return res;
	}{
		return obj;
	}
}
```

#### 8.ES6 有什么新语法

- let、const、块级作用域
- 扩展运算符、数组对象解构
- map、set
- 箭头函数
- promise、async函数、generator函数
- proxy代理、迭代器、reflect
- class
- module

#### 9.var/let/const 的区别

|       | 变量提升 | 重复定义变量 | 块级作用域 |
| ----- | :------: | :----------: | :--------: |
| var   |    √     |      √       |     ×      |
| let   |    ×     |      ×       |     √      |
| const |    ×     |      ×       |     √      |

> const定义的值是常量不可修改，如果定义的值是对象那么对象内的值是可以修改的，但是修改不能覆盖整个对象

#### 10.map 跟 forEach 的区别

​	两者都是用来遍历数组，区别在于map可以返回一个新的数组，forEach只用来操作数组

#### 11.常用的数组方法

- 影响原数组：push、pop、shift、unshift、splice、sort、reverse
- 不影响原数组：forEach、map、concat、slice、reduce、join、indexOf、some、every、filter

#### 12.防抖和节流函数

```js
//防抖函数 重复运行函数会重置函数的执行时间
function debounce(fn,delay){
    //定时器变量
	let timer = null;
	return function(){
        //清空上一次的定时器
		clearTimerout(timer);
        //重置函数定时器
		timer = setTimeout(()=>{
			fn.call(this,arguments);
		},delay)
	}
}
//节流函数 定义一个阀门变量,第一次执行后关闭阀门，只有等函数执行完后阀门才会打开,才能重新执行函数
function throttle(fn,delay){
    //阀门变量
	let valve = true;
	return function(){
        //阀门关闭则函数执行无效
		if(valve){
			setTimeout(()=>{
				fn.call(this,arguments);
                //函数执行完毕 打开阀门
                valve = true;
			},delay);
		}
       	//函数运行关闭阀门
        valve = false;
	}
}
```

#### 13.数组去重的方法

```js
//set去重
var arr = [1,2,2,3,5,6,6,8];
var res = [...new Set(arr)];
//for循环 + indexOf去重
var arr = [1,2,2,3,5,6,6,8];
var res = [];
for(var i = 0; i < arr.length; i ++){
    if(res.indexOf(arr[i]) === -1){
        res.push(arr[i]);
    }
}
//双层for循环去重
var arr = [1,2,2,3,5,6,6,8];
var res = [];
for(var i = 0; i < arr.length; i ++){
    var flag = true;
    for(var j = 0; j < arr.length; j ++){
        if(arr[i] === res[j]){
            flag = false;
        }
    }
    if(flag){
        res.push(arr[i]);
    }
}
```

#### 14.Promise 是什么

​	Promise是一种异步的解决方式,它有三种状态，pending、resolved、rejected，只有异步的操作结果才能决定它的状态，并且一旦状态发生改变就不再会变，它的状态只有可能从pending变为resolved或者rejected。Promise是一个构造函数，接收一个回调函数作为参数，该函数有两个参数也是回调函数,resolve和reject的作用分别是讲Promise的状态从未完成变为成功和从未完成变成失败。Promise的原型上有一个then方法，该方法接收两个回调函数作为参数，第一个参数当Promise状态变成resolved时候执行，第二个参数当状态变成rejected的时候执行，then会返回一个promise实例，所以then方法可以链式调用。

#### 15.async 是什么

​	async是generator函数的语法糖，async函数内置了执行器不需要手动调用next方法，async函数会返回一个Promise对象，当在async函数内遇到await语句就会先返回，等到await后面的异步操作执行完成之后再继续执行函数体后的内容，await期望跟着的是一个Promise对象或者异步操作并返回它的结果，如果都不是那么await会直接返回对应的值。

#### 16.setTimeout 设置 0ms 会立即执行吗，为什么会有误差

​	不会立即执行，因为setTimeout是宏任务，JS在执行的时候会先执行同步任务再清空微任务队列，最后再执行宏任务，所以就算设置0ms也是会有误差，并且V8内部规定当setTimeout嵌套超过4层的时候会固定有4ms的延迟

#### 17.JS的预编译

​	JS在执行代码之前会对全局代码进行预编译

- 函数预编译过程：

1. 创建AO对象
2. 将所有变量声明赋给AO对象，值为undefined
3. 形参实参相统一
4. 将所有函数声明提升到作用域顶部

- 全局预编译过程：

1. 创建GO对象
2. 将所有变量声明赋给GO对象，值为undefined
3. 将所有函数声明提升到作用域顶部

#### 18.this 指向

- 普通函数this指向函数的调用者，全局调用指向window(严格模式下为undefined)
- 构造函数this指向实例
- 箭头函数this指向和距离自己最近的外层函数this指向一致

#### 19.箭头函数和普通函数的区别

- 箭头函数写法更简洁
- 箭头函数没有自己的this指向，也不能改变this指向
- 箭头函数没有arguments
- 箭头函数不能被new、不能当做generator函数
- 箭头函数没有原型属性

#### 20.null 和 undefined 的区别

​	null代表空，undefined代表未定义

#### 21."==="和"=="和 Object.is 的区别

- "==="比较值不会做隐式类型转换
- "=="比较值内部会做隐式类型转换
- Object.is用来比较两个值，只要两个值是一样的就返回true,（NaN也是）

#### 22.eval 是什么

​	eval是一个函数接受一个字符串作为参数，可以把该字符串参数当做语句执行

#### 23.JSON 是什么

​	JSON是一种传输数据的格式

#### 24.document.write 和 innerHTML 的区别

- document.write如果页面解析完成（在DOMContent事件之后）再调用write方法就会清除整个页面然后加载内容
- innerHTML将内容写入某个DOM节点

#### 25.JS 的垃圾回收机制

- 引用计数：JS在执行过程中扫描所有的值，没有被引用的变量值就是0，被引用过的变量值就会+1，JS执行完后会回收所有引用次数为0的变量，但是这种方法有缺点，如果两个变量相互引用那么引用次数就不会是0那么垃圾回收器就无法回收该变量，从而造成内存泄漏
- 标记清除(主流)：垃圾回收器定期从根节点开始扫描对象，对具有可达性的对象打上标记，最后执行完毕后回收所有没有被标记的对象

#### 26.Object.defineProperty 怎么用

```js
//第一个参数表示描述的对象,第二个参数是对象的key，第三个参数是属性描述对象
Object.defineProperty({},"name",{
    //属性值
    value:"张三",
    //是否可修改
    writable:true,
    //是否可遍历
    enumerable:false,
    //是否可配置
    configurable:true,
    //读取属性值会触发get方法
    get(){
        return "张三";
    },
    //设置新属性值会触发set方法
    set(value){
        console.log(value);
    }
})
```

#### 26.axios 和 fetch 区别对比

​	两者都是发送HTTP请求的API

- axios基于xhr封装实现，兼容性好，返回json格式数据，可以拦截请求和响应，可直接抛出异常对象，可全局配置默认请求头和超时时间...
- fetch是js原生API，返回response数据需要自己转换，兼容性较差，对异常处理也比较繁琐

#### 27.JS 中的继承方式有哪些

```js
//原型链继承 缺点:无法向父类传参
function Parent(age){
    this.age = age;
}
Parent.prototype.getAge = function(){
	console.log(this.age);
}
function Child(age){
    this.age = age;
}
Child.prototype = new Parent();
Child.prototype.constructor = Child;
Child.getAge();
//构造函数继承 缺点:虽然可以向父类传参 但是无法继承父类原型上的属性
function Parent(age){
	this.age = age;
}
function Child(name,age){
	Parent.call(this,age);
	this.name = name;
}
const p1 = new Child("张三",13);
const p2 = new Child("李四",16);
//组合继承 缺点:构造实例的时候父类构造函数会调用两次
function Parent(age){
    this.age = age;
}
Parent.prototype.getAge = function(){
    console.log(this.age);
}
function Child(name,age){
	Parent.call(this,age);
	this.name = name;
}
Child.prototype = new Parent();
Child.prototype.constructor = Child;
//原型式继承(Objec.create的实现) 缺点:只能继承原型对象上的属性和方法,无法给父类传参
function create(sup){
	function F(){};
	F.prototype = sup;
	F.prototype.constructor = F;
	return new F
}
function Parent(name,age){
	this.name = name;
	this.age = age;
}
Parent.prototype.getAge = function(){
	console.log(this.age);
}
const child = create(Parent.prototype);
//寄生式继承 在原型式继承的基础上给继承对象添加属性和方法 增强这个对象 缺点：同上
function create(sup){
	function F(){};
	F.prototype = sup;
	F.prototype.constructor = F;
    F.prototype.age = 30;
	F.prototype.showAge = function(){
		console.log(this.age)
	}
	return new F
}
//寄生组合式继承  寄生+构造函数继承 最优的继承方式
function Parent(name){
	this.name = name;
}
Parent.prototype.getAge = function(){
    console.log(this.age);
}
function Child(age,name){
    Parent.call(this,age,name);
    this.age = age;
}
Child.prototype = Object.create(Parent.prototype);
Child.prototype.constructor = Child;
Child.prototype.getName = function(){
    console.log(this.name);
}
```

#### 28.call、apply、bind 有什么区别

​	三者都是用来改变this指向

- call、apply会改变函数的this指向并且调用一次函数，它们的区别在于传参的方式不同
- bind用于将函数的this绑定到某个对象然后返回一个新的函数

#### 29.浅拷贝和深拷贝，有什么办法实现深浅拷贝

​	浅拷贝是指通过扩展运算符或者Object.create等方法将一个对象拷贝一份，但是通过这些方法拷贝出来的对象只是拷贝了最外层，内层对象并没有拷贝实际的值，当改变原始对象的时候内层拷贝对象也会发生改变

```js
//实现深拷贝
function deepClone(obj){
    //判断传入的是否为数组或者对象
    const objType = Object.prototype.toString.call(obj);
    if (objType !== "[object Object]" && objType !== "[object Array]") {
        return;
    }
    //创建克隆对象
    let cloneObj = obj.constructor === Array ? [] : {};
    for(key in obj){
        //for in会遍历到原型上的属性 用hasOwnProperty过滤
        if(obj.hasOwnProperty(key)){
            //对象类型递归处理
            if(typeof obj[key] === 'object'){
                cloneObj[key] = deepClone(key);
            }else{
            //基本类型数据直接赋值
                cloneObj[key] = obj[key]
            }
        }
    }
    return cloneObj;
}
```

#### 30.typeof null 的结果是什么，为什么？

​	object，历史遗留问题，null在设计的时候机器码是000和object一致

#### 31.intanceof 操作符的实现原理及实现

​	`instanceof`运算符的左边是实例对象，右边是构造函数。它会检查右边构造函数的原型对象（prototype），是否在左边对象的原型链上

```js
function _instanceof(left,right){
    //判断实例对象类型 如过不是函数或者对象直接返回false
	if(!['object','function']includes(typeof left) || left === null) return false;
    //获取左边实例对象的原型对象
	let proto = Object.getPrototypeOf(left);
    while(true){
        //实例的原型对象和构造函数的原型相等 返回true
        if(proto === right.prototype){
            return true;
        }
        //原型链到达尽头返回false
        if(proto === null){
            return false;
        }
        //获取原型的原型
        proto = Object.getPrototypeOf(proto);
    }
}
```

#### 32.为什么 0.1+0.2 !== 0.3，如何让其相等

​	js的浮点数以二进制存储，所以用浮点数进行数学运算的时候会出现精度失真，运算出来的结果可能是无限循环的小数，可以用toFixed方法来四舍五入

#### 33.如何获取安全的 undefined 值？

​	由于undefined并不是一个关键字，所以可以用undefined来定义变量，为了防止用undefined定义的变量造成全局污染所以可以使用void 0来获取一个安全的undefined值

#### 34.typeof NaN 的结果是什么？

​	number,因为NaN是数字类型

#### 35.isNaN 和 Number.isNaN 函数的区别？

​	isNaN用来判断一个数字类型的数据是否为NaN，如果传入的数据不是数字类型的时候，isNaN会在内部调用Number方法把数据转换成数字类型，所以这里如果传入的是一个非空数组或者非数值字符串那么Number方法会返回NaN，isNaN的结果就是true。Number.isNaN方法内部不会调用Number方法转换，只会判断传入的值是否为NaN，否则都返回false

#### 36.JS 的隐式类型转换和强制类型转换

###### 强制类型转换：

​	调用String()、Boolean()、Number()方法可以对数值进行强制类型转换

###### 隐式类型转换：

​	遇到以下三种情况会发生隐式类型转换，即转换是自动完成的，用户不可见：

- 自动转换为布尔值,js预期为布尔值的地方(比如if的条件部分)会把非布尔值类型的数据转换成布尔类型，系统内部会调用Boolean方法，因此除了以下五个值其余都为true:
  1. undefined
  2. false
  3. 0 (正0或负0)
  4. "" (空串)
  5. NaN

- 自动转换为字符串,js预期为字符串的地方，主要发生在加法运算，当一个值为字符串另个一个值为非字符串则后者会转换为字符串然后拼接在一起
- 自动转换为数字，js预期为数字的地方内部调用Number方法把非数字的值转换为数字再进行运算，除了加法有可能把数字转换为字符串，其它运算都会自动转换为数值

###### 补充：

> 易错点：
>
> 一、转数字类型
>
> 1.对象转数字类型返回NaN，除非对象是只包含单个值的数组 如[1]、[3]、[5]才会转换成数值
>
> 2.空串转数字类型结果是0
>
> 3.字符串不为纯数字类型转换数字为NaN
>
> 二、转字符串类型
>
> 1.对象转字符串返回该对象对应的字符串类型 如"[object Object]"
>
> 
>
> **对象转换的内部处理：**
>
> 一、转布尔
>
> 所有对象转布尔类型都为true
>
> 二、转字符串
>
> 1.调用对象的toString方法，如果返回原始类型的值则使用String函数转换，不再进行后续操作
>
> 2.如果toString方法返回的是对象，再调用原对象的valueOf方法，如果valueOf方法返回的是原始值那么使用String函数转换，不再进行后续操作
>
> 3.如果valueOf方法返回的还是对象就报错
>
> 三、转数值
>
> 1.调用对象的valueOf方法，如果返回原始类型的值则使用String函数转换，不再进行后续操作
>
> 2.如果valueOf方法返回的是对象，再调用原对象的toString方法，如果toString方法返回的是原始值那么使用String函数转换，不再进行后续操作
>
> 3.如果toString方法返回的还是对象就报错

#### 37.|| 和 && 操作符的用法以及返回值是什么

- ||全假才为假，如果第一个值是true则直接返回第一个值，否则返回第二个值
- &&全真才为真，如果第一个值是false则直接返回第一个值，否则返回第二个值

#### 38.什么是包装类

​	Boolean、String、Number这三个原生对象可以通过new操作符把原始类型的值包装成包装类的实例

```js
let boo = new Boolean(true);
let str = new String("abc");
let num = new Number(123);
typeof boo //"object"
typeof str //"object"
typeof num //"object"
```

​	如果在原始类型上调用方法，js内部会先将原始类型的值通过上述方法转换成包装对象，再去调用包装对象上的方法，所以虽然字符串是原始值没有方法,但是我们依然可以调用字符串的length方法，其实就是js内部会自动把字符串包装成了一个包装类的实例对象，然后我们调用length其实调用的是实例对象上的length方法，当我们调用完方法后这个实例对象就会自动销毁。

​	自动转换生成的包装对象是只读的，无法修改。所以，原始值无法添加新属性，原因是调用结束后实例对象会销毁，所以下次读取的包装对象是一个新的实例对象

#### 39.为什么会有 BigInt 的提案？

​	js所有的数据都以双精度64位浮点格式存储，导致js无法精确表示非常大的数值，超出这个范围会出现精度失真，所以在处理非常大的数值数据的时候需要借助第三方库的帮助，所以就有了BIGINT的提案

#### 40.const 对象的属性可以修改吗

​	可以修改，因为const不能改变是指对象的指针不能改变，用const定义的对象储存的是这个对象所在的地址，所以修改对象上的属性不会影响到对象

#### 41.ES6 中的模板字符串

```
const day = "周一";
//``表示字符串 可以随便换行 ${}插入变量
console.log(`今天${day}`);
```

#### 42.Map 和 Object 的区别，WeakMap 和 Map 又有什么区别

- Object的key必须是字符串,Map的key可以是各种类型的值
- WeakMap的key必须是对象或Symbol类型，并且WeakMap的key弱引用，只要所引用的对象的其他引用都被清除，垃圾回收机制就会释放该对象所占用的内存

#### 43.JavaScript 有哪些内置对象

- Arguments
- Date
- RegExp
- Booelan
- Number
- String

#### 44.什么是类数组

​	类数组也叫伪数组，类数组指含有数字下标属性值和length属性并且length的值为正正数，但是类数组没有Array.prototype上的方法,常见的类数组有Dom元素和Arguments对象

#### 45.Unicode、UTF-8、UTF-16、UTF-32 的区别？

​	Unicode是字符集，UTF-8/16/32是编码规则，它们的编码规则不同，最常用的是UTF-8

#### 46.什么是 DOM 和 BOM？

- DOM是文档对象模型，是HTML的标准接口，通过调用这些DOM接口可以修改网页内容和样式
- BOM是浏览器对象模型，提供了和浏览器窗口交互的接口，通过这些接口可以获取一些客户信息或者移动修改浏览器窗口等功能

#### 47.对 requestAnimationframe 的理解

​	该方法可以推迟某个函数的执行时机到下一次浏览器回流执行，执行完才会进行页面重绘，和定时器不同的地方在于该方法更节省资源，当浏览器在后台运行的时候该方法会暂停，该方法接收一个回调函数作为参数，表示浏览器下一次回流要执行的方法。

```js
//获取box元素 使用requestAnimationFrame让它向右移动
let dom = document.querySelector('.box');
let distance = 0;
function move(){
	distance ++;
    dom.style.left = distance + 'px';
    window.requestAnimationFrame(move);
}
window.requestAnimationFrame(move);
```

#### 48.escape、encodeURI、encodeURIComponent 的区别

​	escape对字符串进行编码，encodeURI、和encodeURIComponent对URI进行编码

#### 49.对 AJAX 的理解，实现一个 AJAX 请求

​	AJAX是用来发起http请求的API，通过JS的原生对象XMLHttpRequest对象来发送

```js
const xhr = new XMLHttpRequest();
//参数1：请求方式 2:请求URL 3:同步(false)/异步(true)
xhr.open("GET","getAjaxDatas",true);
//发送请求
xhr.sent();
//接收服务器的响应
xhr.onreadystatechange = ()=>{
	//判断请求状态是否成功
	if(xhr.readState == 4 && xrh.status == 200){
		//获取返回值
		const res = xhr.responseText;
		console.log(res);
	}
}
```

#### 50.什么是尾调用，使用尾调用有什么好处？

​	尾调用是指在函数的内的最后一步调用函数，因为函数的执行基于执行栈，每个函数都需要在栈内存中保存这个函数的执行期上下文，如果把函数放在最后一步执行那么就不需要保存这个函数的上下文了，所以使用尾调用可以节省内存

#### 51.ES6 模块与 CommonJS 模块有什么异同？

- 语法区别：

```JS
/* ES6-静态加载，编译时确定依赖关系，优点是效率高，缺点是无法引用自身，因为不是对象*/
//引入、导出
import {add} from './util';
export function add(a,b){
    return a + b;
}
/* CommonJS-动态加载，运行时确定依赖 */
//引入、导出
const fs = require("fs.js");
module.exports = {
    ...
}
```

- 加载方式：

​	ES6使用静态加载，在编译时确定依赖关系，优点是效率高，缺点是无法引用自身。CommonJS使用动态加载，在运行时确定依赖关系

- 对象的引用方式：

​	ES6模块导出的是模块的地址，即所有导入的对象都指向同一个引用，所以如果模块发生改变那么所有导入对象都会改变。CommonJS导出的模块是通过值的拷贝，修改原始模块不会影响导入的模块

- 循环依赖的处理：

​	ES6会在编译时处理循环依赖的模块，将这些循环的依赖转换成静态的拓扑结构。CommonJS无法做到处理循环依赖

- 应用场景：

​	ES6适用于浏览器和Node.js环境，CommonJS适用于服务端

#### 52.常见的 DOM 操作有哪些

```js
//获取DOM
document.getElementById();
document.getElementsByClassName();
document.getElementsByName();
document.querySelector();
document.querySelectorAll();
//创建DOM
document.createElement('元素名'); //创建新的元素节点
document.createAttribute('属性名'); //创建新的属性节点
document.createTextNode('文本内容'); //创建新的文本节点
document.createComment('注释节点'); //创建新的注释节点
document.createDocumentFragment( ); //创建文档片段节点
//删除DOM
parentNode.replaceChild( newChild, existingChild );//用新节点替换父节点中已有的子节点
element.setAttributeNode( attributeName );//若原元素已有该节点，此操作能达到修改该属性值的目的
element.setAttribute( attributeName, attributeValue );//若原元素已有该节点，此操作能达到修改该属性值的目的
//插入DOM
parent.appendChild( element/txt/comment/fragment );//向父节点的最后一个子节点后追加新节点
parent.insertBefore( newChild, existingChild );//向父节点的某个特定子节点之前插入新节点
element.setAttributeNode( attributeName );//给元素增加属性节点
element.setAttribute( attributeName, attributeValue );//给元素增加指定属性，并设定属性值
```

#### 53.use strict 是什么意思 ? 使用它区别是什么？

​	表示开启严格模式,当开启了严格模式之后以下行为会报错：

- 只读属性不可写
- eval、arguments对象不可作标识符
- 函数不能有重名的参数
- 禁止八进制前缀为0
- 必须显示声明变量
- this指向全局变量
- 禁止使用callee、caller
- 禁止删除变量
- 禁止使用with语句

#### 54.如何判断一个对象是否属于某个类

- 使用constructor判断对象的构造函数
- 使用instanceof判断对象的原型是否在某个类的原型上

#### 55.强类型语言和弱类型语言的区别

​	强类型语言指该语言必须强制定义数据类型，一旦某个变量指定了某个数据类型不经过强制的类型转换就永远不能随便更改，弱类型语言的数据类型可以被忽略，它与强类型语言相反，一个变量可以变成任意类型的值，强类型在速度上比弱类型语言要慢，但是强类型的严谨性能避免很多错误

#### 56.解释性语言和编译型语言的区别

​	编译型语言在程序在执行之前需要一个专门的编译过程，通过编译器把程序编译成为可执行文件，再由机器运行这个文件，运行时不需要重新翻译，直接使用编译的结果就行了。而解释型语言是一边执行一边转换的，其不会由源代码生成可执行文件，而是先翻译成中间代码，再由解释器对中间代码进行解释运行，每执行一次都要翻译一次。

#### 57.for...in 和 for...of 的区别

​	for...in可以用来遍历数组和对象,并且会遍历到原型上的属性。for...of只能用来遍历实现了iterator接口的数据结构

#### 58.如何获得对象非原型链上的属性？

​	使用for...in循环遍历对象，然后用hasOwnProperty方法过滤原型链上的属性

```
const obj = {...}
for(item in obj){
	if(obj.hasOwnProperty(item)){
		console.log(obj[item])
	}
}
```

#### 59.Promise 有哪些方法

- then()   //Promise状态发生改变后执行的回调
- catch()  //Promise状态变成失败时候的回调
- race()   //接收一个Promise数组,返回最先改变状态的那个回调
- all()     //接收一个Promise数组,只有数组内的所有Promise状态变为成功才会把数组组成一个返回值传递给回调，否则返回第一个失败的Promise给回调
- finaly()  //无论Promise的状态成功还是失败都会执行的回调
- resolve()  //快速返回一个成功状态的Promise
- reject()   //快速返回一个失败状态的Promise

#### 60.哪些情况会导致内存泄漏

- 滥用闭包
- 定时器没有被销毁
- DOM元素没有被正确移除
- 没有声明初始化的全局变量
- 垃圾回收机制为引用计数的时候 循环引用变量

#### 61.一个文件可以使用两个 export defalut 导出吗

​	不可以，因为一个模块只能有一个默认输出,export defalut命令本质是将输出的值赋给defalut变量

```
//util.js
export defalut function(){
	...
}
//main.js
import foo from 'util.js';
foo();

----等价于----

//util.js
export defalut function foo(){...}
//main.js
import {foo as defalut} from 'util.js';
```

#### 62.import 的执行顺序是什么，怎么执行的

​	import命令在编辑阶段执行，模块的导入发生在代码执行之前，执行顺序如下：

1. 解析模块路径：首先，解释器会解析`import`语句中指定的模块路径。
2. 下载模块：一旦解析了模块路径，解释器将从指定的路径下载相应的模块文件。这可以是本地文件路径或URL。
3. 编译模块：解释器会编译模块文件，将其转换为可执行的JavaScript代码。这一过程中可能会包括对依赖模块的解析和下载。
4. 创建模块的作用域：一旦模块被编译为可执行代码，解释器会为该模块创建一个独立的作用域。这意味着模块内部的变量和函数在模块外部是不可访问的，除非被明确导出。
5. 执行模块代码：在模块作用域中，解释器会按照代码的顺序执行模块中的语句。这包括变量声明、函数定义等。

#### 63.import 后加{}和不加{}的区别

​	加{}一般是引入模块的局部变量或者方法，不加{}引入的是整个模块，并且模块必须要有默认导出(export default)才可以引入不加{}的模块

```
//加{}
//util.js
export foo(){}
export bar(){}
//main.js
import {foo,bar} from './util.js';
foo();
bar();

//不加{}
//util.js
export defalut {
	foo:function(){},
	bar:function(){}
}
//main.js
import util from './util.js';
util.foo();
util.bar();
```

#### 64.事件的冒泡和捕获以及事件委托是什么

​	js的事件运行机制：当某个DOM事件触发的时候会先从根元素(html)开始触发事件，向下一层一层的捕获，直到到达目标节点，然后从目标节点向上触发事件，一层一层的冒泡，直到达到根节点。事件委托就是如果要触发多个元素的事件，那么就把事件绑定到这些元素的父节点上，利用捕获冒泡的机制只订阅一个元素来实现所有事件。

#### 65.什么是执行栈

​	js的执行栈是指js在运行的时候会先将全局上下文压入执行栈底，当遇到了函数执行就会创建一个函数执行期上下文并把它压入栈中，执行完后该函数的执行上下文就会从执行栈中弹出，直到所有代码运行完毕最后全局上下文也弹出执行栈，形成了一个后进先出的顺序

#### 66.documentFragment 是什么？用它跟直接操作 DOM 的区别是什么？

​	documentFragment是文档片段，它不属于当前文档，操作documentFragment比直接操作DOM要快很多，当有频繁且很多要操作的DOM对象推荐使用documentFragment来操作

#### 67.JavaScript 中的数组和函数在内存中是如何存储的？

​	由于数组和函数都属于引用类型，所以它们的实际值都储存在堆内存当中，同时在栈内存中储存了访问它们地址的指针，所以当我们访问函数或者数组的时候会先在栈内存中获取到它们的地址，再通过地址去堆内存中访问实际值。

# Vue

#### 1.Vue2 的生命周期

​	beforeCreate -> create -> beforeMounted -> mounted -> beforeUpdate -> update -> beforeDestory -> destory

#### 2.组件传值的方式有哪些

- 父传子  父在子标签bind属性 子用props接收
- 子传父  父在子标签绑定自定义事件  子通过$emit触发父回调传值
- $refs  通过ref拿到子组件的实例
- $attrs 爷传孙 获取所有父作用域不被作为prop识别的属性
- 通过provide注入依赖 inject 接收依赖 适合层次很深的组件传值
- 中央事件处理  注册一个js文件返回一个新的vue实例 通过$on监听事件  $emit触发事件
- vuex 全局状态管理器
- $parent  $children获取父实例 子实例

#### 3.computed 与 watch 的区别

​	computed是计算属性，必须有返回值，是惰性计算的，只有当依赖的值发生改变才会重新执行函数返回新的值。watch是监听器，当监听的属性发生改变就会执行回调函数

#### 4.v-if 和 v-for 的优先级

​	v-for比v-if有更高的优先级

#### 5.$nextTick 的作用

​	该方法接收一个回调函数作为参数，在下次 DOM 更新循环结束之后执行延迟回调

#### 6.v-for 中 key 的作用

​	给虚拟DOM一个唯一标识，当DOM更新的时候vue的diff算法可以根据key来辨别新旧节点从而更高效的更新DOM

#### 7.keep-alive 的作用以及实现

​	keep-alive可以缓存组件状态避免组件重新渲染。keep-alive的实现原理其实是被keep-alive所包裹的组件在内部都会被打上一个shouldKeepAlive的标识，在组件的卸载钩子触发的时候不会真正的卸载组件，而是将组件移动到缓存当中，当组件被缓存后还会被添加一个keptAlive标记，标识组件已经被缓存，当组件下次要重新渲染的时候vue的渲染器不会重新挂载组件，而是从缓存中拿出组件并将它重新激活

#### 8.Vuex 和 Pinia

​	两者都是Vue官方的状态管理库，Pinia是作为最新的方案来代替Vuex，它比Vuex提供更简单的API，最重要的是，搭配 TypeScript 一起使用时有非常可靠的类型推断支持

#### 9.vue-router 怎么传参

- 通过$router方法的params获取params参数
- 通过$router方法的query来获取query参数
- 路由路径中使用动态路由参数 例如 {path:'/user/:id'} 
- 路由配置的meta字段传参 通过$route.meta来获取参数

#### 10.插槽 v-slot 的作用以及实现

​	在子组件中定义一个插槽然后在父标签内写入内容，那么Vue渲染的时候就会将父标签内的内容渲染到子组件插槽的位置。插槽的实现原理其实就是父组件的内容会被转换成一个函数，放在父实例的children属性上，该函数返回的内容的render对象。在子组件中定义插槽的地方会被转换成执行这个插槽函数，这样在子组件中就可以获取到父组件的插槽内容了

#### 11.Vue2 的双向绑定原理

​	Vue2中实现数据双向绑定主要由这么几个类组成:

- Observe(监听器)：使用Object.defineProperty劫持所有data上setter和getter，在getter中调用Dep的depend方法收集依赖，在setter中调用Dep的notify方法通知所有依赖更新
- Compile(编译器)：编译模板，对不同类型的节点做不同的处理，解析所有节点上的指令并且实现相应的更新函数，每编译一个节点都会实例化一个Watcher实例
- Dep(依赖收集器)：提供了收集依赖和通知所有依赖更新的方法
- Watcher(观察者)：实例化的时候会获取一次数据的旧值，然后等待依赖更新再调用自身的update方法去调用Compile实现的更新函数达到更新视图的效果
- 通过Object.defineProperty劫持所有data上setter和getter，在get函数中收集所有依赖

```js
//一个简单的双向绑定实现
//MVue
class MVue{
	constructor(options){
		this.$el = options.el;
		this.$data = options.data;
		this.$options = options;
        //如果传入了根元素则开始模板编译
		if(this.$el){
			new Compile($el,this);
		}
        //实例化监听器
        new Obsever(this.$data);
	}
}
//初始化一个Vue实例
const vm = new MVue({
    el:"#app",
    data:{
        name:"xxx",
        age:11,
    }
})
//Compile.js
class Compile{
	constructor(el,vm){
        //el可传"#app" 也可以传document.querySelector("#app")
        this.el = el.nodeType === 1 ? el : document.querySelector(el);
        //保存vue的实例
        this.vm = vm;
        //开始编译模板
        this.compile(this.el);
    }
    //编译模板
    compile(el){
        // 1.获取子节点
        const childNodes = el.childNodes;
        [...childNodes].forEach((child)=>{
            if(this.isElementNodes(child)){
                //是元素节点,调用编译元素节点的方法 省略...
            }else{
                //是文本节点,调用文本节点的方法
                this.compileText(child);
            }
            //递归遍历子元素
            if (child.childNodes && child.childNodes.length) {
                this.compile(child);
            }
        })
    }
    //编译文本节点
    compileText(node) {
    	const content = node.textContent;
    	// 匹配插值语句中的内容 {{ xxx }}
        if (/\{\{(.+?)\}\}/.test(content)) {
            // 处理文本节点
            compileUtil['text'](node, content, this.vm)
        }
    }
}
//compileUtile.js
const compileUtile = {
    // 获取值的方法 如data.name的实际取值
    getVal(expr, vm) {
        return expr.split('.').reduce((data, currentVal) => {
            return data[currentVal]
        }, vm.$data)
    },
    //获取新值 对{{a}}--{{b}} 这种格式进行处理
    getContentVal(expr, vm) {
        return expr.replace(/\{\{(.+?)\}\}/g, (...args) => {
            return this.getVal(args[1], vm);
        })
    },
    //编译文本节点
    text(node, expr, vm) {
        let val = this.getVal(expr, vm);
        //如果是插值语法{{ data }} 则实例化一个观察者
        if (expr.indexOf('{{') !== -1) {
            //获取当前插值语法中的实际值
            val = expr.replace(/\{\{(.+?)\}\}/g, (...args) => {
                //实例化Watcher并且绑定callback函数,等待依赖改变就调用callback
                new Watcher(vm,args[1],()=>{           
                    this.updater.textUpdater(node,this.getContentVal(expr, vm));
                })
                return this.getVal(args[1], vm);
            })
        }
        //初始化调用更新函数
        this.updater.textUpdater(node,val);
    },
  	updater: {
        textUpdater(node, value) {
            //更新DOM
            node.textContent = value;
        },
    }
}
//Watcher.js
class Watcher{
    constructor(vm,expr,cb){
        this.vm = vm;
        this.expr = expr;
        this.cb = cb;
        //实例化的时候先获取一遍旧值
        this.oldVal = this.getOldVal();
    }
    getOldVal(){
        //将自身放到一个全局环境
        Dep.target = this;
        //调用compile工具获取值,在这里会触发Obsever的getter,所以会把watcher实例放入依赖当中
        let oldVal = compileUtile.getVal(this.expr,this.vm);
        //自身放入依赖后清空这个变量 供其他Watcher使用
        Dep.target = null;
        return oldVal;
    }
    update(){
        //触发更新的时候获取一遍最新的值
        let newVal = compileUtile.getVal(this.expr,this.vm);
        //新旧值不相等就触发更新
        if(newVal !== this.oldVal){
            this.cb(newVal);
        }
    }
}
//Observer.js
class Observer{
    constuctor(data){
        this.observer(data);
    }
    observer(data){
        Object.keys(data).forEach(function(key) {
            defineReactive(data, key, data[key]);
        });
    }
    defineReactive(data, key, val) {
        this.observe(val); // 监听子属性
        const dep = new Dep();
        Object.defineProperty(data, key, {
            enumerable: true, // 可枚举
            configurable: false, // 不能再define
            get: function() {
                //取值的时候添加向Dep添加依赖
                Dep.target && dep.addSub(Dep.target);
                return val;
            },
            set: function(newVal) {
                val = newVal;
                //修改值的时候通知dep触发更新函数
                dep.notify();
            }
        });
    }
}
//Dep.js
class Dep{
    constructor(){
        //依赖集合
        this.subs = [];
    }
    addSub(watcher){
        this.subs.push(watcher);
    }
    notify(){
        //通知所有watcher触发更新函数
        this.subs.forEach(watcher=>{
            watcher.upDate();
        })
    }
}
```

> 总结：Vue底层通过Observe劫持所有data的getter和setter，实例化一个依赖收集器Dep，在getter中调用Dep的addSub方法收集watcher依赖,在setter中通知所有wathcer触发更新函数,在Vue实例化的时候会触发Compile编译模板，在这一阶段Compile会递归解析模板中的节点，并且针对不同类型的节点调用一次更新函数进行初始化,在初始化之前还会为每个节点实例化一个Wathcer，当数据发生改变的时候就会触发Dep的notify方法从而让所有watcher执行节点的更新函数

#### 12.v-model 的用法

​	v-model是用于表单的双向绑定

```
<input v-model="text"/>
//等价于
<input :value="text" @input="event => text = event.target.value"/>
export {
    data(){
        return{
			text:"123"
        }
    }
}
```

> 文本类型的元素v-model绑定的是value值和监听input事件,checkbox和radio会绑定checked值和监听change事件，select会绑定value值和监听change事件

#### 13.Vue2 和 Vue3 区别

- Vue2使用Object.defineProperty处理双向绑定,Vue3使用Proxy返回一个对象的代理
- Vue3新增setup函数，使用组合式API来编写业务，解决了关注点分离的问题
- Vue3的性能比Vue2要更好
- 新增了Teleport、Suspense组件
- Vue3在写模板的时候可以没有根标签
- 生命周期发生了改变
- Vue3的diff算法做了静态提升，给所有静态节点打上标记，渲染的时候直接复用
- Vue3中v-if比v-for优先级高

#### 14.Vue3 双向绑定原理

​	Vue3通过Proxy返回一个对象的代理，在Proxy中拦截getter、setter操作，在触发读取属性操作时候将依赖此属性的副作用函数存入一个队列中，当触发属性的修改操作时从队列中取出所有的副作用函数执行一遍就可以达到数据响应式的效果

#### 15.Vue3 的生命周期

​	setup -> onBeforeMount -> onMount -> onBeforeUpdate -> onUpdate -> onBeforeUnmount -> onUnmount

#### 16.Vue3 中 setup 函数

​	有两种返回值，返回一个函数该函数将作为组件的render函数，如果组件以模板来表达渲染内容那么setup不能返回函数，否则会和编译模板发生冲突。返回一个对象，会将该对象包含的数据暴露给模板使用。setup函数只会在组件挂载的时候执行一次，它有两个参数，第一个参数是组件接收到的props，第二个参数是context对象，包含了slots、emits、attrs、expose这些与接口相关的数据和方法

#### 17.Vue 中的 data 为什么是一个函数

​	因为对象是引用类型，如果返回的是一个对象创建多个组件就会共用一个data,修改其中一个组件的data,其他组件的data也会改变

#### 18.MVC、MVP、MVVM 的区别

- MVC特点：关注点分离，View（视图）发送指令到Controller（控制器），然后Controller通知Model（数据）发生改变，Model将最新的数据发送到View
- MVP特点：切断了View和Model之间的关系，所有操作和通知都在Persenter里处理，Model和View向Persenter双相通信
- MVVM特点：同样切断了View和Model之间的联系，但是采用双向绑定的模式，View和Model发生变化会通过ViewModel触发自动更新的操作

#### 19.v-if 和 v-show 的区别

​	v-if会让元素真正的销毁，并且是惰性的，如果v-if的值一开始就是false那么不会渲染元素。v-show只是切换了元素的display属性

#### 20.Vue 的单向数据流

​	props会因为父组件的更新而变化，这形成了一条单向的数据流，子组件不应该去修改props中的属性，不然应用的数据流会变得混乱和难以理解

#### 21.Vue2 中使用索引或者 length 改变数组项视图不更新原因是什么，怎么解决

​	因为Vue2中无法拦截数组用索引和length改变数组的操作，可以使用this.$set方法来修改数组

#### 22.Vue 的父组件和子组件生命周期钩子函数执行顺序

​	父beforeCreate -> 父create -> 父beforeMounted -> 子beforeCreate ->子beCreate -> 子beforeMounted -> 子mounted -> 父mounted 父beforeUpdate -> 子beforeUpdate -> 父update -> 子update -> 父beforeDestroy -> 子beforeDestroy -> 子destroy -> 父destroy

#### 23.父组件如何监听到子组件的生命周期

​	在父组件上监听对应的生命周期事件并绑定回调函数，例如监听mounted钩子就是，`<Child @mounted="callback"/>`,然后在子组件通过this.$emit("mounted",params)来触发父组件的回调函数

#### 24.vue-router 路由模式有几种，它们有什么区别，实现原理是什么

- hash模式：URL中会带有一个# 后面代表hash值，hash值不会包括在http请求当中，所以改变hash不会刷新页面，这种模式的原理是监听window下的hashChange事件，当URL中的hash发生变化的时候触发事件
- history模式：由于使用了HTML5的history API所以这种模式对低版本浏览器不兼容，原理是调用history API的pushState方法来进行路由跳转
- abstract模式：当前环境为非浏览器环境时候会使用这个模式，不依赖浏览器的路由，内部用数组模拟了一个浏览器的历史记录栈

#### 25.虚拟 DOM 是什么

​	Vue在初始化的时候会将模板编译成虚拟DOM，虚拟DOM实际上就是一个JS对象，表示一个DOM的结构，由于频繁的操作DOM非常消耗性能，所以Vue内部使用虚拟DOM，在需要更新DOM的地方使用diff算法，计算出需要更新的地方后再去更新真实DOM

#### 26.说下 diff 算法

​	Vue在遇到更新的时候会使用diff算法对新旧节点进行比对，比对的过程也叫patch意为补丁，整个patch的过程只会有三种情况，1.旧节点没有而新节点有说明要创建节点，2.新节点没有而旧节点有说明要删除节点，3.新旧节点都有说明要更新节点，以新节点为准。Vue会循环递归使用diff算法处理每一个节点，并且针对不同的patch结果做出相应的操作处理

#### 27.Vue 模板编译原理

​	Vue通过编译器将模板转换成渲染函数，Vue首先会对模板进行词法分析和语法分析得到AbstractSyntaxTree（抽象语法树：描述模板的抽象JS对象）,然后将模板AST转换成JavaScriptAST，最终生成渲染函数。在词法分析和语法分析的过程中会调用parse函数来解析模板（template会变成字符串），其实parse的内部使用了很多的正则表达式来匹配模板中标签的开始、结束、指令...通过复杂的匹配和转换最终得到AST

#### 28.常见的事件修饰符及其作用

- stop：阻止事件传播
- prevent：提交事件不会重新加载页面
- self：只在event.target为自身才触发事件
- capture：开启捕获模式
- once：事件只能被触发一次
- passive：一般用于触摸事件的监听器，可以用来改善移动端设备的滚屏性能

#### 29.什么是 render 函数

​	render函数可以返回一个虚拟DOM，Vue提供了一个h函数来创建虚拟DOM，使用模板和使用render函数是等价的，它们最终都会返回虚拟DOM，模板更贴近html，render函数不需要被解析器转换，速度更快

```js
h(
    'div', //类型
    {class:'foo'},  //props
    []	//children
)
```

#### 30.Vue data 中某一个属性的值发生改变后，视图会立即同步执行重新渲染吗？

​	不会，Vue的响应式不会在数据发生改变就立即更新视图，DOM更新是异步执行的，当Vue侦听到数据变化会开启一个队列，在该队列中缓冲当前事件循环所有发生的数据改变，同一个数据被多次改变只会被推入到队列一次，在当前事件循环结束后再执行队列中的数据变更，这样做的好处是可以去除多余的计算和更新重复的DOM

#### 31.Vue 的自定义指令

```js
/* 全局注册 */
app.directive("指令名称",{
	...钩子函数
})

/* 钩子函数列表 */
//在绑定元素的 attribute 前或事件监听器应用前调用
created(el, binding, vnode, prevVnode) {},
// 在元素被插入到 DOM 前调用
beforeMount(el, binding, vnode, prevVnode) {},
// 在绑定元素的父组件及他自己的所有子节点都挂载完成后调用
mounted(el, binding, vnode, prevVnode) {},
// 绑定元素的父组件更新前调用
beforeUpdate(el, binding, vnode, prevVnode) {},
// 在绑定元素的父组件及他自己的所有子节点都更新后调用
updated(el, binding, vnode, prevVnode) {},
// 绑定元素的父组件卸载前调用
beforeUnmount(el, binding, vnode, prevVnode) {},
// 绑定元素的父组件卸载后调用
unmounted(el, binding, vnode, prevVnode) {}
```

​	指令的钩子会传递以下几种参数：

- `el`：指令绑定到的元素。这可以用于直接操作 DOM
- `binding`：一个对象，包含以下属性:
  - `value`：传递给指令的值。例如在 `v-my-directive="1 + 1"` 中，值是 `2`
  - `oldValue`：之前的值，仅在 `beforeUpdate` 和 `updated` 中可用。无论值是否更改，它都可用
  - `arg`：传递给指令的参数 (如果有的话)。例如在 `v-my-directive:foo` 中，参数是 `"foo"`
  - `modifiers`：一个包含修饰符的对象 (如果有的话)。例如在 `v-my-directive.foo.bar` 中，修饰符对象是 `{ foo: true, bar: true }`
  - `instance`：使用该指令的组件实例
  - `dir`：指令的定义对象

- `vnode`：代表绑定元素的底层 VNode
- `prevNode`：代表之前的渲染中指令所绑定元素的 VNode。仅在 `beforeUpdate` 和 `updated` 钩子中可用

#### 32.Vue 和 React 的区别以及对两者的理解

- React：国外发明的框架，比Vue出现的更早，使用JSX的语法，对于组件的划分更细，推崇函数式编程
- Vue：是渐进式框架，上手难度低，开发灵活高效

#### 33.assets 和 static 文件夹的区别

​	都是用来存放静态文件的，区别是static文件夹不会被webpack打包而是直接输出

#### 34.Vue 性能优化的方法有哪些

- v-for上必须绑定key
- 对于只展示不会改变的数据用Object.freeze冻结起来，防止Vue劫持getter和setter
- 使用keep-alive缓存组件
- 路由懒加载、组件懒加载、图片懒加载
- 第三方插件按需引入
- v-if和v-show区分使用场景
- watche和computed区分使用场景

#### 35.Vue 初始化页面闪动问题

​	使用v-clock指令防止Vue实例未完全加载时出现未渲染的模板

```css
//main.css
[v-clock]{
	display:none;
}
```

```vue
//main.vue
//执行到动态style的时候模板一定渲染完成了
<div style="display:none;" :style="{display: 'block'}"><div/>
```

#### 36.Vue-Router 的懒加载如何实现

​	使用ES6的Module语法提供的import()函数来实现懒加载，只有执行了import函数才会加载文件，所以可以传入一个回调函数，当需要使用路由的时候再去加载对应的页面，示例：

```js
const routes = [
	{ path: '/login', component: ()=>import('./login/index.vue') }
]
```

#### 37.$route 和$router 的区别

- $route是路由的配置对象，可以获取当前路由的参数、名称、路径
- $router是router的实例对象，可以用来操作路由比如调用push来跳转路由

#### 38.如何获取页面 URL 的 hash 变化

​	通过监听window下的hashChange方法来获取页面URL的hash变化

#### 39.Vue-router 路由钩子

> // 钩子函数的参数：
>
> to 表示要进入的目标路由	
>
> from 表示离开的路由
>
> next 跳转到指定路由 请确保钩子内调用了一次该函数
>
> failure 表示导航是否真的离开了当前路由

- beforeEach：全局前置守卫，在路由跳转的前一刻触发，参数：to、from、next

- afterEach：全局后置钩子，在路由跳转到目标后触发，参数：to、from、failure
- beforeEntry：路由独享守卫，可以在路由配置上添加该守卫，只有进入到该路由下才会触发钩子函数，参数：to、from
- 组件内的路由守卫：
  - beforeRouteEnter：在渲染该组件的对应路由被验证前调用，参数：to、from、next
  - beforeRouteUpdate：在当前路由改变，但是该组件被复用时调用，参数、to、from
  - beforeRouteLeave：在导航离开渲染该组件的对应路由时调用，可以通过返回false取消跳转，参数：to、from

#### 40.Vue-router 跳转和 location.href 有什么区别

- Vue-router使用history API的pushState进行路由更新，并且是静态跳转，浏览器不会重新加载
- location.href会重新加载整个页面

#### 41.对前端路由的理解

​	路由就是根据不同的URL渲染不同的页面，在以前前后端不分离的时候由后端来控制路由，根据收到客户端传递的http请求来返回不同的页面。现在随着技术的发展前端可以自己实现路由，其中核心的点就是监听URL的变化，根据路由的路径去渲染路由的页面，目前常用路由模式有hash模式和history模式，hash模式通过hashChange事件来监听URL的hash变化，然后根据最新的hash值找到对应的路由页面，然后渲染页面。history模式使用了HTML5的history API，通过pushState方法向浏览器添加历史记录，然后根据URL来渲染相应的路由页面

#### 42.如何在组件中批量使用 Vuex 的 getter 属性

```js
//使用mapGetters辅助函数将store中的getter映射到计算属性当中
import { mapGetters } from 'vuex'

export default {
  computed: {
  // 使用对象展开运算符将 getter 混入 computed 对象中
    ...mapGetters([
      'doneTodosCount',
      'anotherGetter',
      // ...
    ])
  }
}
```

#### 43.如何在组件中重复使用 Vuex 的 mutation

```js
//使用mapMutation辅助函数将store中的mutation映射到方法当中
import { mapMutations } from 'vuex'

export default {
  // ...
  methods: {
    ...mapMutations([
      'increment', // 将 `this.increment()` 映射为 `this.$store.commit('increment')`
      // `mapMutations` 也支持载荷：
      'incrementBy' // 将 `this.incrementBy(amount)` 映射为 `this.$store.commit('incrementBy', amount)`
    ]),
    ...mapMutations({
      add: 'increment' // 将 `this.add()` 映射为 `this.$store.commit('increment')`
    })
  }
}
```

#### 44.虚拟 DOM 真的比真实 DOM 性能好吗

​	在DOM操作不频繁的情况下虚拟DOM的性能不一定比真实DOM的性能好，因为虚拟DOM会先创建描述DOM的JS对象再转换成真实的DOM渲染到页面，但是如果DOM更新的比较频繁或者页面较大的情况下，虚拟DOM的性能一定比真实DOM要好，虚拟DOM会通过Diff算法计算出需要更新的元素，并且无论页面多大，虚拟DOM只会更新变化的内容，而真实DOM无法做到只改变需要更新的内容，每次更新都会将整个页面重新渲染一遍，并且操作DOM的性能消耗远远大于JS运算所产生的性能消耗

#### 45.Vue 中 key 的作用

​	key用来在diff算法中比较新旧节点的时候来识别VNode，内部根据key的变化来重新排列元素，key就像虚拟DOM的身份证一样，有了key就可以对DOM进行复用，没有key就无法知道新旧节点的映射关系，从而需要进行额外的对比操作来确定新旧节点的关系

#### 46.scoped 的作用以及原理

​	scoped在style标签上使用，可以让它的样式只作用在当前组件上，可以让组件之间的样式不互相污染。scoped的实现原理是在编译模板的时候会生成一个该组件的scopedId（例如：[data-v-12e412bd]）并添加到每个标签上，在编译style标签时会根据当前组件的scopeId通过属性选择器来输出样式 例如：

```html
<div class="demo"> Test <div/>
//编译成
<div class="demo" data-v-12e412bd> Test <div/>
```

```css
.demo{
	color:red;
}
//编译成
.demo[data-v-12e412bd]{
	color:red;
}
```

#### 47.如何理解 Vue 是一个渐进式框架？

​	渐进式框架的意思就是你不需要一开始就接受这个框架所有的功能，你可以放弃官方推荐的依赖库使用你当前所使用的依赖，例如在创建Vue项目的时候TypeScript、Webpack、Vue-Router、Vuex...这些都是可选的

#### 48.Vue CLI 3.x 的 Webpack 是如何组装处理的？

​	VueCLI3.x内嵌了webpack的基础配置，没有了之前的webpack.config.js配置文件，现在想要配置webpack需要在vue.config.js中配置，在configureWebpack中提供一个对象来配置webpack

# 浏览器

#### 1.输入一个 URL 到页面过程中发生了什么

1. 查找URL对应的资源是否在缓存当中并且缓存是否过期，没过期直接返回资源
2. DNS递归解析URL的域名得到对应的IP地址
3. 建立TCP连接，进行三次握手并发送http请求
4. 客户端接收服务器返回的资源
5. 分析html和css构建DOM树和CSS树，最终合并成一颗render树
6. 布局、分层、绘制页面

#### 2.浏览器渲染机制、重绘、重排

​	浏览器无法直接读取html和css，当浏览器获取到资源后会先构建DOM树和CSS树，在这个过程中会转换样式表中的属性，比如em转换成px，并且计算出DOM树种每个节点的具体样式，然后将DOM树和CSS树合并成为Render树，根据生成的Render树进行布局，获取到每个元素确切的位置和大小，接下来对页面进行分层，在这一阶段会确定重叠在一起的元素之间的层叠关系，构建完图层后渲染引擎会对元素进行绘制，在这一步GPU也会将图块进行栅格化最后完成绘制。

- 重绘：当元素的外观或者颜色发生改变的时候浏览器会进行重新绘制
- 重排：也叫回流，当元素的位置大小发生改变的时候浏览器需要重新计算页面所有元素的定位和大小，回流一定会引起重绘，重绘不一定回流，并且回流代价高

#### 3.浏览器存储方式有哪些

- cookie：上限4KB，会在同域名下的请求中携带
- localStorage：本地存储，最大支持5MB或者更高，关闭浏览器不会清空缓存，只有删除对应的本地文件才会清空
- sessionStorage：会话存储，当关闭浏览器窗口时就会清空缓存
- WebSQL：一个浏览器本地数据库储存方案
- IndexDB：HTML5新增的数据库存储方案，是NoSQL数据库

#### 4.同源策略

​	浏览器执行脚本前会判断脚本是否与当前网页是同源，同源政策必须满足三个条件：

- 协议相同 http/https/file...
- 域名相同 xxx.com
- 端口号相同 :8080

​	只要有一个条件不满足就会产生跨域

#### 5.说说你对 SPA 单页面的理解，它的优缺点分别是什么

​	传统的前端页面由多个页面组成，每跳转一个页面都会使浏览器加载一个新的html页面，这种方式虽然有利于SEO，但是对用户的体验差，每次跳转一个页面都需要等待，SPA可以解决这个问题，首次加载了所有的页面，当要跳转到一个新页面的时候只是切换了组件，优点是用户体验好和不需要重新加载页面，缺点是首屏加载慢和不利于SEO

#### 6.说说 SSR

​	SSR（服务端渲染），客户端可以直接从服务端获取完整的html页面，浏览器获取到资源后无需等待JS的加载直接渲染页面，这种方式可以让屏幕的首次加载更快，并且有利于SEO，缺点是会占用服务端资源

#### 7.强缓存和协商缓存

​	浏览器在第一次发送http请求后会缓存资源，再次发送请求的时候会根据请求头中的`Cache-Control`字段和`Expires`字段来判断是否是强缓存，如果是就会直接从缓存中获取资源，如果不是浏览器会发送一次请求到服务器，判断是否命中协商缓存，如果命中则返回状态码304然后从缓存中获取资源，如果没有命中则发起请求从服务器获取最新的资源

#### 8.浏览器内核是什么，有哪些常见的浏览器内核

​	浏览器的内核分为渲染引擎（负责解析html和css并进行样式计算和布局），和JS引擎（执行JS脚本实现网页的动态交互），常见浏览器内核：

- Chrome -- 以前是Webkit 现在是Blink
- Firefox -- Gekco
- Opera -- Presto
- Safari -- Webkit
- IE -- Trident

#### 9.如何给网页添加父标题

​	在title标签中添加内容

#### 10.什么是 XSS 攻击，什么是 CSRF 攻击，什么是中间人攻击？

- XSS：没有对用户的输入进行转码和过滤导致网页中被执行恶意脚本，XSS分三种类型：
  - 存储型：将恶意脚本发送到数据库储存
  - 反射型：将恶意脚本作为请求的一部分，经过服务器再反射到HTML文档中
  - 文档型：不经过服务端，在数据传输的过程中劫持数据包，修改里面的HTML文档
- CSRF：用户点击了恶意网站，黑客拿到了用户的登录状态跟服务端通讯，然而服务端并不知道和自己通讯的是黑客
- 中间人攻击：客户端和服务器通讯发送的数据包被中间人劫持篡改

#### 11.有哪些可能引起前端安全的问题?

- 输入框没有过滤转码导致XSS攻击
- 没有使用https协议
- 发送http请求没有使用Token校验身份
- Ifream滥用

#### 12.网络劫持有哪几种，如何防范？

​	网络劫持分为DNS劫持（输入京东但是跳转到了淘宝）和HTTP劫持（访问百度但是一直有广告），DNS劫持由于涉嫌违法，已经被监管起来，现在很少会有DNS劫持，⽽HTTP劫持依然⾮常盛⾏，最有效的办法就是全站HTTPS，将HTTP加密，这使得运营商⽆法获取明⽂，就⽆法劫持你的响应内容。

#### 13.如何实现浏览器内多个标签页之间的通信?

- WebSocket：启动一个WebSocke服务器，让AB页面都与之建立连接，AB页面之间就可以实时通信了
- localStorage：A页面监听storage事件，B页面存储数据到本地，A页面触发回调接收数据
- ifream：使用postMessage方法向子页面发送消息，子页面监听message事件获取数据
- WebWorker：和WebSocket类似，广播通信，不需要额外的服务器，浏览器内部启动一个独立线程

#### 14.对 Service Worker 的理解

​	HTML5提供的持久化离线存储API，本质是一个WebWorker，独立于主线程，在后台运行脚本，只有在https协议或者本地调试的情况下才能运行，ServiceWorker首先要在主线程当中注册，注册成功后会开始执行它的生命周期：install（安装）、installed（安装后）、activateing（激活）、activated（激活后）、redundant（废弃）

```js
//main.js
//在主线程注册sw
if(navigator.serviceWorker){
	window.addEventListener('load',()=>{
		navigator.serviceWorker.register('sw.js').then(reg=>{
			console.log('注册成功',reg);
		}).catch(err=>{
			console.log('注册失败',err);
		})
	});
}

//sw.js
//在sw线程监听生命周期钩子
self.addEventListener('install',event=>{});
self.addEventListener('installed',event=>{});
self.addEventListener('activateing',event=>{});
self.addEventListener('activated',event=>{});
self.addEventListener('redundant',event=>{});
//拦截主线程的网络请求
self.addEventListener('fetch',event=>{});
//获取主线程传递过来的信息
self.addEventListener('message',event=>{});
```

#### 15.什么是文档的预解析？

​	浏览器在解析html资源的时候会先全局扫描一遍文档，提前获取和处理与渲染相关的资源，比如样式表、字体文件、脚本引用、媒体文件等等...

#### 16.V8的垃圾回收机制

​	V8引擎实现了标准式的垃圾回收机制（GC），将内存分为新生代和老生代区域

- 新生代区域：主要存放存活周期较短的对象，里面有两个区域From和to，在进行内存分配的时候会将新对象分配到From区域，当进行垃圾回收的时候会启用新生代的回收算法，检查From空间中存活的对象，并将这些对象移动到To空间中，非存活的对象会被释放，然后From和To进行空间对换。当新生代区域里的对象经过以下条件会晋升到老生代区域中：
  - 经历过新生代GC算法的对象
  - To空间已经使用了超过25%
- 老生代区域：主要存放存活周期较长的对象，老生代区在空间不足的时候会进行老生代区GC，使用的是标记清除和标记压缩算法，首先遍历内存中所有存活的对象进行标记，最后清空没有被标记的对象，使用标记清除清理了非存活的对象后内存的状态不是连续的，所以要接着使用标记压缩算法，将所有存活的对象往一端移动，再清理掉边界的内存（可以理解为盛饭的时候压一下就可以让碗装下更多米饭）

# 计算机网络相关

#### 1.post 和 get 请求的区别

- post请求参数放在body体里面，一般用于提交修改服务器资源
- get请求参数拼接在URL后面，明文传输，一般用来获取资源

#### 2.http 和 https 的区别

- http是明文传输，安全性差，默认端口号是80
- https需要去CA机构申请数字证书，比http多了一层SSL/TLS，比http更安全，默认端口号是443

#### 3.http 状态码

- 200：成功
- 301：重定向
- 304：协商缓存
- 400：客户端错误
- 404：未找到资源
- 500：服务器错误

#### 4.跨域的解决方案

- Nginx配置反向代理
- CROS：后端配置
- JSONP：利用script标签没有跨域限制的特性，在script标签中放入回调函数获取资源
- 使用postMessage方法通信
- 利用WebSocket不存在跨域问题的特性来通信

#### 5.TCP 传输的三次握手和四次挥手

- 发起连接的三次握手（只有客户端可以发起连接）：
  - 第一次握手：客户端第一次向服务器发送一个SYN包等待服务器确认，客户端进入等待确认状态
  - 第二次握手：服务器收到了客户端发来的包，也发送一个SYN包给客户端，服务器进入等待连接的状态
  - 第三次握手：客户端收到了服务器的回应后向服务器发送确认的包，客户端和服务器就可以开始传递数据了
- 断开连接的四次挥手（断开连接可以是客户端和服务器任意一方发起）：
  - 第一次挥手：主动关闭方发送一个FIN包给对方，告诉对方我不会再给你发数据了
  - 第二次挥手：被动关闭方接收到了包后也返回一个包给主动关闭方，告诉对方我收到了，但是我现在还是可以给你发数据
  - 第三次挥手：被动关闭方没有要发送的数据了，再发送一个包给主动关闭方，告诉对方我现在也不给你发数据了
  - 第四次挥手：主动关闭方收到消息后最后给被动关闭方发送一个包，表示我收到了你的消息，然后双方断开连接

#### 6.线程与进程的区别

​	进程是操作系统资源分配的基本单位，线程是CPU任务调度和执行的基本单位，一个进程内至少有一个线程并且会共享同一进程下的资源。进程就是在内存中运行了一个应用程序，而线程就是执行当前运行程序中的一个任务

#### 7.常见的 http 请求头和响应头

​	**常见请求头：**

- Accept：浏览器可以接受服务器返回资源的类型
- Accept-Encodeing：浏览器接收的编码格式
- Accept-Language：浏览器接收的语言
- Connection：表示请求是长连接
- Host：请求头域名
- User-Agent：告诉服务器浏览器的版本信息
- Cache-Control：请求是否缓存
- Cookie：存储用户信息让服务器辨别身份
- Range：用于断点续传

​	**常见响应头：**

- Cache-Type：资源文件的类型
- Content-Encoding：资源采用的压缩编码
- Date：服务器发送资源的时间
- Server：服务器对应的版本信息
- Transfer-Encoding：告诉客户端资源的发送方式
- Expirse：告诉资源缓存的持续时间
- Last-Modified：请求对象上次修改的时间
- Etag：标识请求资源是否被修改
- Refresh：用于重定向
- Access-Control-Allow-Origin：指定可以跨域请求的地址，类似于白名单
- Access-Control-Allow-Methods：允许访问的方法
- Access-Control-Allow-Credentials：是否允许发送cookie

#### 8.HTTP 状态码 304 是多好还是少好

​	状态码304本质不算一个错误状态码，304可以判断服务器资源是否发生变化从而去缓存里获取资源，对性能是有提升的，但是过多的304请求会导致网站的爬虫率降低，网站收录排名会靠后，所以304状态码也是有利也有弊，多好还是少好得区分场景

#### 9.OPTIONS 请求方法是什么以及使用场景

​	OPTIONS请求方法用来获取资源支持的http请求方式有哪些，使用场景有：

- 跨域请求：在跨域请求中，浏览器会先发送一个OPTIONS请求获取服务器的跨域政策
- API文档生成：获取接口中的元数据，用来生成API文档或自动化测试
- 服务器探测：先探测服务器所支持的请求方法功能有哪些

#### 10.HTTP 1.0 、 HTTP 1.1 、HTTP 2.0、HTTP3.0之间有哪些区别？

- HTTP1.0：
  - 每次发送请求都要建立一个TCP连接，不支持断点续传，获取对象的一部分会将整个对象传递过来
- HTTP1.1：
  - Host字段强制要求设置
  - 默认开启长连接，多个请求可以复用同一个TCP连接
  - 引入了Range头域支持断点续传
  - 管线化处理，不用等待响应就可以发送下一个请求
- HTTP2.0：
  - 采用二进制的格式传输数据
  - 多路复用：一个TCP上可以有多个流传输，等传输完成后再重新组装形成一个完整的请求响应
  - 可以设置请求优先级，重要的请求会先响应
  - 压缩头部：采用HPACK在服务器和客户端之间维护一份相同的静态字典和一份相同的动态字典，通过哈夫曼编码对传输的首部字段进行编码，也就是在发送请求的时候要传输首部字段的时候只需传入字典里对应的索引值就可以了
- HTTP3.0:
  - 放弃了TCP协议，使用QUIC协议（基于UDP协议）
  - 解决了多路复用线头阻塞的问题
  - 没有了三次握手时间，速度更快
  - 优化了丢包重传策略

#### 11.GET 方法 URL 长度限制的原因

​	HTTP并没有限制GET方法URL的长度，限制URL长度的是浏览器，各大浏览器厂商对它的限制都不一样

- IE：2083字节
- FireFox：65536字节
- Safari：80000字节
- Opear：190000字节
- Chrome：8182字节

#### 12.对 keep-alive 的理解

​	keep-alive是用来开启http请求的长连接，通过设置请求头Connection：keep-alive来开启，开启了长连接之后多个http请求就会复用一个TCP连接，这样可以减少三次握手和四次挥手

#### 13.页面有多张图片，HTTP 是怎样的加载表现？

​	在HTTP1.x中,TCP的最大连接数为6，所以加载图片会请求多次，在HTTP2.x中因为采用了多路复用，可以一瞬间加载处很多图片资源

#### 14.HTTP2 的头部压缩算法是怎样的？

​	服务器和客户端都维护相同了一份静态字典和一份动态字典，在传输头部字段的时候就不需要添加具体的字段信息，只需要传入两份字典里的索引和参数即可，然后通过哈夫曼编码对传输首部进行编码

#### 15.http 的优点和缺点

- 优点：可靠性（TCP三次握手）、简单灵活可跨平台、无状态（服务器不记录请求状态，减轻了服务器的压力）
- 缺点：明文传输不安全、无状态导致每次请求都要验证身份

#### 16.URL 有哪些组成部分

```
/*	 协议  //    域名      :端口/路由/参数
	https://www.baidu.com:443/new/query?test=123
```

#### 17.什么是对称加密和非对称加密

- 对称加密：双方共用一把私匙来加密和解密，优点是加密和解密的速度快，缺点是安全性不稳定，必须保证密匙的安全性
- 非对称加密：接收方有一把公匙和一把私匙，公匙公开在网上，私匙自己保管，发送方拿到了公匙用公匙把数据包进行加密然后发送给接收方，然后接收方就可以用私匙来解密这个数据包

#### 18.数字证书是什么

​	非对称加密虽然可以保证数据包的安全性，但是发送方在获取公匙对数据包加密的时候有可能这个公匙是黑客提供的，这样当数据包发送出去的时候第三方就可以拦截数据包用自己的私匙解密破解数据包的内容，这个时候就需要用到数字证书了，数字证书CA机构颁发用来证明公匙确实是由自己生成的，接收方会提供自己申请的数字证书来证明自己的身份，发送方通过数字证书验证了身份之后从数字证书中拿到安全的公匙再来对数据包进行加密

#### 19.DNS 协议是什么

​	DNS是一种可以将域名和IP地址相互映射的以层次结构分布的数据库系统，DNS系统采用递归查询的方式来响应用户操作

#### 20.网络模型-OSI 七层模型

- 应用层（网络应用，通过各种协议：HTTP、HTTPS...）
- 表示层（将应用层的数据转换成计算机能读懂的机器码）
- 会话层（让计算机和服务器之间建立连接）
- 传输层（使用UDP、TCP等协议来实现数据的传输）
- 网络层（收到传输层的数据后，逻辑寻址，寻找目标计算机的IP地址）
- 数据链路层（收到网络层的数据包后物理寻址，通过光纤或无线信号）
- 物理层（将数据链路层收到的二进制序列转换成信号在电脑上传输，最终在目标计算机的应用层上显示数据）

#### 21.TCP 与 UDP

- TCP：面向连接、面向字节流、可靠性的通信协议，传输数据要经过三次握手和四次挥手，传输方式只能一对一
- UDP：面向无连接、面向报文、不可靠的通信协议，传输数据不需要确认是否送达，支持一对多

#### 22.TCP 的拥塞控制机制

​	TCP发送端维持一个拥塞窗口的变量，用来表示未接收到接收端确认的情况下可以连续发送数据的字节数，拥塞窗口的大小取决于网络的拥塞程度，并且会动态的发生改变，拥塞控制机制分为：

- 慢启动：最开始不知道网络负荷情况TCP采用试探的方法慢慢增大拥塞窗口的大小
- 拥塞避免：设置一个慢启动的阈值，当拥塞窗口的值达到阈值就减缓窗口的增长速度
- 快速重传：信号不好的时候会出现丢包的情况，快速重传要求接收方收到一个丢包的报文立即发出重复确认，为了让发送方更快知道丢包了，快速重传规定发送方只要连续收到三次重复确认就应该立即重新发送对方还没接收到的报文字段
- 快速恢复：当发生快速重传机制后，为了防止网络拥塞，将拥塞窗口的阈值减半，然后执行拥塞避免算法让阈值慢慢加大

#### 23.对 WebSocket 的理解

​	http请求只能做到客户端向服务器推送消息，不能做到服务器主动向客户端发送消息，WebSocket可以解决这个问题，并且也是基于TCP的可靠协议，客户端通过监听事件的方式来获取服务端发送的数据

#### 24.即时通讯的实现方法有哪些

- 长轮询
- 短轮询
- WebSocket

#### 25.进程之前的通信方式

- 管道通信（在内存中开辟一道缓冲区来传递数据）
- 消息队列（消息队列提供一个进程向另一个进程发送数据的方法，间接的将数据拷贝到另一个进程）
- 信号量通信（当某内存被访问时，信号量会从1变成0，当另一个进程来访问这个内存发现信号量是0就不能访问）
- 共享内存通信（映射出一块能被其他进程所访问的内存）
- 套接字通信（使用Socket进行套接字通信）

#### 26.列举你所了解的编程范式

- 声明式（告诉计算机应该做什么但是不指定具体要做什么）
- 函数式（将算法抽象成演算公式）
- 命令式（一步一步的告诉计算机应该做什么）

# Webpack 相关

#### 1.Loader是什么以及原理

​	webpack只能处理js类型的文件，loader是webpack的翻译官，用来把非js类型的文件翻译成webpack能读懂的模块，loader的原理其实就是一个编译函数，参数是要转换的文件内容，然后将编译后的结果返回出去

```json
//一个最简单的loader
module.exports = function loader(source){
	console.log("test loader run !");
	return source;
}
```

#### 2.Plugin 是什么以及原理

​	plugin是webpack的插件，提供了在webpack执行的时候扩展程序的能力，plugin可以在webpack编译过程中注册钩子并且监听webpack广播的关键事件，plugin本质上是一个类，webpack在初始化的时候会实例化这个类，然后调用它的apply方法，每个plugin必须提供一个apply方法参数是compiler对象（webpack的配置对象）,之后plugin就可以就可以通过compiler对象来监听webpack广播的事件也可以使用compiler来操作webpack

```js
//一个最简单的plugin
//plugin.js
class TestPlugin{
	constructor(options){
		//...
	}
	apply(compiler){
		//监听run事件
		compiler.plugin("run",()=>{})
	}
}

//webpack.config.js
const TestPlugin = require('./TestPlugin.js');
module.exports = {
    plugins:[
        new TestPlugin(options),
    ]
}
```

#### 3.说一些常用的Loader

- css-loader
- style-loader
- scss-loader
- less-loader
- postcss-loader
- vue-loader
- ts-loader
- babel-loader
- vue-loader
- react-loader

#### 4.说一些常用的 Plugin

- HtmlWebpackPlugin（项目打包后自动生成html文件）
- CleanWebpackPlugin（每次打包自动删除dist目录）
- DefinPlugin（可以在模板中使用%=%占位，在webpack编译过程中创建全局常量）
- uglifyjs-webpack-plugin（用来压缩js文件）
- mini-css-extract-plugin（将css代码提取到css文件中）

#### 5.打包后 dist 目录过大，解决办法？

- 关闭source-map
- 开启代码压缩
- 第三方资源挂CDN
- loader编译排除node_modules包下的文件
- TreeShaking

#### 6.什么是 webpack

​	webpack是一款构建工具，用于将JS应用打包成静态模块

#### 7.webpack 的构建流程和打包原理

- 构建流程：
  - 初始化（启动构建，读取配置文件和shell命令的参数然后合并成打包配置参数，创建compiler对象，加载plugin）
  - 编译（从入口文件出发，对每个模块调用相应的loader进行翻译，再递归寻找依赖模块进行编译处理）
  - 输出（将编译后的模块组合成chunk然后将chunk转换成文件输出到指定目录）
- 打包原理：webpack开始打包会先读取webpack.config.js的配置，然后读取启动shell命令中的参数，将这两项合并成最终的配置参数，然后通过调用webpack方法获得compiler配置对象，然后注册所有的plugin并调用他们的apply方法将compiler传入，接下来会从配置中找到入口，调用compiler.run()方法从入口开始编译。从入口开始调用配置中对应的loader对模块进行编译，继续递归寻找模块依赖进行编译处理。编译完成后得到了各模块之间的依赖关系，然后将文件输出到output指定的路径下

#### 8.webpack 的热更新是如何做到的？说明其原理

​	webpack的热更新实现需要node启动一个Express本地服务让浏览器可以访问到本地服务，还会启动一个WebSocket服务用于浏览器和node服务进行通讯，webpack监听文件变化用到了webpack-dev-middleware这个第三方库，该库可以对本地文件进行编译打包，并且在编译结束后对代码进行持续监听，当文件发生变化的时候会重新编译，每次编译结束的时候就会通过WebSocket给浏览器发送通知，浏览器拿到hash值后来检查代码是否需要更新

#### 9.webpack 如何解决循环依赖问题

​	webpack遇到循环依赖的情况会将循环依赖转换成一个异步加载的过程，在这个过程中会使用webpack的内置模块加载器和插件来实现，可以将模块分成更小的块，并且在需要的时候异步加载从而避免循环依赖的问题

#### 10.如何提高 Webpack 构建速度

- 关闭source-map
- 使用HappyPack将loader交给子进程处理
- 缩小范围（排除不需要解析的模块）
- 使用DLL动态链接（原理是将模块放到一个动态链接库当中，需要使用的时候直接从库里获取，webpack5已弃用）

#### 11.css-loader 和 style-loader 执行顺序

​	先执行css-loader解析css文件中的依赖关系，然后执行style-loader处理样式并把内容插入html中的head代码里

#### 12.简单描述下 bable 的编译过程

- 解析：对源码作词法分析、语法分析，将源码解析成机器能理解的抽象语法树AST
- 转换：遍历AST上的所有节点，针对不同类型的节点执行调用相应的转换函数对节点进行转换
- 生产：把转换完成后的AST打印成字符串并且生成source-map文件，然后输出转换完毕后的代码

#### 13.tree-shaking 实现原理是怎样的？

​	tree-shaking的实现分为三个阶段：

- 标记阶段（make）：收集模块并标记所有导出变量记录到依赖图中
- 确认阶段（seal）：遍历模块依赖关系图，确认哪些导出的变量没有被使用
- 执行阶段：调用Terser方法将所有没被使用的变量和语句进行删除

#### 14.webpack的联邦模块

​	类似于微前端，通过webpack5原生提供的插件来实现，主要是解决多个应用之间需要共享同一模块的问题，可以让我们实现跨应用的代码共享

# 手写代码

#### 1.手写 call、apply、bind 函数

```js
//call、apply用来改变函数this指向
//思路：this指向函数的调用者，把函数放到要改变this的目标对象上调用一遍
Function.prototype.myCall = function(target,...arg){
	target = target || window;
	const key = Symbol();
    //this是要改变this指向的函数 把它添加到目标对象上
	target[key] = this;
    //目标对象调用一次这个函数
	const result = target[key](...arg);
	delete target[key];
	return result;
}
//bind也是用来改变this指向，返回的是一个改变了this指向的函数
//思路：也是把函数放到目标对象上，在返回的函数中调用该函数
Function.prototype.myBind = function(target,...arg1){
	target = target || window;
	const key = Symbol();
	target[key] = this;
	return (...arg2)=>{
		const result = target[key](...arg1,...arg2);
		delete target[key];
		return result;
	}
}
```

#### 2.手写 new 操作符

```js
function myNew(fn,...args){
    //创建一个空对象，并且原型指向构造函数的原型
    let obj = Object.create(fn.prototype);
    //改变构造函数this指向,并且执行一次构造函数
    let res = fn.apply(obj,args);
    //判断构造函数是否返回一个对象
    if(res instanceof Object){
        return res;
    }else{
        return obj;
    }
}
```
#### 3.手写 instanceOf 操作符

```js
//思路：遍历左边对象的原型，如果和右边原型对象一致返回true，没找到返回false
function myInstanceOf(left,right){
    //如果左边不是对象或者函数直接返回false
	if(!["object","function"].includes(typeof left) || left === null) return false;
    //如果右边不是函数直接返回false
	if(typeof right !== "function") return false;
    //获取左边的原型对象
	let proto = Object.getPrototypeOf(left);
	while(true){
        //原型和右边原型对象一致 返回true
        if(proto === right.prototype){
			return true;
		}
        //如果原型对象是null说明找到原型链尽头了 说明没找到
		if(proto === null){
			return false;
		}
		//获取原型的原型对象
		proto = Object.getPrototypeOf(proto);
	}
}
```

#### 4.实现防抖节流函数

```js
//防抖思路：每次执行函数都清空上一次触发的定时器
function debounce(cb,delay){
	let timer = null;
	return ()=>{
		clearTimeout(timer);
		timer = setTimeout(() => {
			cb();
		}, delay);
	}
}
//节流思路：定义一个阀门，函数触发之后阀门关闭，函数执行完阀门打开
function throttle(cb,delay){
	let flag = true;
	return () => {
		if(flag){
			setTimeout(()=>{
				cb();
				flag = true;
			},delay);
		}
		flag = false;
	}
}
```

#### 5.Object.create

```js
Object.prototype.myCreate = function(obj){
    //创建一个空构造函数
	function F(){}
    //把空函数的原型对象设置为目标对象
	F.prototype = obj;
    //返回空函数的实例
	return new F();
}
```

#### 6.手写 Promise、then、race、all、any、resolve、reject

```js
//使用常量消除硬编码
const PENDING = 'pending';
const FULFILLED = 'fulfilled';
const REJECTED = 'rejected';
class MyPromise{
    //当前promise的状态
	#state = PENDING;
    //当前promise的结果
	#result = undefined;
    //回调函数的集合
	#handler = [];
    //初始化
	constructor(excutor){
		const resolve = (data)=>{
			this.#changeState(FULFILLED,data);
		}
		const reject = (reson)=>{
			this.#changeState(REJECTED,reson);
		}
        //执行一遍参数函数
		try {
			excutor(resolve,reject);
		} catch (err) {
			reject(err);
		}
	}
    //当promise状态发生变化改变状态和promise结果 并且调用一次run方法
	#changeState(state,data){
		if(this.#state === PENDING){
			this.#state = state;
			this.#result = data;
		}
		this.#run();
	}
    //把then的回调放入微任务队列中执行
	#runMicroTask(func){
        //如果是node环境使用process.nexTick方法
		if(typeof process === 'object' && typeof process.nextTick === 'function'){
			process.nextTick(func);
		}else{
        //浏览器环境使用MutationObserver监听一个文本节点 手动发生改变来触发微任务
			const ob = new MutationObserver(func);
			const textNode = document.createTextNode("1");
			ob.observe(textNode,{characterData:true});
			textNode.data = "2";
		}
	}
    //判断一个对象是否为promise A+规范(有then方法的对象或者函数)
	#isPromiseLike(data){
		if(typeof data !== null && (typeof data === 'function' || typeof data === 'object')){
			return typeof data.then === 'function';
		}
		return false
	}
    //抽离run方法
	#runOne(callback,resolve,reject){
		this.#runMicroTask(()=>{
			if(typeof callback !== 'function'){
                //如果then传入的不是函数就透传给下一个then
				const setted = this.#state === FULFILLED ? resolve : reject;
				setted(this.#result);
				return;
			}
			try {
                //如果是函数就触发回调函数 并且获取函数的返回值
				const data = callback(this.#result);
                //函数返回值是一个promise直接调用它的then方法
				if(this.#isPromiseLike(data)){
					data.then(resolve,reject);
				}else{
                //不是promise就调用resolve链式触发then
					resolve(data);
				}
			} catch (err) {
                //then里抛出异常也会被catch捕获
				reject(err);
			}
		})
	}
    //执行then的回调
	#run(){
		if(this.#state === PENDING) return;
        //遍历回调集合中的方法并执行(为了防止多次then同一个promise)
		while(this.#handler.length){
			const {onFulfilled,onRejected,resolve,reject} = this.#handler.shift();
			if(this.#state === FULFILLED){
				this.#runOne(onFulfilled,resolve,reject);
			}else{
				this.#runOne(onRejected,resolve,reject);
			}
		}
	}
	//执行then方法返回一个新的promise并且把回调函数放入handler中 然后执行一次run
	then(onFulfilled,onRejected){
		return new MyPromise((resolve,reject)=>{
			this.#handler.push({
				onFulfilled,
				onRejected,
				resolve,
				reject
			});
			this.#run();
		});
	}
	//catch就是then的第二个回调函数
	catch(onRejected){
		return this.then(undefined,onRejected);
	}
	//不管then是成功还是失败都执行一次finally的回调
	finally(onFinally){
		return this.then(()=>{
			onFinally();
		},()=>{
			onFinally();
		});
	}
	//静态方法 返回一个成功的promise
	static resolve(data){
		if(data instanceof MyPromise) return data;
		return new MyPromise((resolve,reject)=>{
			resolve(data);
		});
	}
	//静态方法 返回一个失败的promise
	static reject(reson){
		return new MyPromise((resolve,reject)=>{
			reject(reson);
		});
	}
	//静态方法 接收一个promise集合,只要有一个失败,则返回失败结果,全部成功才返回结果集合
	static all(promises){
		const len = promises.length;
		let results = [];
		let count = 0;
		return new MyPromise((resolve,reject)=>{
			for(let i = 0; i < len; i ++){
				MyPromise.resolve(promises[i]).then(res=>{
					results[i] = res;
					count ++;
				}).catch(err=>{
                    //只要有一个失败就返回失败的回调结果
					reject(err);
				});
                //集合所有promise执行完并且状态都是成功就返回成功集合
				if(count === results.length){
					resolve(results);
				}
			}
		});
	}
	//静态方法 接收一个promise集合,返回状态最先改变的那个promise
	static race(promises){
		return new MyPromise((resolve,reject)=>{
			const len = promises.length;
            //正常遍历即可
			for(let i = 0; i < len; i ++){
				MyPromise.resolve(promises[i]).then(res=>{
					resolve(res);
				}).catch(err=>{
					reject(err);
				});
			}
		});
	}
	//静态方法 接收一个promise集合,只要有一个成功,则返回成功结果,全部失败才返回结果集合
	static any(promises){
		const len = promises.length;
		let results = [];
		let count = 0;
		return new MyPromise((resolve,reject)=>{
			for(let i = 0; i < len; i ++){
				MyPromise.resolve(promises[i]).then(res=>{
					resolve(res);
				}).catch(err=>{
					count++;
					results[i] = err;
				});
				if(count === results.length){
					reject(results);
				}
			}
		});
	}
}
```

#### 7.实现深拷贝

```js
function deepClone(obj){
	let result = Array.isArray(obj) ? [] : {};
	for(let key in obj){
        //过滤for in遍历到原型链上的属性
		if(obj.hasOwnProperty(key)){
            //如果子元素也是对象,就递归处理
			if(obj[key] && typeof obj[key] === 'object'){
				result[key] = deepClone(obj[key]);
			}else{
            //普通类型直接拷贝
				result[key] = obj[key];
			}
		}
	}
	return result;
}
```

#### 8.交换 a,b 的值，不能用临时变量

```js
var a = 5;
var b = 10;
a = a + b;
b = a - b;
a = a - b;
```

#### 9.实现数组的乱序输出

```js
//思路 洗牌算法 每次循环取一个随机位插入到最后一位
function disorder(arr){
	for(let i = arr.length; i > 0; i--){
		const j = Math.floor(Math.random() * i);
		let x = arr[i - 1];
		arr[i - 1] = arr[j];
		arr[j] = x;
	}
	return arr;
}
```

#### 10.数组求和

```js
function sum(arr){
	return arr.reduce((a,b)=>{
		return a + b;
	})
}
```

#### 11.实现数组的扁平化

```js
function flat(arr){
	let res = [];
	for(let i = 0; i < arr.length; i ++){
		if(Array.isArray(arr[i])){
			res = res.concat(flat(arr[i]));
		}else{
			res.push(arr[i]);
		}
	}
	return res;
}
```

#### 12.实现数组的 filter 方法

```js
Array.prototype.MyFilter = function(cb){
	let res = [];
	for(let i = 0; i < this.length; i ++){
		if(cb(this[i],i,this)){
			res.push(this[i]);
		}
	}
	return res;
}
```

#### 13.实现数组的 map 方法

```js
Array.prototype.MyMap = function(cb,context){
	let res = [];
	for(let i = 0; i < this.length; i ++){
		res.push(cb.call(context,this[i],i,this));
	}
	return res;
}
```

#### 14.循环打印红黄绿（红灯 3s 亮一次，绿灯 1s 亮一次，黄灯 2s 亮一次；如何让三个灯不断交替重复亮灯？）

```js
function trafficLight(){
	const task = (color,delay,callback) =>{
		setTimeout(() => {
			switch (color) {
				case "red":
					console.log("red");
					break;
				case "yellow":
					console.log("yellow");
					break;
				case "green":
					console.log("green");
					break;
			}
			callback();
		}, delay);
	}
	const step = ()=>{
		task("red",1500,()=>{
			task("yellow",1000,()=>{
				task("green",500,()=>{
					step();
				})
			})
		})
	}
	step();
}
```

#### 15.实现每隔一秒打印 1,2,3,4

```js
for(let i = 0; i < 4; i ++){
	setTimeout(()=>{
		console.log(i + 1);
	},i*1000)
}
```

#### 16.实现发布-订阅模式

```js
class PubSub{
	constructor(){
		this.eventListeners = {};
	}
	//监听事件
	on(event,handler){
		if(typeof handler !== 'function'){
			throw new Error("Event handler should be a function")
		}
		if(this.eventListeners[event]){
			this.eventListeners[event].push(handler);
		}else{
			this.eventListeners[event] = [handler];
		}
	}
	//取消事件函数
	off(event,handler){
		if(typeof handler !== 'function'){
			throw new Error("Event handler should be a function")
		}
		if(!this.eventListeners[event]) return;
		this.eventListeners[event] = this.eventListeners[event].filter((fn)=>{
			return handler !== fn;
		});
	}
	//提交事件
	emit(event,...arg){
		if(this.eventListeners[event].length > 0){
			this.eventListeners[event].forEach(fn => {
				fn.apply(this,arg)
			});
		}
	}
}
```

# 项目相关

#### 1.优化项目的方法

- 代码压缩、静态文件压缩
- 图片懒加载、路由懒加载
- 第三方资源按需引入
- TreeShaking
- 静态资源使用CDN托管
- 减少http请求
- 使用浏览器缓存

#### 2.常见兼容性问题有哪些

- CSS属性（flex，grid等）
- DOM的方法和事件
- 盒模型
- !important  IE6不兼容
- IE6绝对定位

#### 3.什么是 CDN

​	CDN（内容分发网络），分布在世界各地的服务器，作用是在源服务器之前拦截作一层缓冲，将资源缓存到世界各地的服务器上，获取资源的时候不去源服务器上获取，而是去离自己最近的服务器上获取资源，可以减少源服务器的压力

#### 4.懒加载是什么

​	懒加载就是当需要使用到该资源的时候才去加载，否则不会加载该资源

#### 5.如何优化动画？

​	可以使用requestAnimationFream来实现js动画，它比定时器的性能更好，并且浏览器失去焦点的时候会暂停动画

#### 6.如何对项目中的图片进行优化？

- 压缩图片
- 使用雪碧图
- 图片挂载到CDN
- 图片本地缓存

#### 7.什么是单点登录？如何做单点登录？

​	单点登录是指在同一个系统不同的页面不需要重复登录，具体实现方案：单一域名把cookie种在根域名下实现单点登录，多域名需要实现一个认证中心，用户访问系统A(www.app-a.com)判断未登录，跳转到认证中心页面（www.sso.com），在认证中心输入账号密码登录生成sso-cookie到认证中心域名下(www.sso.com)，重定向到系统A并带上生成的ticket参数（www.app-a.com?ticket=xxx）,系统A请求后端去sso服务验证，验证成功后把cookieA种在系统A的域名下,后面访问直接通过cookieA去访问就不需要登录了。用户访问B系统（www.app-b.com）重定向到认证中心，发现有sso-cookie说明已经登录过了，则直接重定向到系统B（www.app-b.com）,并且带上生成的ticket参数（www.app-b.com?ticket=xxx）,然后系统B请求后端去sso服务验证，验证成功后把cookieB种在系统B的域名下

# 主观问题

1. 你都做过什么项目呢？具体聊某一个项目中运用的技术
2. 项目中遇到过什么技术难点，是怎么解决的
3. 开发中会使用一些什么工具软件
4. 除了前端还有了解过其他的技术吗
5. 对前端开发这个岗位的理解
6. 你有什么优点，<!--有什么缺点-->
