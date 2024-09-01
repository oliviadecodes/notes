为了更好的提供给浏览者想要的内容和信息，需要有一些输入和输出的机制，让浏览者可以输入一些东西，
然后给他对应的一些输出内容，所以有了表单的能力，有了表单自然还需要一些表单校验，和计算的能力。
所以JavaScript 作为一种校验和计算的脚本，诞生了。


由于当时没有一个标准化组织可以对技术进行统一，因此两者对同一功能的实现往往大相径庭。
当时两者都具有很高的市场份额，网站开发者不得不开发出能同时在两个浏览器上运行的代码，
使开发者的工作量成倍的增多。



为各大主流浏览器提供了统一的接口，只要提供一份jQuery规范的代码，就可以在各大浏览器上正常运行除了进行浏览
器兼容，jQuery还对JavaScript本身提供了很多的扩展，提供了诸如DOM操作、css选择器、异步队列、数据缓存、动
画、属性操作、事件封装、ajax请求封装等一系列的功能，使前端开发进入了一个崭新的时代。



ES5规范的提出，使JavaScript进一步成熟，在编程语言市场占有了一席之地。紧接着，ECMA标准组织又推出了ES6规范，为这门语言提供了相当多的现代语言特性，
大大增强了其对前端环境的适应力。同时也为JavaScript进入后端开发奠定了基础。




由于JavaScript单线程的语言特性以及不具备如java般严谨的面向对象特征，它一度被认为只能用于前端开发，不能适应后端复杂业务逻辑的开发，这主要基于三点：

单线程特性，无法充分利用多核CPU强大的计算能力，不利于开发分布式应用
不够安全，一旦主线程出错，整个执行过程就会崩溃
没有严谨的面向对象特性，封装程度不够，无法处理复杂的业务逻辑

但同时作为面向前端浏览器环境所设计的一门语言，JavaScript也具有一些其他大部分语言没有的特性，最典型的包括其事件循环机制，同时单线程的特点也可以说是有利有弊。

利用JavaScript的这些语言特点，Ryan Dahl于2009年发布了JavaScript的服务器端运行环境nodejs。它基于谷歌浏览器广受好评的JavaScript引擎–V8引擎，是一个事件驱动的非阻塞I/O模型。它将所有的客户端请求都交给事件循环机制来处理，从而将I/O代价降到极低。由于单线程的语言机制，它不需要处理复杂的线程同步问题，更不会发生死锁等线程问题。随着ES6规范中web worker的出现，nodejs也具备了利用多核CPU的能力（当然仍然无法与java相提并论）。




英雄终有落幕，尽管jQuery红极一时，但是终究无法应对越来越复杂的前端开发工作。一方面，jQuery大量的优秀特性已经被吸纳为JavaScript标准。另一方面，占有其60%代码量的DOM操作已经被公认为网页的性能杀手，因为DOM操作需要反复地操作文档，并触发网页的重绘和重排，这会严重影响网页的性能，最严重的可能导致页面卡死。此外，使用jQuery开发的网站，会因为大量的DOM操作，需要书写大量的代码，从而变得难以维护。
我们需要有一种更优雅的方式来操作页面，以获得更优秀的用户体验。

为了解决这些问题，前端兴起了组件化开发和MVVM开发模型。



现代化前端框架通常都是实现 MVVM 的方案，数据层（M）和 视图层（V）相互连接，同时变更，使得页面交互保持高度的一致性。
前端组件化开发，就是将页面的某一部分独立出来，将这一部分的 数据层（M）、视图层（V）和 控制层（C）用黑盒的形式全部封装到一个组件内，暴露出一些开箱即用的函数和属性供外部组件调用。





1.判断回文数

var isPalindrome = function(x) {
    let m = 0;
    const temp = String(x).split('');
    // let m = temp.reverse().join('');
    for (let i = temp.length - 1; i >= 0; --i) {
        m += temp[i] * Math.pow(10, i);
    }
    if (x == m) { 
        return true;
    } else {
        return false;
    }
};

2.封装个数组的jion方法
function Join(arr, temp) {
  let stringData;
  if (temp === "undefined") {
    return arr.toString();
  } else if (typeof temp !== 'string') {
    return false;
  }
  for (let i = 0; i < arr.length - 1; i++) {
    stringData = (stringData ? stringData : arr[i]) + temp + arr[i + 1];
  }
  return stringData;
}

var a = [1, 2, 3, 4, 5];
console.log(Join(a, "-"));
console.log(Join(a, ""));
console.log(Join(a));



AFox基于electron开发的一个抓包工具。electron，有两个进程一个主进程，一个渲染进程。主进程监听接口返回的数据传给渲染进程进行渲染配置webpack创建一个子进程去获取执行命令的结果，然后通过插件DefinePlugin，付给一个全局变量。

![image-20220706155241097](/Users/wangpeizhen/Library/Application Support/typora-user-images/image-20220706155241097.png)





React https://www.jianshu.com/p/9463f42d8457 React 和 Vue 的 diff 时间复杂度O(n^3) 和 O(n) 是如何计算出来的链接：https://jishuin.proginn.com/p/763bfbd4ec42O(n^3)确切地说，树的最小距离编辑算法的时间复杂度是O(n^2m(1+logmn)), 我们假设m 与 n 同阶， 就会变成 O(n^3)。关于O(n)怎么计算出来的React 将 Virtual DOM 树转换为 actual DOM 树的最小操作的过程称为调和， diff 算法便是调和的结果，React 通过制定大胆的策略，将 O(n^3)的时间复杂度转换成 O(n)。1. diff 策略下面是 React diff 算法的 3 个策略：	•	策略一：Web UI 中 DOM 节点跨层级的移动操作特别少。可以忽略不计。 	•	策略二：拥有相同类的两个组件将会生成相似的树形结构，拥有不同类的两个组件将会生成不同的树形结构。 	•	策略三：对于同一层级的一组子节点，它们可以通过唯一 id 进行区分。 基于以上三个策略，React 分别对 tree diff、component diff 以及 element diff 进行算法优化。说一下类组件和函数组件的区别?1. 语法上的区别： 函数式组件是一个纯函数，它是需要接受props参数并且返回一个React元素就可以了。类组件是需要继承React.Component的，而且class组件需要创建render并且返回React元素，语法上来讲更复杂。 2. 调用方式 函数式组件可以直接调用，返回一个新的React元素；类组件在调用时是需要创建一个实例的，然后通过调用实例里的render方法来返回一个React元素。 3. 状态管理 函数式组件没有状态管理，类组件有状态管理。 4. 使用场景 类组件没有具体的要求。函数式组件一般是用在大型项目中来分割大组件（函数式组件不用创建实例，所有更高效），一般情况下能用函数式组件就不用类组件，提升效率。Fiber源码速览 https://juejin.im/post/5bea68a6e51d450cb20fdd70 父子组件生命周期函数执行顺序： 进入页面：parent-constructor -> parent-getDerivedStateFromProps -> parent-render -> child-constructor -> child-getDerivedStateFromProps -> child-render -> child-componentDidMount -> parent-componentDidMount更新页面：parent-getDerivedStateFromProps -> parent-shouldComponentUpdate -> parent-render -> child-getDerivedStateFromProps -> child-shouldComponentUpdate -> child-render -> child-componentDidUpdate -> parent-componentDidUpdate销毁页面：parent-componentWillUnmount -> child-componentWillUnmountgetDerivedStateFromProps ： 从props中获取stateReact新的生命周期，为什么 getDrivedStatefromProps 是静态的？React HookuseMemo 和 useCallback 目的：useCallback 和 useMemo 是react的hooks中的两个函数，专门用于性能优化的。执行时机：useCallback 和 useMemo 在第一次渲染组件的时候，就会执行，拿到各自的缓存；之后，当它们的依赖发生改变的时候，才会执行。useCallback缓存的是函数useMemo缓存的是值两者之间的比较：useMemo和useCallback都是reactHook提供的两个API，用于缓存数据，优化性能；两者接收的参数都是一样的，第一个参数表示一个回调函数，第二个表示依赖的数据。共同作用：在依赖数据发生变化的时候，才会调用传进去的回调函数去重新计算结果，起到一个缓存的作用两者的区别：useMemo 缓存的结果是回调函数中return回来的值，主要用于缓存计算结果的值，应用场景如需要计算的状态useCallback 缓存的结果是函数，主要用于缓存函数，应用场景如需要缓存的函数，因为函数式组件每次任何一个state发生变化，会触发整个组件更新，一些函数是没有必要更新的，此时就应该缓存起来，提高性能，减少对资源的浪费；另外还需要注意的是，useCallback应该和React.memo配套使用，缺了一个都可能导致性能不升反而下降。useCallback返回一个函数，当把它返回的这个函数作为子组件使用时，可以避免每次父组件更新时都重新渲染这个子组件useMemo返回的的是一个值，用于避免在每次渲染时都进行高开销的计算



2月5日计划（周日）

- Vue视频 30 - 47
- 运动25分钟
- 喝两半杯水
- 九点半起床

2月6日计划（周一）

- Vue视频 48 - 69
- 运动25分钟
- 喝两杯水
- 九点起床

2月7日计划（周二）

- Vue视频 70 - 77
- 运动25分钟
- 喝两杯水
- 九点起床
- 复习基础知识和自己总结的八股文

2月8日计划（周三）

- 8:45起床
- 运动30分钟
- 喝两杯水
- 投简历复习简历里的知识，看网站上的八股文
- Vue视频 78 - 82