---
title: bear's 杂谈
---

写这篇文章的起因是因为我的好朋友最近面试不顺，所以帮她总结一下我眼中成熟的java 后台工程师应该具备的技能和需要看的书。顺便给自己新开的github开个张\~

## [](#如何快速准备面试 "如何快速准备面试")如何快速准备面试

其实，个人感觉面试那段时间其实是最后的冲刺了，其实是需要平时就进行拓展阅读，对技术有一定的理解，面试的时候才能针对面试官的提问进行深层次的回答。  
当然，如果拓展的少，需要快速恶补，可以在github上找一些面试指南来进行恶补。个人建议参考博客：[java guide](https://github.com/Snailclimb/JavaGuide)，这个本身就是专门为技术面试而写的，可以先把所有的知识点记下来，然后再根据结合自己的项目和实际情况来进行拓展，个人感觉可以按照以下几点来准备\(以redis 为例\)：

* redis 最新版本中发布的最新特性
* redis 的单机、集群、哨兵、cluster模式的演化,为了解决什么问题，以及实际过程中的具体实现（请背熟所在公司的redis 架构）
* 因为redis 属于缓存，所以可以拓展看一下缓存的相关知识点，推荐[深入分布式缓存：从原理到实践](https://item.jd.com/12276070.html)

以上是基本操作，推荐一波我感觉非常棒的书和博客

## [](#java-基础 "java 基础")java 基础

这个看《JAVA 卷1》和《JAVA 卷2》即可

## [](#Java进阶 "Java进阶")Java进阶

主要是和并发编程相关的，以及建议积累一下JAVA 性能调优相关的知识

* 并发编程推荐书单  
  《JAVA 并发编程实战》 JAVA 并发入门书籍，强推  
  《实战JAVA 高并发程序设计》这本书开头对JAVA 并发的一些概念进行了总结，个人感觉《JAVA 并发编程实战》有些概念可能因为翻译问题不那么好懂
* JAVA 线上异常处理  
  主要是希望对JAVA 程序下经常出现的一些异常有一些积累，比如oom、jvm 一直full gc该如何排查问题。其实一般只需要知道发现异常后如何快速保存现场，然后用对应的工具进行分析即可。
* JAVA 性能调优  
  这个其实是一个很大的概念，推荐一个专栏[Java性能调优实战](https://time.geekbang.org/column/article/102619)  
  当然，这块也有一些佛脚也可以报一下，下面我介绍一下入门级概。首先需要知道其实在Java web的性能调优分为5块了：
* 接口调优 这块主要是对接口的性能进行优化，常用技术包括：a.降低报文的大小 b.加缓存 c.调小对下游超时时间 d.改串行为并行 （包括采用并发、使用消息解耦同步操作为异步等做法）e.对并发程序的优化，包括减少锁的竞争，降低锁的力度等等
* JVM 调优 GC时会stop了world,频繁的gc必然影响程序的运行，所以对参数进行合理的调整也可以带来性能的提升。
* 存储调优 包括对使用的缓存和mysql的调优 比如redis，不推荐使用大key大value\(目前很多地方使用的redis单进程，使用大key 大value很容易导致慢查询！\)mysql则包括sql慢查询、分库分表等
* 服务器+网关等调优 服务器级别的调优理解不深…推荐一本书《性能之巅》（我还在研究中）服务器级别的性能调优，可以了解Linux自带的perf指令  
  不过其实这里一般是就是简单粗暴答++++机器也就够了
* 架构调优

  ## [](#Java-web "Java web")Java web

  主要是spring相关知识

  ## [](#jvm "jvm")jvm

  这个不用说了《深入理解Java虚拟机：JVM高级特性与最佳实践》人手一本了，个人感觉重点在这里:
* JVM 基础知识
* jvm 对JAVA 并发的支持（Java中有些锁是依赖jvm实现的，这个必须清楚）
* jvm 调优

## [](#Java-web-1 "Java web")Java web

dubbo 其实没啥可说的，就是dubbo的常用参数、架构等必须知道

## [](#中间件相关 "中间件相关")中间件相关

消息队列  
研发还是建议对kafka、rabbit qmq等有一些了解，不要只局限在自研的mq上

## [](#redis-相关 "redis 相关")redis 相关

[Redis 开发与运维](https://item.jd.com/12121730.html)  
个人感觉这本书把redis讲的比较清楚，看完基本上就懂redis了  
此外 redis 实现消息队列、分布式锁建议手写一下

## [](#数据库 "数据库")数据库

[高性能MySQL](https://item.jd.com/11220393.html) 这本书讲的很全面，但是目测看不完  
这个专栏强推：  
[MySQL实战45讲](https://time.geekbang.org/column/article/0?cid=100020801)  
研发比如对sql语句调优、索引、数据库事务（MVCC）、分布式数据库有理解  
此外，JAVA web目前都是spring+mybatis+mysql 3件套，所以建议对mybatis 进阶知识也了解一下,例如mybatis缓存等，附上个参考链接  
<https://www.w3cschool.cn/mybatis/mybatis-xlc73bt4.html>

## [](#架构设计相关 "架构设计相关")架构设计相关

是滴….小qa也有一颗想review架构的梦想….ヾ\(◍°∇°◍\)ﾉﾞ  
[大型网站系统与Java中间件实践](https://item.jd.com/13184550.html) 这本书不错，但是看得时间太久了，有点忘记讲了什么了

以上聊了这么多，都是rd相关的，作为一名qa，也推荐一些我感觉在测试方面不错的书

## [](#精准测试 "精准测试")精准测试

[不测的秘密，精准测试之路](https://e.jd.com/30402411.html?ebook=1)  
精准测试是依然是目前测试工作中最有价值的研究方向之一，这本书写了腾讯在这方面的一些实战，可以拓展一下视野

## [](#性能测试 "性能测试")性能测试

推荐极客时间的一个专栏：  
[性能测试实战30讲](https://time.geekbang.org/column/article/0?cid=100042501)

