### react tutorial ###

学习react组建开发

React 涉及的主要概念：

- Component
- JSX
- Virtual  DOM
- Data Flow

*JSX*

React 允许将 HTML 代码直接嵌入到 JS 代码中，对于长久以来一直被"表现与逻辑分离"的思想洗脑，要接受这种代码的书写方需要一定的过程，而一旦熟悉了这种在 JS 中支持 HTML 的写法，就会发现 JSX 的聪明之处。

传统的 MVC 是将模板放在其他地方，比如 `<script>` 标签或者模板文件，再在 JS 中通过某种手段引用模板（在Angular1中便是使用这种方式）。React 则把 HTML 模板直接嵌入到 JS 代码里面，做到了模板和组件的直接关联。

组件属性：为了和原生的 HTML 标签进行区分，组件变量使用大写开头，而且为了和原生属性以及 js 关键字区分，组件属性中的 class 要写成 className，submit 要写成 htmllType="submit" ， for 要写成 "htmlFor"，其他类推。

JS 表达式：组件属性中使用表达式，要用 {} 替换 " " ，同时在 JSX 进行注释要用 {} 包起来。


 *Virtual DOM*

当组件状态 state 有更改的时候，React 会自动调用组件的 render 方法重新渲染整个组件的 UI。但是如此大规模地操作 DOM ，会对性能造成很大的影响，因此 React 实现了一个 Virtual DOM，在 这个Virtual DOM 实现了一个 diff 算法，当 state 变化时，便通过 diff 寻找需要更新的节点，再把这个修改更新到浏览器的 DOM 节点上，相当于实现了局部的更新，在性能上比原生的 DOM 要快许多。

*核心思想：封装组件*

React 十分强调组件的概念，对于所有功能独立的模块都可以抽离成组件，然后在需要的地方 import ，降低了代码之间的耦合性，并且方便维护。

在React 中组件有两个概念：props 和 state。一个组件就是通过这两个属性的值在 render 方法里面生成这个组件对应的 HTML 结构。需要注意的是，一个组件只能有一个根节点（在这一点上，vue.js 也一样）

props：组件属性由外部通过 JSX 属性传入设置，比如由父组件传递过来的 id，通过路由获取到的 url 参数等等。props一旦设置完成，一般是不可更改的。

state：state 是组件的当前状态，可以把组件简单看成一个“状态机”，根据状态 state 呈现不同的 UI 展示。

一旦状态（数据）更改，组件就会自动调用 render 重新渲染 UI，这个更改的动作会通过 this.setState方法来触发。

组件生命周期
装载
componentWillMount： 只会在装载之前调用一次，在 render 之前调用，你可以在这个方法里面调用 setState 改变状态，并且不会导致额外调用一次 render
componentDidMount：只会在装载完成之后调用一次，在 render 之后调用，从这里开始可以通过 ReactDOM.findDOMNode(this) 获取到组件的 DOM 节点。
更新
componentWillReceiveProps
shouldComponentUpdate
componentWillUpdate
componentDidUpdate
卸载
componentWillUnmount


*Data Flow*

React 的架构方式是单向的数据绑定，在之前的开放过程中没有直接使用到这个功能，但是 Ant Design 组件已经封装好了大量的具有数据绑定功能的组件，因此使用起来也十分方便，在之后的项目中，随着应用的逐步扩大和复杂，单向数据绑定会变得十分实用。