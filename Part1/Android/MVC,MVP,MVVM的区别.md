#MVC,MVP,MVVM的区别
---


#MVC
软件可以分为三部分

* 视图（View）:用户界面
* 控制器（Controller）:业务逻辑
* 模型（Model）:数据保存

各部分之间的通信方式如下：

1. View传送指令到Controller
2. Controller完成业务逻辑后，要求Model改变状态
3. Model将新的数据发送到View，用户得到反馈

Tips：所有的通信都是单向的。

#互动模式
接受用户指令时，MVC可以分为两种方式。一种是通过View接受指令，传递给Controller。

另一种是直接通过Controller接受指令


#MVP

MVP模式将Controller改名为Presenter，同时改变了通信方向。

1. 各部分之间的通信，都是双向的
2. View和Model不发生联系，都通过Presenter传递
3. View非常薄，不部署任何业务逻辑，称为"被动视图"(Passive View)，即没有任何主动性，而Presenter非常厚，所有逻辑都部署在那里。


#MVVM

MVVM模式将Presenter改名为ViewModel，基本上与MVP模式完全一致。

唯一的区别是，它采用双向绑定(data-binding)：View的变动，自动反映在ViewModel，反之亦然。


#VIPER 
VIPER 应该是架构里面职责划分最为明确的，真正做到了SOLID 原则。其他架构因为有VC 的存在，或多或少都会导致各层的职责划分不明确。但是也由于VIPER 的分成过多，并且是唯一一个把界面路由功能单独分离出来放到一个单独的类里面处理，所有的事件响应和界面跳转都需要自己处理，这导致代码复杂度大大增加。

apple 苦心孤诣的给我们搞出一个VC，虽然会导致层次耦合，但是也确实简化了开发流程，而VIPER 则是彻底抛弃了VC，重新进行分层，做到了每个模块都可以单独测试和复用，但是也导致了代码过多，逻辑比较绕的问题。

mvvm 是为了解决C 层臃肿，MVC难以测试的问题，其实并不是这样，按照架构演进顺序来看，C层臃肿大部分是没有拆分好MVC 模块，好好拆分就行了，用不着MVVM。
而MVC 难以测试也可以用MVP 来解决，只是MVP 也并非完美，在VP 之间的数据交互太繁琐，所有才引出了MVVM。而VIPER 则是跳出了MVX 架构，自己开辟一条新的路。

VIPER 是非常干净的架构。它将每个模块与其他模块隔离开来。因此，更改或修复错误非常简单，因为您只需要更新特定的模块。此外，VIPER 还为单元测试创建了一个非常好的环境。由于每个模块独立于其他模块，因此保持了低耦合。在开发人员之间划分工作也简单。
不应该在小项目中使用VIPER，因为MVP 或MVC 就足够了。

VIPER 各层职责
interactor（交互器）--这是应用程序的主干，因为它包含应用程序中用例描述的业务逻辑。交互器负责从数据层获取数据，并执行特定场景下的业务逻辑，其实现完全独立于用户界面。
Presenter（展示器）--它的职责是从用户操作的Interactor获取数据，创建一个Entities 实例，并将其传送到View 以显示它。
Entities（实体）--纯粹的数据对象。不包括数据访问层，因为这是Interactor 的职责。
Router（路由）--负责VIPER 模块之间的跳转。
View（视图）---视图的责任是将用户操作发送给演示者，并显示presenter 告诉它的任何内容。

VIPER 架构的主要优点
1、简化复杂项目。由于模块独立，VIPER 对呀大型团队来说真的很好。
2、使其可扩展。是开发人员尽可能无缝地同时处理它。
3、代码达到了可重用性和可测试性
4、根据应用程序的作用划分应用程序组件，设定明确的责任
5、可以轻松添加新功能。
6、由于UI逻辑与业务逻辑分离，因此可以轻松编写自动化测试
7、它鼓励分离使得更容易采用TDD 的关注。Interactor包含独立于任何UI的纯逻辑，这使得通过测试轻松开车。
8、创建清晰明确的接口，独立于其他模块。这使得更容易更改界面向用户呈现各种模块的方式。
9、通过单一责任原则，通过奔溃报告更容易地跟踪问题。
10、使源代码更清洁，更紧凑和可重用。
11、减少开发团队内的冲突数量
12、适用SOLID 原则
13、使代码看起来类似。阅读别人的代码变得更快。

VIPER 架构有很多好处，但重要的是要将其用于大型和复杂的项目。由于所涉及的元素数量，这种架构在启动新的小型项目时或导致开销，因此VIPER 架构可能会对无意扩展的小型项目造成过高的影响。




































