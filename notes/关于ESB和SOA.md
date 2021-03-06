# ESB(企业服务总线) & SOA(面向服务架构)
## 服务
* 为让复杂的系统环境，还可以方便扩展，不同模块之间不能直接一步一步地通信；
* 需要分离接口；需要调度不同的应用；
* 如果不借助调度，假设有几百上千个应用；每个应用都有自己独特的生态系统，都需要用10个物理服务器或者设备跑在上门；所有这些群体彼此之间需要不断、持续交换信息；
* 需要变更IT系统的结构；需清楚的：系统和应用 很少用来被创建成导出推送数据，它们是为了支持业务(银行业务、声音记录等等)，下面，可以来重新设计系统服务；
* 服务能重用、原子性，为其他的应用提供功能，但是，它不会用点对点的方式直接暴露出来；
* 一个给定的功能系统要作为服务，三个条件：I nteresting 有趣;R eusable 可重用;A tomic 原子性;

## 使用SOA架构，用ESB提供服务
* 理解系统不直接交换信息；理解“服务”-->开始使用ESB；
* ESB的工作：提供和调用-"集成系统的->服务"
```
多数情况，每个系统和ESB之间，只需要定义一个访问方法、一个接口；
假设有8个系统，就会有16个接口(双向)需要被创建、维护、管理和关注；
如果没有ESB，就需要56个接口去处理(假设每个系统都需要跟其他系统对话)，少了40个接口意味着少花时间和金钱；
```
* ESB的好处：
```
节省接口，节省外部调http负担，节省维护代价；
一个系统重写，其他系统不需要周知，因为他们与ESB的接口不变；
```
* ESB的责任
```
如果每天使用IRA服务，可以考虑组合他们；
选择原子的服务，组合成混合服务；提供给某些客户端系统需要的特定的数据组合；
这样的架构，人们可以只关注ESB，处理与ESB相关的事情，享用它提供的有趣服务；

```
* 注意：需要你整理架构，然后放到ESB上；如果只是简单安装ESB，什么接口都往上放，而没有梳理出大块的服务，基本没什么用；
## 使用ESB的3条原则
* 直接对外的{重度频繁接口}直接做【微服务】并考虑将来直接做并发多实例；
* 外部{频繁调用}但{不是保持一直重度访问}的且{没有复杂上下游接口调用}的可以考虑做成[微服务]并【容器化】；
* {复杂逻辑的多接口调用}-->一个大接口，走esb
