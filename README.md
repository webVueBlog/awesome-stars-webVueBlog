<div align="center">

# awesome-stars-webVueBlog

[![Auth](https://img.shields.io/badge/Auth-webVueBlog-ff69b4?logo=github)](https://github.com/webVueBlog/awesome-stars-webVueBlog)
[![GitHub Pull Requests](https://img.shields.io/github/stars/webVueBlog/awesome-stars-webVueBlog?logo=Undertale)](https://github.com/webVueBlog/awesome-stars-webVueBlog/stargazers)
[![HitCount](https://views.whatilearened.today/views/github/webVueBlog/awesome-stars-webVueBlog.svg)](https://github.com/webVueBlog/awesome-stars-webVueBlog)

🤩 我的star列表，每天凌晨自动更新 🤩

<img src="https://camo.githubusercontent.com/82291b0fe831bfc6781e07fc5090cbd0a8b912bb8b8d4fec0696c881834f81ac/68747470733a2f2f70726f626f742e6d656469612f394575424971676170492e676966" width="800"  height="3">
</div><br>

# 数据结构

## 队列

*   [《java队列——queue详细分析》](https://www.cnblogs.com/lemon-flm/p/7877898.html)
    *   非阻塞队列：ConcurrentLinkedQueue(无界线程安全)，采用CAS机制（compareAndSwapObject原子操作）。
    *   阻塞队列：ArrayBlockingQueue(有界)、LinkedBlockingQueue（无界）、DelayQueue、PriorityBlockingQueue，采用锁机制；使用 ReentrantLock 锁。

*   [《LinkedList、ConcurrentLinkedQueue、LinkedBlockingQueue对比分析》](https://www.cnblogs.com/mantu/p/5802393.html)

## 集合

*   [《Java Set集合的详解》](https://blog.csdn.net/qq_33642117/article/details/52040345)

## 链表、数组

*   [《Java集合详解--什么是List》](https://blog.csdn.net/wz249863091/article/details/52853360)

## 字典、关联数组

*   [《Java map 详解 - 用法、遍历、排序、常用API等》](https://baike.xsoftlab.net/view/250.html)

## 栈

*   [《java数据结构与算法之栈（Stack）设计与实现》](https://blog.csdn.net/javazejian/article/details/53362993)
*   [《Java Stack 类》](http://www.runoob.com/java/java-stack-class.html)
*   [《java stack的详细实现分析》](https://blog.csdn.net/f2006116/article/details/51375225)
    *   Stack 是线程安全的。
    *   内部使用数组保存数据，不够时翻倍。

## 树

### 二叉树

每个节点最多有两个叶子节点。

*   [《二叉树》](https://blog.csdn.net/cai2016/article/details/52589952)

### 完全二叉树

*   [《完全二叉树》](https://baike.baidu.com/item/%E5%AE%8C%E5%85%A8%E4%BA%8C%E5%8F%89%E6%A0%91/7773232?fr=aladdin)
    *   叶节点只能出现在最下层和次下层，并且最下面一层的结点都集中在该层最左边的若干位置的二叉树。

### 平衡二叉树

左右两个子树的高度差的绝对值不超过1，并且左右两个子树都是一棵平衡二叉树。

*   [《浅谈数据结构-平衡二叉树》](http://www.cnblogs.com/polly333/p/4798944.html)
*   [《浅谈算法和数据结构: 八 平衡查找树之2-3树》](http://www.cnblogs.com/yangecnu/p/Introduce-2-3-Search-Tree.html)

### 二叉查找树（BST）

二叉查找树（Binary Search Tree），也称有序二叉树（ordered binary tree）,排序二叉树（sorted binary tree）。

*   [《浅谈算法和数据结构: 七 二叉查找树》](http://www.cnblogs.com/yangecnu/p/Introduce-Binary-Search-Tree.html)

### 红黑树

*   [《最容易懂得红黑树》](https://blog.csdn.net/sun_tttt/article/details/65445754)
    *   添加阶段后，左旋或者右旋从而再次达到平衡。
*   [《浅谈算法和数据结构: 九 平衡查找树之红黑树》](http://www.cnblogs.com/yangecnu/p/Introduce-Red-Black-Tree.html)

### B，B+，B\*树

MySQL是基于B+树聚集索引组织表

*   [《B-树，B+树，B\*树详解》](https://blog.csdn.net/aqzwss/article/details/53074186)
*   [《B-树，B+树与B\*树的优缺点比较》](https://blog.csdn.net/bigtree_3721/article/details/73632405)
    *   B+树的叶子节点链表结构相比于 B-树便于扫库，和范围检索。

### LSM 树

LSM（Log-Structured Merge-Trees）和 B+ 树相比，是牺牲了部分读的性能来换取写的性能(通过批量写入)，实现读写之间的平衡。
Hbase、LevelDB、Tair（Long DB）、nessDB 采用 LSM 树的结构。LSM可以快速建立索引。

*   [《LSM树 VS B+树》](https://blog.csdn.net/dbanote/article/details/8897599)
    *   B+ 树读性能好，但由于需要有序结构，当key比较分散时，磁盘寻道频繁，造成写性能较差。
    *   LSM 是将一个大树拆分成N棵小树，先写到内存（无寻道问题，性能高），在内存中构建一颗有序小树（有序树），随着小树越来越大，内存的小树会flush到磁盘上。当读时，由于不知道数据在哪棵小树上，因此必须遍历（二分查找）所有的小树，但在每颗小树内部数据是有序的。
*   [《LSM树（Log-Structured Merge Tree）存储引擎》](https://blog.csdn.net/u014774781/article/details/52105708)
    *   极端的说，基于LSM树实现的HBase的写性能比MySQL高了一个数量级，读性能低了一个数量级。
    *   优化方式：Bloom filter 替代二分查找；compact 小数位大树，提高查询性能。
    *   Hbase 中，内存中达到一定阈值后，整体flush到磁盘上、形成一个文件（B+数），HDFS不支持update操作，所以Hbase做整体flush而不是merge update。flush到磁盘上的小树，定期会合并成一个大树。

## BitSet

经常用于大规模数据的排重检查。

*   [《Java Bitset类》](http://www.runoob.com/java/java-bitset-class.html)
*   [《Java BitSet（位集）》](https://blog.csdn.net/caiandyong/article/details/51581160)

# 常用算法

*   [《常见排序算法及对应的时间复杂度和空间复杂度》](https://blog.csdn.net/gane_cheng/article/details/52652705)

## 排序、查找算法

*   [《常见排序算法及对应的时间复杂度和空间复杂度》](https://blog.csdn.net/gane_cheng/article/details/52652705)

### 选择排序

*   [《Java中的经典算法之选择排序（SelectionSort）》](https://www.cnblogs.com/shen-hua/p/5424059.html)
    *   每一趟从待排序的记录中选出最小的元素，顺序放在已排好序的序列最后，直到全部记录排序完毕。

### 冒泡排序

*   [《冒泡排序的2种写法》](https://blog.csdn.net/shuaizai88/article/details/73250615)
    *   相邻元素前后交换、把最大的排到最后。
    *   时间复杂度 O(n²)

### 插入排序

*   [《排序算法总结之插入排序》](https://www.cnblogs.com/hapjin/p/5517667.html)

### 快速排序

*   [《坐在马桶上看算法：快速排序》](https://blog.csdn.net/afjaklsdflka/article/details/52829030)
    *   一侧比另外一侧都大或小。

### 归并排序

*   [《图解排序算法(四)之归并排序》](http://www.cnblogs.com/chengxiao/p/6194356.html)
    *   分而治之，分成小份排序，在合并(重建一个新空间进行复制)。

### 希尔排序

TODO

### 堆排序

*   [《图解排序算法(三)之堆排序》](https://www.cnblogs.com/chengxiao/p/6129630.html)
    *   排序过程就是构建最大堆的过程，最大堆：每个结点的值都大于或等于其左右孩子结点的值，堆顶元素是最大值。

### 计数排序

*   [《计数排序和桶排序》](https://www.cnblogs.com/suvllian/p/5495780.html)
    *   和桶排序过程比较像，差别在于桶的数量。

### 桶排序

*   [《【啊哈！算法】最快最简单的排序——桶排序》](http://blog.51cto.com/ahalei/1362789)
*   [《排序算法（三）：计数排序与桶排序》](https://blog.csdn.net/sunjinshengli/article/details/70738527)
    *   桶排序将\[0,1)区间划分为n个相同的大小的子区间，这些子区间被称为桶。
    *   每个桶单独进行排序，然后再遍历每个桶。

### 基数排序

按照个位、十位、百位、...依次来排。

*   [《排序算法系列：基数排序》](https://blog.csdn.net/lemon_tree12138/article/details/51695211)
*   [《基数排序》](https://www.cnblogs.com/skywang12345/p/3603669.html)

### 二分查找

*   [《二分查找(java实现)》](https://www.cnblogs.com/coderising/p/5708632.html)
    *   要求待查找的序列有序。
    *   时间复杂度 O(logN)。

*   [《java实现二分查找-两种方式》](https://blog.csdn.net/maoyuanming0806/article/details/78176957)
    *   while + 递归。

### Java 中的排序工具

*   [《Arrays.sort和Collections.sort实现原理解析》](https://blog.csdn.net/u011410529/article/details/56668545?locationnum=6\&fps=1)
    *   Collections.sort算法调用的是合并排序。
    *   Arrays.sort() 采用了2种排序算法 -- 基本类型数据使用快速排序法，对象数组使用归并排序。

## 布隆过滤器

常用于大数据的排重，比如email，url 等。
核心原理：将每条数据通过计算产生一个指纹（一个字节或多个字节，但一定比原始数据要少很多），其中每一位都是通过随机计算获得，在将指纹映射到一个大的按位存储的空间中。注意：会有一定的错误率。
优点：空间和时间效率都很高。
缺点：随着存入的元素数量增加，误算率随之增加。

*   [《布隆过滤器 -- 空间效率很高的数据结构》](https://segmentfault.com/a/1190000002729689)
*   [《大量数据去重：Bitmap和布隆过滤器(Bloom Filter)》](https://blog.csdn.net/zdxiq000/article/details/57626464)
*   [《基于Redis的布隆过滤器的实现》](https://blog.csdn.net/qq_30242609/article/details/71024458)
    *   基于 Redis 的 Bitmap 数据结构。
*   [《网络爬虫：URL去重策略之布隆过滤器(BloomFilter)的使用》](https://blog.csdn.net/lemon_tree12138/article/details/47973715)
    *   使用Java中的 BitSet 类 和 加权和hash算法。

## 字符串比较

### KMP 算法

KMP：Knuth-Morris-Pratt算法（简称KMP）
核心原理是利用一个“部分匹配表”，跳过已经匹配过的元素。

*   [《字符串匹配的KMP算法》](http://www.ruanyifeng.com/blog/2013/05/Knuth%E2%80%93Morris%E2%80%93Pratt_algorithm.html)

## 深度优先、广度优先

*   [《广度优先搜索BFS和深度优先搜索DFS》](https://www.cnblogs.com/0kk470/p/7555033.html)

## 贪心算法

*   [《算法：贪婪算法基础》](https://www.cnblogs.com/MrSaver/p/8641971.html)
*   [《常见算法及问题场景——贪心算法》](https://blog.csdn.net/a345017062/article/details/52443781)

## 回溯算法

*   [《 五大常用算法之四：回溯法》](https://blog.csdn.net/qfikh/article/details/51960331)

## 剪枝算法

*   [《α-β剪枝算法》](https://blog.csdn.net/luningcsdn/article/details/50930276)

## 动态规划

*   [《详解动态规划——邹博讲动态规划》](https://www.cnblogs.com/little-YTMM/p/5372680.html)
*   [《动态规划算法的个人理解》](https://blog.csdn.net/yao_zi_jie/article/details/54580283)

## 朴素贝叶斯

*   [《带你搞懂朴素贝叶斯分类算法》](https://blog.csdn.net/amds123/article/details/70173402)
    *   P(B|A)=P(A|B)P(B)/P(A)

*   [《贝叶斯推断及其互联网应用1》](http://www.ruanyifeng.com/blog/2011/08/bayesian_inference_part_one.html)

*   [《贝叶斯推断及其互联网应用2》](http://www.ruanyifeng.com/blog/2011/08/bayesian_inference_part_two.html)

## 推荐算法

*   [《推荐算法综述》](http://www.infoq.com/cn/articles/recommendation-algorithm-overview-part01)
*   [《TOP 10 开源的推荐系统简介》](https://www.oschina.net/news/51297/top-10-open-source-recommendation-systems)

## 最小生成树算法

*   [《算法导论--最小生成树（Kruskal和Prim算法）》](https://blog.csdn.net/luoshixian099/article/details/51908175)

## 最短路径算法

*   [《Dijkstra算法详解》](https://blog.csdn.net/qq_35644234/article/details/60870719)

# 并发

## Java 并发

*   [Java 并发知识合集](https://github.com/CL0610/Java-concurrency)
*   [JAVA并发知识图谱](https://github.com/CL0610/Java-concurrency/blob/master/Java并发知识图谱.png)

## 多线程

*   [《40个Java多线程问题总结》](https://www.cnblogs.com/xrq730/p/5060921.html)

## 线程安全

*   [《Java并发编程——线程安全及解决机制简介》](https://www.cnblogs.com/zhanht/p/5450325.html)

## 一致性、事务

### 事务 ACID 特性

*   [《数据库事务ACID特性》](https://blog.csdn.net/u012440687/article/details/52116108)

### 事务的隔离级别

*   未提交读：一个事务可以读取另一个未提交的数据，容易出现脏读的情况。

*   读提交：一个事务等另外一个事务提交之后才可以读取数据，但会出现不可重复读的情况（多次读取的数据不一致），读取过程中出现UPDATE操作，会多。（大多数数据库默认级别是RC，比如SQL Server，Oracle），读取的时候不可以修改。

*   可重复读： 同一个事务里确保每次读取的时候，获得的是同样的数据，但不保障原始数据被其他事务更新（幻读），Mysql InnoDB 就是这个级别。

*   序列化：所有事物串行处理（牺牲了效率）

*   [《理解事务的4种隔离级别》](https://blog.csdn.net/qq_33290787/article/details/51924963)

*   [数据库事务的四大特性及事务隔离级别](https://www.cnblogs.com/z-sm/p/7245981.html)

*   [《MySQL的InnoDB的幻读问题 》](http://blog.sina.com.cn/s/blog_499740cb0100ugs7.html)
    *   幻读的例子非常清楚。
    *   通过 SELECT ... FOR UPDATE 解决。

*   [《一篇文章带你读懂MySQL和InnoDB》](https://draveness.me/mysql-innodb)
    *   图解脏读、不可重复读、幻读问题。

### MVCC

*   [《【mysql】关于innodb中MVCC的一些理解》](https://www.cnblogs.com/chenpingzhao/p/5065316.html)
    *   innodb 中 MVCC 用在 Repeatable-Read 隔离级别。
    *   MVCC 会产生幻读问题（更新时异常。）

*   [《轻松理解MYSQL MVCC 实现机制》](https://blog.csdn.net/whoamiyang/article/details/51901888)

    *   通过隐藏版本列来实现 MVCC 控制，一列记录创建时间、一列记录删除时间，这里的时间
    *   每次只操作比当前版本小（或等于）的 行。

## 锁

### Java中的锁和同步类

*   [《Java中的锁分类》](https://www.cnblogs.com/qifengshi/p/6831055.html)
    *   主要包括 synchronized、ReentrantLock、和 ReadWriteLock。

*   [《Java并发之AQS详解》](https://www.cnblogs.com/waterystone/p/4920797.html)

*   [《Java中信号量 Semaphore》](http://cuisuqiang.iteye.com/blog/2020146)
    *   有数量控制
    *   申请用 acquire，申请不要则阻塞；释放用 release。

*   [《java开发中的Mutex vs Semaphore》](https://www.cnblogs.com/davidwang456/p/6094947.html)
    *   简单的说 就是Mutex是排它的，只有一个可以获取到资源， Semaphore也具有排它性，但可以定义多个可以获取的资源的对象。

### 公平锁 & 非公平锁

公平锁的作用就是严格按照线程启动的顺序来执行的，不允许其他线程插队执行的；而非公平锁是允许插队的。

*   [《公平锁与非公平锁》](https://blog.csdn.net/EthanWhite/article/details/55508357)
    *   默认情况下 ReentrantLock 和 synchronized 都是非公平锁。ReentrantLock 可以设置成公平锁。

### 悲观锁

悲观锁如果使用不当（锁的条数过多），会引起服务大面积等待。推荐优先使用乐观锁+重试。

*   [《【MySQL】悲观锁&乐观锁》](https://www.cnblogs.com/zhiqian-ali/p/6200874.html)
    *   乐观锁的方式：版本号+重试方式
    *   悲观锁：通过 select ... for update 进行行锁(不可读、不可写，share 锁可读不可写)。

*   [《Mysql查询语句使用select.. for update导致的数据库死锁分析》](https://www.cnblogs.com/Lawson/p/5008741.html)
    *   mysql的innodb存储引擎实务锁虽然是锁行，但它内部是锁索引的。
    *   锁相同数据的不同索引条件可能会引起死锁。

*   [《Mysql并发时经典常见的死锁原因及解决方法》](https://www.cnblogs.com/zejin2008/p/5262751.html)

### 乐观锁 & CAS

*   [《乐观锁的一种实现方式——CAS》](https://blog.csdn.net/u011514810/article/details/76895723/)
    *   和MySQL乐观锁方式相似，只不过是通过和原值进行比较。

### ABA 问题

由于高并发，在CAS下，更新后可能此A非彼A。通过版本号可以解决，类似于上文Mysql 中提到的的乐观锁。

*   [《Java CAS 和ABA问题》](https://www.cnblogs.com/549294286/p/3766717.html)
*   [《Java 中 ABA问题及避免》](https://blog.csdn.net/li954644351/article/details/50511879)
    *   AtomicStampedReference 和 AtomicStampedReference。

### CopyOnWrite容器

可以对CopyOnWrite容器进行并发的读，而不需要加锁。CopyOnWrite并发容器用于读多写少的并发场景。比如白名单，黑名单，商品类目的访问和更新场景，不适合需要数据强一致性的场景。

*   [《JAVA中写时复制(Copy-On-Write)Map实现》](https://www.cnblogs.com/hapjin/p/4840107.html)
    *   实现读写分离，读取发生在原始数据上，写入发生在副本上。
    *   不用加锁，通过最终一致实现一致性。
*   [《聊聊并发-Java中的Copy-On-Write容器》](https://blog.csdn.net/a494303877/article/details/53404623)

### RingBuffer

*   [《线程安全的无锁RingBuffer的实现【一个读线程，一个写线程】》](http://www.cnblogs.com/l00l/p/4115001.html)

### 可重入锁 & 不可重入锁

*   [《可重入锁和不可重入锁》](https://www.cnblogs.com/dj3839/p/6580765.html)
    *   通过简单代码举例说明可重入锁和不可重入锁。
    *   可重入锁指同一个线程可以再次获得之前已经获得的锁。
    *   可重入锁可以用户避免死锁。
    *   Java中的可重入锁：synchronized 和 java.util.concurrent.locks.ReentrantLock

*   [《ReenTrantLock可重入锁（和synchronized的区别）总结》](https://www.cnblogs.com/baizhanshi/p/7211802.html)
    *   synchronized 使用方便，编译器来加锁，是非公平锁。
    *   ReenTrantLock 使用灵活，锁的公平性可以定制。
    *   相同加锁场景下，推荐使用 synchronized。

### 互斥锁 & 共享锁

互斥锁：同时只能有一个线程获得锁。比如，ReentrantLock 是互斥锁，ReadWriteLock 中的写锁是互斥锁。
共享锁：可以有多个线程同时或的锁。比如，Semaphore、CountDownLatch 是共享锁，ReadWriteLock 中的读锁是共享锁。

*   [《ReadWriteLock场景应用》](https://www.cnblogs.com/liang1101/p/6475555.html)

### 死锁

*   [《“死锁”四个必要条件的合理解释》](https://blog.csdn.net/yunfenglw/article/details/45950305)
    *   互斥、持有、不可剥夺、环形等待。
*   [Java如何查看死锁？](https://blog.csdn.net/u014039577/article/details/52351626)
    *   JConsole 可以识别死锁。
*   [java多线程系列：死锁及检测](https://blog.csdn.net/bohu83/article/details/51135061)
    *   jstack 可以显示死锁。

# 操作系统

## 计算机原理

*   [《操作系统基础知识——操作系统的原理，类型和结构》](https://segmentfault.com/a/1190000003692840)

## CPU

### 多级缓存

典型的 CPU 有三级缓存，距离核心越近，速度越快，空间越小。L1 一般 32k，L2 一般 256k，L3 一般12M。内存速度需要200个 CPU 周期，CPU 缓存需要1个CPU周期。

*   [《从Java视角理解CPU缓存和伪共享》](https://blog.csdn.net/zero__007/article/details/54089730)

## 进程

TODO

## 线程

*   [《线程的生命周期及状态转换详解》](https://blog.csdn.net/asdf_1024/article/details/78978437)

## 协程

*   [《终结python协程----从yield到actor模型的实现》](https://www.thinksaas.cn/group/topic/839375/)
    *   线程的调度是由操作系统负责，协程调度是程序自行负责
    *   与线程相比，协程减少了无谓的操作系统切换.
    *   实际上当遇到IO操作时做切换才更有意义，（因为IO操作不用占用CPU），如果没遇到IO操作，按照时间片切换.

## Linux

*   [《Linux 命令大全》](http://www.runoob.com/linux/linux-command-manual.html)

# 设计模式

## 设计模式的六大原则

*   [《设计模式的六大原则》](https://blog.csdn.net/q291611265/article/details/48465113)
    *   开闭原则：对扩展开放,对修改关闭，多使用抽象类和接口。
    *   里氏替换原则：基类可以被子类替换，使用抽象类继承,不使用具体类继承。
    *   依赖倒转原则：要依赖于抽象,不要依赖于具体，针对接口编程,不针对实现编程。
    *   接口隔离原则：使用多个隔离的接口,比使用单个接口好，建立最小的接口。
    *   迪米特法则：一个软件实体应当尽可能少地与其他实体发生相互作用，通过中间类建立联系。
    *   合成复用原则：尽量使用合成/聚合,而不是使用继承。

## 23种常见设计模式

*   [《设计模式》](http://www.runoob.com/design-pattern/design-pattern-tutorial.html)
*   [《23种设计模式全解析》](https://www.cnblogs.com/susanws/p/5510229.html)
*   [《设计模式类图与示例》](https://github.com/ToryZhou/design-pattern)

## 应用场景

*   [《细数JDK里的设计模式》](https://www.cnblogs.com/winkey4986/p/5148953.html)
    *   结构型模式：
        *   适配器：用来把一个接口转化成另一个接口，如 java.util.Arrays#asList()。
        *   桥接模式：这个模式将抽象和抽象操作的实现进行了解耦，这样使得抽象和实现可以独立地变化，如JDBC；
        *   组合模式：使得客户端看来单个对象和对象的组合是同等的。换句话说，某个类型的方法同时也接受自身类型作为参数，如 Map.putAll，List.addAll、Set.addAll。
        *   装饰者模式：动态的给一个对象附加额外的功能，这也是子类的一种替代方式，如 java.util.Collections#checkedList|Map|Set|SortedSet|SortedMap。
        *   享元模式：使用缓存来加速大量小对象的访问时间，如 valueOf(int)。
        *   代理模式：代理模式是用一个简单的对象来代替一个复杂的或者创建耗时的对象，如 java.lang.reflect.Proxy
    *   创建模式:
        *   抽象工厂模式：抽象工厂模式提供了一个协议来生成一系列的相关或者独立的对象，而不用指定具体对象的类型，如 java.util.Calendar#getInstance()。
        *   建造模式(Builder)：定义了一个新的类来构建另一个类的实例，以简化复杂对象的创建，如：java.lang.StringBuilder#append()。
        *   工厂方法：就是 **一个返回**具体对象的方法，而不是多个，如 java.lang.Object#toString()、java.lang.Class#newInstance()。
        *   原型模式：使得类的实例能够生成自身的拷贝、如：java.lang.Object#clone()。
        *   单例模式：全局只有一个实例，如 java.lang.Runtime#getRuntime()。
    *   行为模式：
        *   责任链模式：通过把请求从一个对象传递到链条中下一个对象的方式，直到请求被处理完毕，以实现对象间的解耦。如 javax.servlet.Filter#doFilter()。
        *   命令模式：将操作封装到对象内，以便存储，传递和返回，如：java.lang.Runnable。
        *   解释器模式：定义了一个语言的语法，然后解析相应语法的语句，如，java.text.Format，java.text.Normalizer。
        *   迭代器模式：提供一个一致的方法来顺序访问集合中的对象，如 java.util.Iterator。
        *   中介者模式：通过使用一个中间对象来进行消息分发以及减少类之间的直接依赖，java.lang.reflect.Method#invoke()。
        *   空对象模式：如 java.util.Collections#emptyList()。
        *   观察者模式：它使得一个对象可以灵活的将消息发送给感兴趣的对象，如 java.util.EventListener。
        *   模板方法模式：让子类可以重写方法的一部分，而不是整个重写，如 java.util.Collections#sort()。

*   [《Spring-涉及到的设计模式汇总》](https://www.cnblogs.com/hwaggLee/p/4510687.html)

*   [《Mybatis使用的设计模式》](https://blog.csdn.net/u012387062/article/details/54719114)

## 单例模式

*   [《单例模式的三种实现 以及各自的优缺点》](https://blog.csdn.net/YECrazy/article/details/79481964)
*   [《单例模式－－反射－－防止序列化破坏单例模式》](https://www.cnblogs.com/ttylinux/p/6498822.html)
    *   使用枚举类型。

## 责任链模式

TODO

## MVC

*   [《MVC 模式》](http://www.runoob.com/design-pattern/mvc-pattern.html)
    *   模型(model)－视图(view)－控制器(controller)

## IOC

*   [《理解 IOC》](https://www.zhihu.com/question/23277575)
*   [《IOC 的理解与解释》](https://www.cnblogs.com/NancyStartOnce/p/6813162.html)
    *   正向控制：传统通过new的方式。反向控制，通过容器注入对象。
    *   作用：用于模块解耦。
    *   DI：Dependency Injection，即依赖注入，只关心资源使用，不关心资源来源。

## AOP

*   [《轻松理解AOP(面向切面编程)》](https://blog.csdn.net/yanquan345/article/details/19760027)
*   [《Spring AOP详解》](https://www.cnblogs.com/hongwz/p/5764917.html)
*   [《Spring AOP的实现原理》](http://www.importnew.com/24305.html)
    *   Spring AOP使用的动态代理，主要有两种方式：JDK动态代理和CGLIB动态代理。
*   [《Spring AOP 实现原理与 CGLIB 应用》](https://www.ibm.com/developerworks/cn/java/j-lo-springaopcglib/)
    *   Spring AOP 框架对 AOP 代理类的处理原则是：如果目标对象的实现类实现了接口，Spring AOP 将会采用 JDK 动态代理来生成 AOP 代理类；如果目标对象的实现类没有实现接口，Spring AOP 将会采用 CGLIB 来生成 AOP 代理类

## UML

*   [《UML教程》](https://www.w3cschool.cn/uml_tutorial/)

## 微服务思想

*   [《微服务架构设计》](https://www.cnblogs.com/wintersun/p/6219259.html)
*   [《微服务架构技术栈选型手册》](http://www.infoq.com/cn/articles/micro-service-technology-stack)

### 康威定律

*   [《微服务架构的理论基础 - 康威定律》](https://yq.aliyun.com/articles/8611)
    *   定律一：组织沟通方式会通过系统设计表达出来，就是说架构的布局和组织结构会有相似。
    *   定律二：时间再多一件事情也不可能做的完美，但总有时间做完一件事情。一口气吃不成胖子，先搞定能搞定的。
    *   定律三：线型系统和线型组织架构间有潜在的异质同态特性。种瓜得瓜，做独立自治的子系统减少沟通成本。
    *   定律四：大的系统组织总是比小系统更倾向于分解。合久必分，分而治之。

*   [《微服务架构核⼼20讲》](https://static.geekbang.org/PDF-%E4%BF%AE%E6%94%B9%E7%89%88-%E6%9E%81%E5%AE%A2%E6%97%B6%E9%97%B4-%E5%9B%BE%E7%89%87-%E6%9D%A8%E6%B3%A2-%E5%BE%AE%E6%9C%8D%E5%8A%A1%E6%9E%B6%E6%9E%84.pdf)

# 运维 & 统计 & 技术支持

## 常规监控

*   [《腾讯业务系统监控的修炼之路》](https://blog.csdn.net/enweitech/article/details/77849205)
    *   监控的方式：主动、被动、旁路(比如舆情监控)
    *   监控类型： 基础监控、服务端监控、客户端监控、
        监控、用户端监控
    *   监控的目标：全、块、准
    *   核心指标：请求量、成功率、耗时

*   [《开源还是商用？十大云运维监控工具横评》](https://www.oschina.net/news/67525/monitoring-tools)
    *   Zabbix、Nagios、Ganglia、Zenoss、Open-falcon、监控宝、 360网站服务监控、阿里云监控、百度云观测、小蜜蜂网站监测等。

*   [《监控报警系统搭建及二次开发经验》](http://developer.51cto.com/art/201612/525373.htm)

**命令行监控工具**

*   [《常用命令行监控工具》](https://coderxing.gitbooks.io/architecture-evolution/di-er-pian-ff1a-feng-kuang-yuan-shi-ren/44-an-quan-yu-yun-wei/445-fu-wu-qi-zhuang-tai-jian-ce/4451-ming-ling-xing-gong-ju.html)
    *   top、sar、tsar、nload

*   [《20个命令行工具监控 Linux 系统性能》](http://blog.jobbole.com/96846/)

*   [《JVM性能调优监控工具jps、jstack、jmap、jhat、jstat、hprof使用详解》](https://my.oschina.net/feichexia/blog/196575)

## APM

APM —  Application Performance Management

*   [《Dapper，大规模分布式系统的跟踪系统》](http://bigbully.github.io/Dapper-translation/)

*   [CNCF OpenTracing](http://opentracing.io)，[中文版](https://github.com/opentracing-contrib/opentracing-specification-zh)

*   主要开源软件，按字母排序
    *   [Apache SkyWalking](https://github.com/apache/incubator-skywalking)
    *   [CAT](https://github.com/dianping/cat)
    *   [CNCF jaeger](https://github.com/jaegertracing/jaeger)
    *   [Pinpoint](https://github.com/naver/pinpoint)
    *   [Zipkin](https://github.com/openzipkin/zipkin)

*   [《开源APM技术选型与实战》](http://www.infoq.com/cn/articles/apm-Pinpoint-practice)
    *   主要基于 Google的Dapper（大规模分布式系统的跟踪系统） 思想。

## 统计分析

*   [《流量统计的基础：埋点》](https://zhuanlan.zhihu.com/p/25195217)
    *   常用指标：访问与访客、停留时长、跳出率、退出率、转化率、参与度

*   [《APP埋点常用的统计工具、埋点目标和埋点内容》](http://www.25xt.com/company/17066.html)
    *   第三方统计：友盟、百度移动、魔方、App Annie、talking data、神策数据等。

*   [《美团点评前端无痕埋点实践》](https://tech.meituan.com/mt_mobile_analytics_practice.html)
    *   所谓无痕、即通过可视化工具配置采集节点，在前端自动解析配置并上报埋点数据，而非硬编码。

## 持续集成(CI/CD)

*   [《持续集成是什么？》](http://www.ruanyifeng.com/blog/2015/09/continuous-integration.html)
*   [《8个流行的持续集成工具》](http://www.51testing.com/html/74/n-3723774.html)

### Jenkins

*   [《使用Jenkins进行持续集成》](https://www.liaoxuefeng.com/article/001463233913442cdb2d1bd1b1b42e3b0b29eb1ba736c5e000)

### 环境分离

开发、测试、生成环境分离。

*   [《开发环境、生产环境、测试环境的基本理解和区》](https://my.oschina.net/sancuo/blog/214904)

## 自动化运维

### Ansible

*   [《Ansible中文权威指南》](http://www.ansible.com.cn/)
*   [《Ansible基础配置和企业级项目实用案例》](https://www.cnblogs.com/heiye123/articles/7855890.html)

### puppet

*   [《自动化运维工具——puppet详解》](https://www.cnblogs.com/keerya/p/8040071.html)

### chef

*   [《Chef 的安装与使用》](https://www.ibm.com/developerworks/cn/cloud/library/1407_caomd_chef/)

## 测试

### TDD 理论

*   [《深度解读 - TDD（测试驱动开发）》](https://www.jianshu.com/p/62f16cd4fef3)
    *   基于测试用例编码功能代码，XP（Extreme Programming）的核心实践.
    *   好处：一次关注一个点，降低思维负担；迎接需求变化或改善代码的设计；提前澄清需求；快速反馈；

### 单元测试

*   [《Java单元测试之JUnit篇》](https://www.cnblogs.com/happyzm/p/6482886.html)
*   [《JUnit 4 与 TestNG 对比》](https://blog.csdn.net/hotdust/article/details/53406086)
    *   TestNG 覆盖 JUnit 功能，适用于更复杂的场景。
*   [《单元测试主要的测试功能点》](https://blog.csdn.net/wqetfg/article/details/50900512)
    *   模块接口测试、局部数据结构测试、路径测试 、错误处理测试、边界条件测试 。

### 压力测试

*   [《Apache ab 测试使用指南》](https://blog.csdn.net/blueheart20/article/details/52170790)
*   [《大型网站压力测试及优化方案》](https://www.cnblogs.com/binyue/p/6141088.html)
*   [《10大主流压力/负载/性能测试工具推荐》](http://news.chinabyte.com/466/14126966.shtml)
*   [《真实流量压测工具 tcpcopy应用浅析》](http://quentinxxz.iteye.com/blog/2249799)
*   [《nGrinder 简易使用教程》](https://www.cnblogs.com/jwentest/p/7136727.html)

### 全链路压测

*   [《京东618：升级全链路压测方案，打造军演机器人ForceBot》](http://www.infoq.com/cn/articles/jd-618-upgrade-full-link-voltage-test-program-forcebot)
*   [《饿了么全链路压测的探索与实践》](https://zhuanlan.zhihu.com/p/30306892)
*   [《四大语言，八大框架｜滴滴全链路压测解决之道》](https://zhuanlan.zhihu.com/p/28355759)
*   [《全链路压测经验》](https://www.jianshu.com/p/27060fd61f72)

### A/B 、灰度、蓝绿测试

*   [《技术干货 | AB 测试和灰度发布探索及实践》](https://testerhome.com/topics/11165)

*   [《nginx 根据IP 进行灰度发布》](http://blog.51cto.com/purplegrape/1403123)

*   [《蓝绿部署、A/B 测试以及灰度发布》](https://www.v2ex.com/t/344341)

## 虚拟化

*   [《VPS的三种虚拟技术OpenVZ、Xen、KVM优缺点比较》](https://blog.csdn.net/enweitech/article/details/52910082)

### KVM

*   [《KVM详解，太详细太深入了，经典》](http://blog.chinaunix.net/uid-20201831-id-5775661.html)
*   [《【图文】KVM 虚拟机安装详解》](https://www.coderxing.com/kvm-install.html)

### Xen

*   [《Xen虚拟化基本原理详解》](https://www.cnblogs.com/sddai/p/5931201.html)

### OpenVZ

*   [《开源Linux容器 OpenVZ 快速上手指南》](https://blog.csdn.net/longerzone/article/details/44829255)

## 容器技术

### Docker

*   [《几张图帮你理解 docker 基本原理及快速入门》](https://www.cnblogs.com/SzeCheng/p/6822905.html)
*   [《Docker 核心技术与实现原理》](https://draveness.me/docker)
*   [《Docker 教程》](http://www.runoob.com/docker/docker-tutorial.html)

## 云技术

### OpenStack

*   [《OpenStack构架知识梳理》](https://www.cnblogs.com/klb561/p/8660264.html)

## DevOps

*   [《一分钟告诉你究竟DevOps是什么鬼？》](https://www.cnblogs.com/jetzhang/p/6068773.html)
*   [《DevOps详解》](http://www.infoq.com/cn/articles/detail-analysis-of-devops)

## 文档管理

*   [Confluence-收费文档管理系统](http://www.confluence.cn/)
*   GitLab?
*   Wiki

# 中间件

## Web Server

### Nginx

*   [《Ngnix的基本学习-多进程和Apache的比较》](https://blog.csdn.net/qq_25797077/article/details/52200722)
    *   Nginx 通过异步非阻塞的事件处理机制实现高并发。Apache 每个请求独占一个线程，非常消耗系统资源。
    *   事件驱动适合于IO密集型服务(Nginx)，多进程或线程适合于CPU密集型服务(Apache)，所以Nginx适合做反向代理，而非web服务器使用。

*   [《nginx与Apache的对比以及优缺点》](https://www.cnblogs.com/cunkouzh/p/5410154.html)
    *   nginx只适合静态和反向代理，不适合处理动态请求。

### OpenResty

*   [官方网站](http://openresty.org/cn/)
*   [《浅谈 OpenResty》](http://www.linkedkeeper.com/detail/blog.action?bid=1034)
    *   通过 Lua 模块可以在Nginx上进行开发。
*   [agentzh 的 Nginx 教程](https://openresty.org/download/agentzh-nginx-tutorials-zhcn.html)

### Tengine

*   [官方网站](http://tengine.taobao.org/)

### Apache Httpd

*   [官方网站](http://httpd.apache.org/)

### Tomcat

#### 架构原理

*   [《TOMCAT原理详解及请求过程》](https://www.cnblogs.com/hggen/p/6264475.html)

*   [《Tomcat服务器原理详解》](https://www.cnblogs.com/crazylqy/p/4706223.html)

*   [《Tomcat 系统架构与设计模式,第 1 部分: 工作原理》](https://www.ibm.com/developerworks/cn/java/j-lo-tomcat1/)

*   [《四张图带你了解Tomcat系统架构》](https://blog.csdn.net/xlgen157387/article/details/79006434)

*   [《JBoss vs. Tomcat: Choosing A Java Application Server》](https://www.futurehosting.com/blog/jboss-vs-tomcat-choosing-a-java-application-server/)
    *   Tomcat 是轻量级的 Serverlet 容器，没有实现全部 JEE 特性（比如持久化和事务处理），但可以通过其他组件代替，比如Spring。
    *   Jboss 实现全部了JEE特性，软件开源免费、文档收费。

#### 调优方案

*   [《Tomcat 调优方案》](https://www.cnblogs.com/sunfenqing/p/7339058.html)
    *   启动NIO模式（或者APR）；调整线程池；禁用AJP连接器（Nginx+tomcat的架构，不需要AJP）；

*   [《tomcat http协议与ajp协议》](http://blog.chinaunix.net/uid-20662363-id-3012760.html)

*   [《AJP与HTTP比较和分析》](http://dmouse.iteye.com/blog/1354527)
    *   AJP 协议（8009端口）用于降低和前端Server（如Apache，而且需要支持AJP协议）的连接数(前端)，通过长连接提高性能。
    *   并发高时，AJP协议优于HTTP协议。

### Jetty

*   [《Jetty 的工作原理以及与 Tomcat 的比较》](https://www.ibm.com/developerworks/cn/java/j-lo-jetty/)
*   [《jetty和tomcat优势比较》](https://blog.csdn.net/doutao6677/article/details/51957288)
    *   架构比较:Jetty的架构比Tomcat的更为简单。
    *   性能比较：Jetty和Tomcat性能方面差异不大，Jetty默认采用NIO结束在处理I/O请求上更占优势，Tomcat默认采用BIO处理I/O请求，Tomcat适合处理少数非常繁忙的链接，处理静态资源时性能较差。
    *   其他方面：Jetty的应用更加快速，修改简单，对新的Servlet规范的支持较好;Tomcat 对JEE和Servlet 支持更加全面。

## 缓存

*   [《缓存失效策略（FIFO 、LRU、LFU三种算法的区别）》](https://blog.csdn.net/clementad/article/details/48229243)

### 本地缓存

*   [《HashMap本地缓存》](https://coderxing.gitbooks.io/architecture-evolution/di-er-pian-ff1a-feng-kuang-yuan-shi-ren/42-xing-neng-zhi-ben-di-huan-cun/421-ying-yong-ceng-ben-di-huan-cun/4211.html)

*   [《EhCache本地缓存》](https://coderxing.gitbooks.io/architecture-evolution/di-er-pian-ff1a-feng-kuang-yuan-shi-ren/42-xing-neng-zhi-ben-di-huan-cun/421-ying-yong-ceng-ben-di-huan-cun/4212-ehcache.html)
    *   堆内、堆外、磁盘三级缓存。
    *   可按照缓存空间容量进行设置。
    *   按照时间、次数等过期策略。

*   [《Guava Cache》](https://coderxing.gitbooks.io/architecture-evolution/di-er-pian-ff1a-feng-kuang-yuan-shi-ren/42-xing-neng-zhi-ben-di-huan-cun/421-ying-yong-ceng-ben-di-huan-cun/4213-guava-cache.html)
    *   简单轻量、无堆外、磁盘缓存。

*   [《Nginx本地缓存》](https://coderxing.gitbooks.io/architecture-evolution/di-er-pian-ff1a-feng-kuang-yuan-shi-ren/42-xing-neng-zhi-ben-di-huan-cun/422-fu-wu-duan-ben-di-huan-cun/nginx-ben-di-huan-cun.html)

*   [《Pagespeed—懒人工具，服务器端加速》](https://coderxing.gitbooks.io/architecture-evolution/di-er-pian-ff1a-feng-kuang-yuan-shi-ren/42-xing-neng-zhi-ben-di-huan-cun/422-fu-wu-duan-ben-di-huan-cun/4222-pagespeed.html)

## 客户端缓存

*   [《浏览器端缓存》](https://coderxing.gitbooks.io/architecture-evolution/di-er-pian-ff1a-feng-kuang-yuan-shi-ren/42-xing-neng-zhi-ben-di-huan-cun/423-ke-hu-duan-huan-cun.html)
    *   主要是利用 Cache-Control 参数。

*   [《H5 和移动端 WebView 缓存机制解析与实战》](https://mp.weixin.qq.com/s/qHm_dJBhVbv0pJs8Crp77w)

## 服务端缓存

### Web缓存

*   [nuster](https://github.com/jiangwenyuan/nuster) - nuster cache
*   [varnish](https://github.com/varnishcache/varnish-cache) - varnish cache
*   [squid](https://github.com/squid-cache/squid) - squid cache

### Memcached

*   [《Memcached 教程》](http://www.runoob.com/Memcached/Memcached-tutorial.html)

*   [《深入理解Memcached原理》](https://blog.csdn.net/chenleixing/article/details/47035453)
    *   采用多路复用技术提高并发性。
    *   slab分配算法： memcached给Slab分配内存空间，默认是1MB。分配给Slab之后 把slab的切分成大小相同的chunk，Chunk是用于缓存记录的内存空间，Chunk 的大小默认按照1.25倍的速度递增。好处是不会频繁申请内存，提高IO效率，坏处是会有一定的内存浪费。

*   [《Memcached软件工作原理》](https://www.jianshu.com/p/36e5cd400580)

*   [《Memcache技术分享：介绍、使用、存储、算法、优化、命中率》](http://zhihuzeye.com/archives/2361)

*   [《memcache 中 add 、 set 、replace 的区别》](https://blog.csdn.net/liu251890347/article/details/37690045)
    *   区别在于当key存在还是不存在时，返回值是true和false的。

*   [**《memcached全面剖析》**](https://pan.baidu.com/s/1qX00Lti?errno=0\&errmsg=Auth%20Login%20Sucess&\&bduss=\&ssnerror=0\&traceid=)

### Redis

*   [《Redis 教程》](http://www.runoob.com/redis/redis-tutorial.html)

*   [《redis底层原理》](https://blog.csdn.net/wcf373722432/article/details/78678504)
    *   使用 ziplist 存储链表，ziplist是一种压缩链表，它的好处是更能节省内存空间，因为它所存储的内容都是在连续的内存区域当中的。
    *   使用 skiplist(跳跃表)来存储有序集合对象、查找上先从高Level查起、时间复杂度和红黑树相当，实现容易，无锁、并发性好。

*   [《Redis持久化方式》](http://doc.redisfans.com/topic/persistence.html)
    *   RDB方式：定期备份快照，常用于灾难恢复。优点：通过fork出的进程进行备份，不影响主进程、RDB 在恢复大数据集时的速度比 AOF 的恢复速度要快。缺点：会丢数据。
    *   AOF方式：保存操作日志方式。优点：恢复时数据丢失少，缺点：文件大，回复慢。
    *   也可以两者结合使用。

*   [《分布式缓存--序列3--原子操作与CAS乐观锁》](https://blog.csdn.net/chunlongyu/article/details/53346436)

#### 架构

*   [《Redis单线程架构》](https://blog.csdn.net/sunhuiliang85/article/details/73656830)

#### 回收策略

*   [《redis的回收策略》](https://blog.csdn.net/qq_29108585/article/details/63251491)

### Tair

*   [官方网站](https://github.com/alibaba/tair)
*   [《Tair和Redis的对比》](http://blog.csdn.net/farphone/article/details/53522383)
*   特点：可以配置备份节点数目，通过异步同步到备份节点
*   一致性Hash算法。
*   架构：和Hadoop 的设计思想类似，有Configserver，DataServer，Configserver 通过心跳来检测，Configserver也有主备关系。

几种存储引擎:

*   MDB，完全内存性，可以用来存储Session等数据。
*   Rdb（类似于Redis），轻量化，去除了aof之类的操作，支持Restfull操作
*   LDB（LevelDB存储引擎），持久化存储，LDB 作为rdb的持久化，google实现，比较高效，理论基础是LSM(Log-Structured-Merge Tree)算法，现在内存中修改数据，达到一定量时（和内存汇总的旧数据一同写入磁盘）再写入磁盘，存储更加高效，县比喻Hash算法。
*   Tair采用共享内存来存储数据，如果服务挂掉（非服务器），重启服务之后，数据亦然还在。

## 消息队列

*   [《消息队列-推/拉模式学习 & ActiveMQ及JMS学习》](https://www.cnblogs.com/charlesblc/p/6045238.html)
    *   RabbitMQ 消费者默认是推模式（也支持拉模式）。
    *   Kafka 默认是拉模式。
    *   Push方式：优点是可以尽可能快地将消息发送给消费者，缺点是如果消费者处理能力跟不上，消费者的缓冲区可能会溢出。
    *   Pull方式：优点是消费端可以按处理能力进行拉去，缺点是会增加消息延迟。

*   [《Kafka、RabbitMQ、RocketMQ等消息中间件的对比 —— 消息发送性能和区别》](https://blog.csdn.net/yunfeng482/article/details/72856762)

### 消息总线

消息总线相当于在消息队列之上做了一层封装，统一入口，统一管控、简化接入成本。

*   [《消息总线VS消息队列》](https://blog.csdn.net/yanghua_kobe/article/details/43877281)

### 消息的顺序

*   [《如何保证消费者接收消息的顺序》](https://www.cnblogs.com/cjsblog/p/8267892.html)

### RabbitMQ

支持事务，推拉模式都是支持、适合需要可靠性消息传输的场景。

*   [《RabbitMQ的应用场景以及基本原理介绍》](https://blog.csdn.net/whoamiyang/article/details/54954780)
*   [《消息队列之 RabbitMQ》](https://www.jianshu.com/p/79ca08116d57)
*   [《RabbitMQ之消息确认机制（事务+Confirm）》](https://blog.csdn.net/u013256816/article/details/55515234)

### RocketMQ

Java实现，推拉模式都是支持，吞吐量逊于Kafka。可以保证消息顺序。

*   [《RocketMQ 实战之快速入门》](https://www.jianshu.com/p/824066d70da8)
*   [《RocketMQ 源码解析》](http://www.iocoder.cn/categories/RocketMQ/?vip\&architect-awesome)

### ActiveMQ

纯Java实现，兼容JMS，可以内嵌于Java应用中。

*   [《ActiveMQ消息队列介绍》](https://www.cnblogs.com/wintersun/p/3962302.html)

### Kafka

高吞吐量、采用拉模式。适合高IO场景，比如日志同步。

*   [官方网站](http://kafka.apache.org/)
*   [《各消息队列对比，Kafka深度解析，众人推荐，精彩好文！》](https://blog.csdn.net/allthesametome/article/details/47362451)
*   [《Kafka分区机制介绍与示例》](http://lxw1234.com/archives/2015/10/538.htm)

### Redis 消息推送

生产者、消费者模式完全是客户端行为，list 和 拉模式实现，阻塞等待采用 blpop 指令。

*   [《Redis学习笔记之十：Redis用作消息队列》](https://blog.csdn.net/qq_34212276/article/details/78455004)

### ZeroMQ

TODO

## 定时调度

### 单机定时调度

*   [《linux定时任务cron配置》](https://www.cnblogs.com/shuaiqing/p/7742382.html)

*   [《Linux cron运行原理》](https://my.oschina.net/daquan/blog/483305)
    *   fork 进程 + sleep 轮询

*   [《Quartz使用总结》](https://www.cnblogs.com/drift-ice/p/3817269.html)

*   [《Quartz源码解析 ---- 触发器按时启动原理》](https://blog.csdn.net/wenniuwuren/article/details/42082981/)

*   [《quartz原理揭秘和源码解读》](https://www.jianshu.com/p/bab8e4e32952)
    *   定时调度在 QuartzSchedulerThread 代码中，while()无限循环，每次循环取出时间将到的trigger，触发对应的job，直到调度器线程被关闭。

### 分布式定时调度

*   [《这些优秀的国产分布式任务调度系统，你用过几个？》](https://blog.csdn.net/qq_16216221/article/details/70314337)
    *   opencron、LTS、XXL-JOB、Elastic-Job、Uncode-Schedule、Antares

*   [《Quartz任务调度的基本实现原理》](https://www.cnblogs.com/zhenyuyaodidiao/p/4755649.html)
    *   Quartz集群中，独立的Quartz节点并不与另一其的节点或是管理节点通信，而是通过相同的数据库表来感知到另一Quartz应用的

*   [《Elastic-Job-Lite 源码解析》](http://www.iocoder.cn/categories/Elastic-Job-Lite/?vip\&architect-awesome)

*   [《Elastic-Job-Cloud 源码解析》](http://www.iocoder.cn/categories/Elastic-Job-Cloud/?vip\&architect-awesome)

## RPC

*   [《从零开始实现RPC框架 - RPC原理及实现》](https://blog.csdn.net/top_code/article/details/54615853)
    *   核心角色：Server: 暴露服务的服务提供方、Client: 调用远程服务的服务消费方、Registry: 服务注册与发现的注册中心。

*   [《分布式RPC框架性能大比拼 dubbo、motan、rpcx、gRPC、thrift的性能比较》](https://blog.csdn.net/testcs_dn/article/details/78050590)

### Dubbo

*   [官方网站](http://dubbo.apache.org/)
*   [dubbo实现原理简单介绍](https://www.cnblogs.com/steven520213/p/7606598.html)

\*\* SPI \*\*
TODO

### Thrift

*   [官方网站](http://thrift.apache.org/)
*   [《Thrift RPC详解》](https://blog.csdn.net/kesonyk/article/details/50924489)
    *   支持多语言，通过中间语言定义接口。

### gRPC

服务端可以认证加密，在外网环境下，可以保证数据安全。

*   [官方网站](https://grpc.io/)
*   [《你应该知道的RPC原理》](https://www.cnblogs.com/LBSer/p/4853234.html)

## 数据库中间件

### Sharding Jdbc

*   [官网](http://shardingjdbc.io/)
*   [源码解析](http://www.iocoder.cn/categories/Sharding-JDBC/?vip\&architect-awesome)

## 日志系统

### 日志搜集

*   [《从零开始搭建一个ELKB日志收集系统》](http://cjting.me/misc/build-log-system-with-elkb/)
*   [《用ELK搭建简单的日志收集分析系统》](https://blog.csdn.net/lzw_2006/article/details/51280058)
*   [《日志收集系统-探究》](https://www.cnblogs.com/beginmind/p/6058194.html)

## 配置中心

*   [Apollo - 携程开源的配置中心应用](https://github.com/ctripcorp/apollo)
    *   Spring Boot 和 Spring Cloud
    *   支持推、拉模式更新配置
    *   支持多种语言

*   [《基于zookeeper实现统一配置管理》](https://blog.csdn.net/u011320740/article/details/78742625)

*   [《 Spring Cloud Config 分布式配置中心使用教程》](https://www.cnblogs.com/shamo89/p/8016908.html)

servlet 3.0 异步特性可用于配置中心的客户端

*   [《servlet3.0 新特性——异步处理》](https://www.cnblogs.com/dogdogwang/p/7151866.html)

## API 网关

主要职责：请求转发、安全认证、协议转换、容灾。

*   [《API网关那些儿》](http://yunlzheng.github.io/2017/03/14/the-things-about-api-gateway/)

*   [《谈API网关的背景、架构以及落地方案》](http://www.infoq.com/cn/news/2016/07/API-background-architecture-floo)

*   [《使用Zuul构建API Gateway》](https://blog.csdn.net/zhanglh046/article/details/78651993)

*   [《Spring Cloud Gateway 源码解析》](http://www.iocoder.cn/categories/Spring-Cloud-Gateway/?vip\&architect-awesome)

*   [《HTTP API网关选择之一Kong介绍》](https://mp.weixin.qq.com/s/LIq2CiXJQmmjBC0yvYLY5A)

# 网络

## 协议

### OSI 七层协议

*   [《OSI七层协议模型、TCP/IP四层模型学习笔记》](https://www.cnblogs.com/Robin-YB/p/6668762.html)

### TCP/IP

*   [《深入浅出 TCP/IP 协议》](https://www.cnblogs.com/onepixel/p/7092302.html)
*   [《TCP协议中的三次握手和四次挥手》](https://blog.csdn.net/whuslei/article/details/6667471/)

### HTTP

*   [《http协议详解(超详细)》](https://www.cnblogs.com/wangning528/p/6388464.html)

### HTTP2.0

*   [《HTTP 2.0 原理详细分析》](https://blog.csdn.net/zhuyiquan/article/details/69257126)
*   [《HTTP2.0的基本单位为二进制帧》](https://blog.csdn.net/u012657197/article/details/77877840)
    *   利用二进制帧负责传输。
    *   多路复用。

### HTTPS

*   [《https原理通俗了解》](https://www.cnblogs.com/zhangshitong/p/6478721.html)
    *   使用非对称加密协商加密算法
    *   使用对称加密方式传输数据
    *   使用第三方机构签发的证书，来加密公钥，用于公钥的安全传输、防止被中间人串改。

*   [《八大免费SSL证书-给你的网站免费添加Https安全加密》](https://blog.csdn.net/enweitech/article/details/53213862)

## 网络模型

*   [《web优化必须了解的原理之I/o的五种模型和web的三种工作模式》](http://blog.51cto.com/litaotao/1289790)
    *   五种I/O模型：阻塞I/O，非阻塞I/O，I/O复用、事件(信号)驱动I/O、异步I/O，前四种I/O属于同步操作，I/O的第一阶段不同、第二阶段相同，最后的一种则属于异步操作。
    *   三种 Web Server 工作方式：Prefork(多进程)、Worker方式(线程方式)、Event方式。

*   [《select、poll、epoll之间的区别总结》](http://www.cnblogs.com/Anker/p/3265058.html)
    *   select，poll，epoll本质上都是同步I/O，因为他们都需要在读写事件就绪后自己负责进行读写，也就是说这个读写过程是阻塞的。
    *   select 有打开文件描述符数量限制，默认1024（2048 for x64），100万并发，就要用1000个进程、切换开销大；poll采用链表结构，没有数量限制。
    *   select，poll “醒着”的时候要遍历整个fd集合，而epoll在“醒着”的时候只要判断一下就绪链表是否为空就行了，通过回调机制节省大量CPU时间；select，poll每次调用都要把fd集合从用户态往内核态拷贝一次，而epoll只要一次拷贝。
    *   poll会随着并发增加，性能逐渐下降，epoll采用红黑树结构，性能稳定，不会随着连接数增加而降低。

*   [《select，poll，epoll比较  》](http://xingyunbaijunwei.blog.163.com/blog/static/76538067201241685556302/)
    *   在连接数少并且连接都十分活跃的情况下，select和poll的性能可能比epoll好，毕竟epoll的通知机制需要很多函数回调。

*   [《深入理解Java NIO》](https://www.cnblogs.com/geason/p/5774096.html)
    *   NIO 是一种同步非阻塞的 IO 模型。同步是指线程不断轮询 IO 事件是否就绪，非阻塞是指线程在等待 IO 的时候，可以同时做其他任务

*   [《BIO与NIO、AIO的区别》](https://blog.csdn.net/skiof007/article/details/52873421)

*   [《两种高效的服务器设计模型：Reactor和Proactor模型》](https://blog.csdn.net/u013074465/article/details/46276967)

### Epoll

*   [《epoll使用详解（精髓）》](https://www.cnblogs.com/fnlingnzb-learner/p/5835573.html)

### Java NIO

*   [《深入理解Java NIO》](https://www.cnblogs.com/geason/p/5774096.html)
*   [《Java NIO编写Socket服务器的一个例子》](https://blog.csdn.net/xidianliuy/article/details/51612676)

### kqueue

*   [《kqueue用法简介》](http://www.cnblogs.com/luminocean/p/5631336.html)

## 连接和短连接

*   [《TCP/IP系列——长连接与短连接的区别》](https://www.cnblogs.com/pangguoping/p/5571422.html)

## 框架

*   [《Netty原理剖析》](https://blog.csdn.net/excellentyuxiao/article/details/53390408)
    *   Reactor 模式介绍。
    *   Netty 是 Reactor 模式的一种实现。

## 零拷贝（Zero-copy）

*   [《对于 Netty ByteBuf 的零拷贝(Zero Copy) 的理解》](https://www.cnblogs.com/xys1228/p/6088805.html)
    *   多个物理分离的buffer，通过逻辑上合并成为一个，从而避免了数据在内存之间的拷贝。

## 序列化(二进制协议)

### Hessian

*   [《Hessian原理分析》](https://www.cnblogs.com/happyday56/p/4268249.html)
    Binary-RPC;不仅仅是序列化

### Protobuf

*   [《Protobuf协议的Java应用例子》](https://blog.csdn.net/antgan/article/details/52103966)
    Goolge出品、占用空间和效率完胜其他序列化类库，如Hessian；需要编写  .proto 文件。

*   [《Protocol Buffers序列化协议及应用》](https://worktile.com/tech/share/prototol-buffers)
    *   关于协议的解释；缺点：可读性差;

*   [《简单的使用 protobuf 和 protostuff》](https://blog.csdn.net/eric520zenobia/article/details/53766571)
    *   protostuff 的好处是不用写 .proto 文件，Java 对象直接就可以序列化。

# 数据库

## 基础理论

### 关系数据库设计的三大范式

*   [《数据库的三大范式以及五大约束》](https://www.cnblogs.com/waj6511988/p/7027127.html)
    *   第一范式：数据表中的每一列（每个字段）必须是不可拆分的最小单元，也就是确保每一列的原子性；
    *   第二范式（2NF）：满足1NF后，要求表中的所有列，都必须依赖于主键，而不能有任何一列与主键没有关系，也就是说一个表只描述一件事情；
    *   第三范式：必须先满足第二范式（2NF），要求：表中的每一列只与主键直接相关而不是间接相关，（表中的每一列只能依赖于主键）；

## MySQL

### 原理

*   [《MySQL的InnoDB索引原理详解》](https://blog.csdn.net/voidccc/article/details/40077329)

*   [《MySQL存储引擎－－MyISAM与InnoDB区别》](https://blog.csdn.net/xifeijian/article/details/20316775)
    *   两种类型最主要的差别就是Innodb 支持事务处理与外键和行级锁

*   [《myisam和innodb索引实现的不同》](https://www.2cto.com/database/201211/172380.html)

### InnoDB

*   [《一篇文章带你读懂Mysql和InnoDB》](https://my.oschina.net/kailuncen/blog/1504217)

### 优化

*   [《MySQL36条军规》](http://vdisk.weibo.com/s/muWOT)

*   [《MYSQL性能优化的最佳20+条经验》](https://www.cnblogs.com/zhouyusheng/p/8038224.html)

*   [《SQL优化之道》](https://blog.csdn.net/when_less_is_more/article/details/70187459)

*   [《mysql数据库死锁的产生原因及解决办法》](https://www.cnblogs.com/sivkun/p/7518540.html)

*   [《导致索引失效的可能情况》](https://blog.csdn.net/monkey_d_feilong/article/details/52291556)

*   [《 MYSQL分页limit速度太慢优化方法》](https://www.jianshu.com/p/0a7e3055a01f)
    *   原则上就是缩小扫描范围。

### 索引

#### 聚集索引, 非聚集索引

*   [《MySQL 聚集索引/非聚集索引简述》](https://blog.csdn.net/no_endless/article/details/77073549)
*   [《MyISAM和InnoDB的索引实现》](https://www.cnblogs.com/zlcxbb/p/5757245.html)

MyISAM 是非聚集，InnoDB 是聚集

#### 复合索引

*   [《复合索引的优点和注意事项》](https://www.cnblogs.com/summer0space/p/7247778.html)
    *   文中有一处错误：
    > 对于复合索引,在查询使用时,最好将条件顺序按找索引的顺序,这样效率最高; select \* from table1 where col1=A AND col2=B AND col3=D 如果使用 where col2=B AND col1=A 或者 where col2=B 将不会使用索引
    *   原文中提到索引是按照“col1，col2，col3”的顺序创建的，而mysql在按照最左前缀的索引匹配原则，且会自动优化 where 条件的顺序，当条件中只有 col2=B AND col1=A 时，会自动转化为 col1=A AND col2=B，所以依然会使用索引。
*   [《MySQL查询where条件的顺序对查询效率的影响》](https://www.cnblogs.com/acode/p/7489258.html)

#### 自适应哈希索引(AHI)

*   [《InnoDB存储引擎——自适应哈希索引》](https://blog.csdn.net/Linux_ever/article/details/62043708)

### explain

*   [《MySQL 性能优化神器 Explain 使用分析》](https://segmentfault.com/a/1190000008131735)

## NoSQL

### MongoDB

*   [MongoDB 教程](http://www.runoob.com/mongodb/mongodb-tutorial.html)
*   [《Mongodb相对于关系型数据库的优缺点》](http://mxdxm.iteye.com/blog/2093603)
    *   优点：弱一致性（最终一致），更能保证用户的访问速度；内置GridFS，支持大容量的存储；Schema-less 数据库，不用预先定义结构；内置Sharding；相比于其他NoSQL，第三方支持丰富；性能优越；
    *   缺点：mongodb不支持事务操作；mongodb占用空间过大；MongoDB没有如MySQL那样成熟的维护工具，这对于开发和IT运营都是个值得注意的地方；

### Hbase

*   [《简明 HBase 入门教程（开篇）》](http://www.thebigdata.cn/HBase/35831.html)

*   [《深入学习HBase架构原理》](https://www.cnblogs.com/qiaoyihang/p/6246424.html)

*   [《传统的行存储和（HBase）列存储的区别》](https://blog.csdn.net/youzhouliu/article/details/67632882)

*   [《Hbase与传统数据库的区别》](https://blog.csdn.net/lifuxiangcaohui/article/details/39891099)
    *   空数据不存储，节省空间，且适用于并发。

*   [《HBase Rowkey设计》](https://blog.csdn.net/u014091123/article/details/73163088)
    *   rowkey 按照字典顺序排列，便于批量扫描。
    *   通过散列可以避免热点。

# 搜索引擎

## 搜索引擎原理

*   [《倒排索引--搜索引擎入门》](https://www.jianshu.com/p/0193dc44135b)

## Lucene

*   [《Lucene入门简介》](https://www.cnblogs.com/rodge-run/p/6551152.html)

## Elasticsearch

*   [《Elasticsearch学习，请先看这一篇！》](https://blog.csdn.net/laoyang360/article/details/52244917)
*   [《Elasticsearch索引原理》](https://blog.csdn.net/cyony/article/details/65437708)

## Solr

*   [《 Apache Solr入门教程》](https://blog.csdn.net/u011936655/article/details/51960005)
*   [《elasticsearch与solr比较》](https://blog.csdn.net/convict_eva/article/details/53537837)

## sphinx

*   [《Sphinx 的介绍和原理探索》](http://blog.jobbole.com/101672/)

# 性能

## 性能优化方法论

*   [《15天的性能优化工作，5方面的调优经验》](https://blog.csdn.net/huangwenyi1010/article/details/72673447?ref=myread)
    *   代码层面、业务层面、数据库层面、服务器层面、前端优化。

*   [《系统性能优化的几个方面》](https://blog.csdn.net/tenglizhe/article/details/44563135)

## 容量评估

*   [《联网性能与容量评估的方法论和典型案例》](https://blog.csdn.net/u012528360/article/details/70054156)
*   [《互联网架构，如何进行容量设计？》](https://mp.weixin.qq.com/s?__biz=MjM5ODYxMDA5OQ==\&mid=2651959542\&idx=1\&sn=2494bbea9a855e0e1c3ccd6d2562a600\&scene=21#wechat_redirect)
    *   评估总访问量、评估平均访问量QPS、评估高峰QPS、评估系统、单机极限QPS

## CDN 网络

*   [《CDN加速原理》](https://www.cnblogs.com/wxiaona/p/5867685.html)
*   [《国内有哪些比较好的 CDN？》](https://www.zhihu.com/question/20536932)

## 连接池

*   [《主流Java数据库连接池比较与开发配置实战》](https://blog.csdn.net/fysuccess/article/details/66972554)

## 性能调优

*   [《九大Java性能调试工具，必备至少一款》](https://blog.csdn.net/yethyeth/article/details/73266455)

# 大数据

## 流式计算

### Storm

*   [官方网站](http://storm.apache.org/)
*   [《最详细的Storm入门教程》](https://blog.csdn.net/uisoul/article/details/77989927)

### Flink

*   [《Flink之一 Flink基本原理介绍》](https://blog.csdn.net/lisi1129/article/details/54844919)

### Kafka Stream

*   [《Kafka Stream调研：一种轻量级流计算模式》](https://yq.aliyun.com/articles/58382)

### 应用场景

例如：

*   广告相关实时统计；
*   推荐系统用户画像标签实时更新；
*   线上服务健康状况实时监测；
*   实时榜单；
*   实时数据统计。

## Hadoop

*   [《用通俗易懂的话说下hadoop是什么,能做什么》](https://blog.csdn.net/houbin0912/article/details/72967178)
*   [《史上最详细的Hadoop环境搭建》](http://gitbook.cn/books/5954c9600326c7705af8a92a/index.html)

### HDFS

*   [《【Hadoop学习】HDFS基本原理》](https://segmentfault.com/a/1190000011575458)

### MapReduce

*   [《用通俗易懂的大白话讲解Map/Reduce原理》](https://blog.csdn.net/oppo62258801/article/details/72884633)
*   [《 简单的map-reduce的java例子》](https://blog.csdn.net/foye12/article/details/78358292)

### Yarn

*   [《初步掌握Yarn的架构及原理》](http://www.cnblogs.com/codeOfLife/p/5492740.html)

## Spark

*   [《Spark(一): 基本架构及原理》](http://www.cnblogs.com/tgzhu/p/5818374.html)
*   [《子雨大数据之Spark入门教程(Python版)》](http://dblab.xmu.edu.cn/blog/1709-2/)

# 安全

## web 安全

### XSS

*   [《xss攻击原理与解决方法》](https://blog.csdn.net/qq_21956483/article/details/54377947)

### CSRF

*   [《CSRF原理及防范》](https://coderxing.gitbooks.io/architecture-evolution/di-san-pian-ff1a-bu-luo/641-web-an-quan-fang-fan/6412-csrf.html)

### SQL 注入

*   [《SQL注入》](https://coderxing.gitbooks.io/architecture-evolution/di-san-pian-ff1a-bu-luo/641-web-an-quan-fang-fan/6413-sql-zhu-ru.html)

### Hash Dos

*   [《邪恶的JAVA HASH DOS攻击》](http://www.freebuf.com/articles/web/14199.html)
    *   利用JsonObject 上传大Json，JsonObject 底层使用HashMap；不同的数据产生相同的hash值，使得构建Hash速度变慢，耗尽CPU。
*   [《一种高级的DoS攻击-Hash碰撞攻击》](http://blog.it2048.cn/article_hash-collision.html)
*   [《关于Hash Collision DoS漏洞：解析与解决方案》](http://www.iteye.com/news/23939/)

### 脚本注入

*   [《上传文件漏洞原理及防范》](https://coderxing.gitbooks.io/architecture-evolution/di-san-pian-ff1a-bu-luo/641-web-an-quan-fang-fan/6414-shang-chuan-wen-jian-guo-lv.html)

### 漏洞扫描工具

*   [《DVWA》](https://coderxing.gitbooks.io/architecture-evolution/di-san-pian-ff1a-bu-luo/6421-dvwa.html)
*   [W3af](https://coderxing.gitbooks.io/architecture-evolution/di-san-pian-ff1a-bu-luo/w3af.html)
*   [OpenVAS详解](https://blog.csdn.net/xygg0801/article/details/53610640)

### 验证码

*   [《验证码原理分析及实现》](https://blog.csdn.net/niaonao/article/details/51112686)

*   [《详解滑动验证码的实现原理》](https://my.oschina.net/jiangbianwanghai/blog/1031031)
    *   滑动验证码是根据人在滑动滑块的响应时间，拖拽速度，时间，位置，轨迹，重试次数等来评估风险。

*   [《淘宝滑动验证码研究》](https://www.cnblogs.com/xcj26/p/5242758.html)

## DDoS 防范

*   [《学习手册：DDoS的攻击方式及防御手段》](http://netsecurity.51cto.com/art/201601/503799.htm)
*   [《免费DDoS攻击测试工具大合集》](http://netsecurity.51cto.com/art/201406/442756.htm)

## 用户隐私信息保护

1.  用户密码非明文保存，加动态salt。
2.  身份证号，手机号如果要显示，用 “\*” 替代部分字符。
3.  联系方式在的显示与否由用户自己控制。
4.  TODO

*   [《个人隐私包括哪些》](https://zhidao.baidu.com/question/1988017976673661587.html)

*   [《在互联网上，隐私的范围包括哪些？》](https://www.zhihu.com/question/20137108)

*   [《用户密码保存》](https://coderxing.gitbooks.io/architecture-evolution/di-san-pian-ff1a-bu-luo/642-shu-ju-jia-mi/6425-jia-mi-chang-jing-ff1a-yong-hu-mi-ma-bao-cun.html)

## 序列化漏洞

*   [《Lib之过？Java反序列化漏洞通用利用分析》](https://blog.chaitin.cn/2015-11-11_java_unserialize_rce/)

## 加密解密

### 对称加密

*   [《常见对称加密算法》](https://coderxing.gitbooks.io/architecture-evolution/di-san-pian-ff1a-bu-luo/642-shu-ju-jia-mi/6421-chang-jian-dui-cheng-jia-mi-suan-fa.html)
    *   DES、3DES、Blowfish、AES
    *   DES 采用 56位秘钥，Blowfish 采用1到448位变长秘钥，AES 128，192和256位长度的秘钥。
    *   DES 秘钥太短（只有56位）算法目前已经被 AES 取代，并且 AES 有硬件加速，性能很好。

### 哈希算法

*   [《常用的哈希算法》](https://coderxing.gitbooks.io/architecture-evolution/di-san-pian-ff1a-bu-luo/642-shu-ju-jia-mi/6422-chang-jian-ha-xi-suan-fa-and-hmac.html)
    *   MD5 和 SHA-1 已经不再安全，已被弃用。
    *   目前 SHA-256 是比较安全的。
*   [《基于Hash摘要签名的公网URL签名验证设计方案》](https://blog.csdn.net/zhangruhong168/article/details/78033202)

### 非对称加密

*   [《常见非对称加密算法》](https://coderxing.gitbooks.io/architecture-evolution/di-san-pian-ff1a-bu-luo/642-shu-ju-jia-mi/6424-chang-yong-fei-dui-cheng-jia-mi-suan-fa.html)
    *   RSA、DSA、ECDSA(螺旋曲线加密算法)
    *   和 RSA 不同的是 DSA 仅能用于数字签名，不能进行数据加密解密，其安全性和RSA相当，但其性能要比RSA快。
    *   256位的ECC秘钥的安全性等同于3072位的RSA秘钥。

        [《区块链的加密技术》](http://baijiahao.baidu.com/s?id=1578348858092033763\&wfr=spider\&for=pc)

## 服务器安全

*   [《Linux强化论：15步打造一个安全的Linux服务器》](http://www.freebuf.com/articles/system/121540.html)

## 数据安全

### 数据备份

TODO

## 网络隔离

### 内外网分离

TODO

### 登录跳板机

在内外环境中通过跳板机登录到线上主机。

*   [《搭建简易堡垒机》](http://blog.51cto.com/zero01/2062618)

## 授权、认证

*   [授权认证知识库](https://docs.authing.cn/authing/)

### RBAC

*   [《基于组织角色的权限设计》](https://www.cnblogs.com/zq8024/p/5003050.html)
*   [《权限系统与RBAC模型概述》](https://www.cnblogs.com/shijiaqi1066/p/3793894.html)
*   [《Spring整合Shiro做权限控制模块详细案例分析》](https://blog.csdn.net/he90227/article/details/38663553)

### OAuth2.0

*   [《理解OAuth 2.0》](http://www.ruanyifeng.com/blog/2014/05/oauth_2_0.html)
*   [《一张图搞定OAuth2.0》](https://www.cnblogs.com/flashsun/p/7424071.html)

### OIDC

*   [理解 OIDC](https://docs.authing.cn/authing/advanced/oidc/li-jie-oidc-liu-cheng)

### SAML

*   [理解 SAML](https://docs.authing.cn/authing/advanced/use-saml/li-jie-saml-liu-cheng)

### 双因素认证（2FA）

2FA - Two-factor authentication，用于加强登录验证

常用做法是 登录密码 + 手机验证码（或者令牌Key，类似于与网银的 USB key）

*   【《双因素认证（2FA）教程》】(http://www.ruanyifeng.com/blog/2017/11/2fa-tutorial.html)

### 单点登录(SSO)

*   [《单点登录原理与简单实现》](https://www.cnblogs.com/ywlaker/p/6113927.html)
*   [CAS单点登录框架](https://github.com/apereo/cas)
*   [使用 Authing 实现单点登录](https://docs.authing.cn/authing/quickstart/implement-sso-with-authing)

# 常用开源框架

## 开源协议

*   [《开源协议的选择》](https://coderxing.gitbooks.io/architecture-evolution/chapter1/di-yi-zhang-ff1a-zhun-bei-qi-cheng/12-guan-yu-kai-yuan/123-kai-yuan-xie-yi-de-xuan-ze.html)

*   [如何选择一个开源软件协议](http://choosealicense.online/)

## 日志框架

### Log4j、Log4j2

*   [《log4j 详细讲解》](https://blog.csdn.net/u012422446/article/details/51199724)
*   [《log4j2 实际使用详解》](https://blog.csdn.net/vbirdbest/article/details/71751835)
*   [《Log4j1,Logback以及Log4j2性能测试对比》](https://my.oschina.net/OutOfMemory/blog/789267)
    *   Log4J 异步日志性能优异。

### Logback

*   [《最全LogBack 详解、含java案例和配置说明》](https://blog.csdn.net/rulon147/article/details/52620541)

## ORM

*   [《ORM框架使用优缺点》](https://blog.csdn.net/sinat_34093604/article/details/53082000)
    *   主要目的是为了提高开发效率。

**MyBatis：**

*   [《mybatis缓存机制详解》](https://www.cnblogs.com/winclpt/articles/7511672.html)
    *   一级缓存是SqlSession级别的缓存，缓存的数据只在SqlSession内有效
    *   二级缓存是mapper级别的缓存，同一个namespace公用这一个缓存，所以对SqlSession是共享的；使用 LRU 机制清理缓存，通过 cacheEnabled 参数开启。

*   [《MyBatis学习之代码生成器Generator》](https://blog.csdn.net/baidu_32877851/article/details/53959268)

## 网络框架

TODO

## Web 框架

### Spring 家族

**Spring**

*   [Spring 简明教程](https://www.w3cschool.cn/wkspring/)

**Spring Boot**

*   [官方网站](http://projects.spring.io/spring-boot/)
*   [《Spring Boot基础教程》](http://blog.didispace.com/Spring-Boot%E5%9F%BA%E7%A1%80%E6%95%99%E7%A8%8B/)

**Spring Cloud**

*   [Spring Boot 中文索引站](http://springboot.fun/)
*   [Spring Cloud 中文文档](https://springcloud.cc/)
*   [《Spring Cloud基础教程》](http://blog.didispace.com/Spring-Cloud%E5%9F%BA%E7%A1%80%E6%95%99%E7%A8%8B/)

## 工具框架

*   [《Apache Commons 工具类介绍及简单使用》](https://www.cnblogs.com/crazylqy/p/4872236.html)
*   [《Google guava 中文教程》](http://ifeve.com/google-guava/)

# 分布式设计

## 扩展性设计

*   [《架构师不可不知的十大可扩展架构》](https://blog.csdn.net/hemin1003/article/details/53633926)
    *   总结下来，通用的套路就是分布、缓存及异步处理。

*   [《可扩展性设计之数据切分》](https://yq.aliyun.com/articles/38119)
    *   水平切分+垂直切分
    *   利用中间件进行分片如，MySQL Proxy。
    *   利用分片策略进行切分，如按照ID取模。

*   [《说说如何实现可扩展性的大型网站架构》](https://blog.csdn.net/deniro_li/article/details/78458306)
    *   分布式服务+消息队列。

*   [《大型网站技术架构（七）--网站的可扩展性架构》](https://blog.csdn.net/chaofanwei/article/details/29191073)

## 稳定性 & 高可用

*   [《系统设计：关于高可用系统的一些技术方案》](https://blog.csdn.net/hustspy1990/article/details/78008324)
    *   可扩展：水平扩展、垂直扩展。 通过冗余部署，避免单点故障。
    *   隔离：避免单一业务占用全部资源。避免业务之间的相互影响 2. 机房隔离避免单点故障。
    *   解耦：降低维护成本，降低耦合风险。减少依赖，减少相互间的影响。
    *   限流：滑动窗口计数法、漏桶算法、令牌桶算法等算法。遇到突发流量时，保证系统稳定。
    *   降级：紧急情况下释放非核心功能的资源。牺牲非核心业务，保证核心业务的高可用。
    *   熔断：异常情况超出阈值进入熔断状态，快速失败。减少不稳定的外部依赖对核心服务的影响。
    *   自动化测试：通过完善的测试，减少发布引起的故障。
    *   灰度发布：灰度发布是速度与安全性作为妥协，能够有效减少发布故障。

*   [《关于高可用的系统》](https://coolshell.cn/articles/17459.html)
    *   设计原则：数据不丢(持久化)；服务高可用(服务副本)；绝对的100%高可用很难，目标是做到尽可能多的9，如99.999%（全年累计只有5分钟）。

### 硬件负载均衡

*   [《转！！负载均衡器技术Nginx和F5的优缺点对比》](https://www.cnblogs.com/wuyun-blog/p/6186198.html)
    *   主要是和F5对比。

*   [《软/硬件负载均衡产品 你知多少？》](https://www.cnblogs.com/lcword/p/5773296.html)

### 软件负载均衡

*   [《几种负载均衡算法》](https://www.cnblogs.com/tianzhiliang/articles/2317808.html)
    轮寻、权重、负载、最少连接、QoS

*   [《DNS负载均衡》](https://coderxing.gitbooks.io/architecture-evolution/di-san-pian-ff1a-bu-luo/611-dns-fang-shi.html)
    *   配置简单，更新速度慢。

*   [《Nginx负载均衡》](https://coderxing.gitbooks.io/architecture-evolution/di-san-pian-ff1a-bu-luo/613-nginx-fu-zai-jun-heng.html)
    *   简单轻量、学习成本低；主要适用于web应用。

*   [《借助LVS+Keepalived实现负载均衡 》](https://www.cnblogs.com/edisonchou/p/4281978.html)
    *   配置比较负载、只支持到4层，性能较高。

*   [《HAProxy用法详解 全网最详细中文文档》](http://www.ttlsa.com/linux/haproxy-study-tutorial/)
    *   支持到七层（比如HTTP）、功能比较全面，性能也不错。

*   [《Haproxy+Keepalived+MySQL实现读均衡负载》](http://blog.itpub.net/25704976/viewspace-1319781/)
    *   主要是用户读请求的负载均衡。

*   [《rabbitmq+haproxy+keepalived实现高可用集群搭建》](https://www.cnblogs.com/lylife/p/5584019.html)

### 限流

*   [《谈谈高并发系统的限流》](https://www.cnblogs.com/haoxinyue/p/6792309.html)
    *   计数器：通过滑动窗口计数器，控制单位时间内的请求次数，简单粗暴。
    *   漏桶算法：固定容量的漏桶，漏桶满了就丢弃请求，比较常用。
    *   令牌桶算法：固定容量的令牌桶，按照一定速率添加令牌，处理请求前需要拿到令牌，拿不到令牌则丢弃请求，或进入丢队列，可以通过控制添加令牌的速率，来控制整体速度。Guava 中的 RateLimiter 是令牌桶的实现。
    *   Nginx 限流：通过 `limit_req` 等模块限制并发连接数。

### 应用层容灾

*   [《防雪崩利器：熔断器 Hystrix 的原理与使用》](https://segmentfault.com/a/1190000005988895)
    *   雪崩效应原因：硬件故障、硬件故障、程序Bug、重试加大流量、用户大量请求。
    *   雪崩的对策：限流、改进缓存模式(缓存预加载、同步调用改异步)、自动扩容、降级。
    *   Hystrix设计原则：
        *   资源隔离：Hystrix通过将每个依赖服务分配独立的线程池进行资源隔离, 从而避免服务雪崩。
        *   熔断开关：服务的健康状况 = 请求失败数 / 请求总数，通过阈值设定和滑动窗口控制开关。
        *   命令模式：通过继承 HystrixCommand 来包装服务调用逻辑。

*   [《缓存穿透，缓存击穿，缓存雪崩解决方案分析》](https://blog.csdn.net/zeb_perfect/article/details/54135506)

*   [《缓存击穿、失效以及热点key问题》](https://blog.csdn.net/zeb_perfect/article/details/54135506)
    *   主要策略：失效瞬间：单机使用锁；使用分布式锁；不过期；
    *   热点数据：热点数据单独存储；使用本地缓存；分成多个子key；

### 跨机房容灾

*   [《“异地多活”多机房部署经验谈》](http://dc.idcquan.com/ywgl/71559.shtml)
    *   通过自研中间件进行数据同步。

*   [《异地多活（异地双活）实践经验》](https://blog.csdn.net/jeffreynicole/article/details/48135093)
    *   注意延迟问题，多次跨机房调用会将延时放大数倍。
    *   建房间专线很大概率会出现问题，做好运维和程序层面的容错。
    *   不能依赖于程序端数据双写，要有自动同步方案。
    *   数据永不在高延迟和较差网络质量下，考虑同步质量问题。
    *   核心业务和次要业务分而治之，甚至只考虑核心业务。
    *   异地多活监控部署、测试也要跟上。
    *   业务允许的情况下考虑用户分区，尤其是游戏、邮箱业务。
    *   控制跨机房消息体大小，越小越好。
    *   考虑使用docker容器虚拟化技术，提高动态调度能力。

*   [容灾技术及建设经验介绍](https://blog.csdn.net/yoara/article/details/38013751)

### 容灾演练流程

*   [《依赖治理、灰度发布、故障演练，阿里电商故障演练系统的设计与实战经验》](https://mp.weixin.qq.com/s?__biz=MjM5MDE0Mjc4MA==\&mid=2650996320\&idx=1\&sn=0ed3be190bbee4a9277886ef88cbb2e5)
    *   常见故障画像
    *   案例：预案有效性、预案有效性、故障复现、架构容灾测试、参数调优、参数调优、故障突袭、联合演练。

### 平滑启动

*   平滑重启应用思路
    1.端流量（如vip层）、2. flush 数据(如果有)、3, 重启应用

*   [《JVM安全退出（如何优雅的关闭java服务）》](https://blog.csdn.net/u011001084/article/details/73480432)
    推荐推出方式：System.exit，Kill SIGTERM；不推荐 kill-9；用 Runtime.addShutdownHook 注册钩子。

*   [《常见Java应用如何优雅关闭》](http://ju.outofmemory.cn/entry/337235)
    Java、Spring、Dubbo 优雅关闭方式。

## 数据库扩展

### 读写分离模式

*   [《Mysql主从方案的实现》](https://www.cnblogs.com/houdj/p/6563771.html)

*   [《搭建MySQL主从复制经典架构》](https://www.cnblogs.com/edisonchou/p/4133148.html)

*   [《Haproxy+多台MySQL从服务器(Slave) 实现负载均衡》](https://blog.csdn.net/nimasike/article/details/48048341)

*   [《DRBD+Heartbeat+Mysql高可用读写分离架构》](https://www.cnblogs.com/zhangsubai/p/6801764.html)
    *   DRDB 进行磁盘复制，避免单点问题。

*   [《MySQL Cluster 方式》](https://coderxing.gitbooks.io/architecture-evolution/di-san-pian-ff1a-bu-luo/62-ke-kuo-zhan-de-shu-ju-ku-jia-gou/621-gao-ke-yong-mysql-de-ji-zhong-fang-an/6214-mysql-cluster-fang-an.html)

### 分片模式

*   [《分库分表需要考虑的问题及方案》](https://www.jianshu.com/p/32b3e91aa22c)
    *   中间件： 轻量级：sharding-jdbc、TSharding；重量级：Atlas、MyCAT、Vitess等。
    *   问题：事务、Join、迁移、扩容、ID、分页等。
    *   事务补偿：对数据进行对帐检查;基于日志进行比对;定期同标准数据来源进行同步等。
    *   分库策略：数值范围；取模；日期等。
    *   分库数量：通常 MySQL 单库 5千万条、Oracle 单库一亿条需要分库。

*   [《MySql分表和表分区详解》](https://www.2cto.com/database/201503/380348.html)
    *   分区：是MySQL内部机制，对客户端透明，数据存储在不同文件中，表面上看是同一个表。
    *   分表：物理上创建不同的表、客户端需要管理分表路由。

## 服务治理

### 服务注册与发现

*   [《永不失联！如何实现微服务架构中的服务发现？》](https://blog.csdn.net/jiaolongdy/article/details/51188798)
    *   客户端服务发现模式：客户端直接查询注册表，同时自己负责负载均衡。Eureka 采用这种方式。
    *   服务器端服务发现模式：客户端通过负载均衡查询服务实例。

*   [《SpringCloud服务注册中心比较:Consul vs Zookeeper vs Etcd vs Eureka》](https://blog.csdn.net/u010963948/article/details/71730165)
    *   CAP支持：Consul（CA）、zookeeper（cp）、etcd（cp） 、euerka（ap）
    *   作者认为目前 Consul 对 Spring cloud 的支持比较好。

*   [《基于Zookeeper的服务注册与发现》](http://mobile.51cto.com/news-502394.htm)
    *   优点：API简单、Pinterest，Airbnb 在用、多语言、通过watcher机制来实现配置PUSH，能快速响应配置变化。

### 服务路由控制

*   [《分布式服务框架学习笔记4 服务路由》](https://blog.csdn.net/xundh/article/details/59492750)
    *   原则：透明化路由
    *   负载均衡策略：随机、轮询、服务调用延迟、一致性哈希、粘滞连接
    *   本地路由优先策略：injvm(优先调用jvm内部的服务)，innative(优先使用相同物理机的服务),原则上找距离最近的服务。
    *   配置方式：统一注册表；本地配置；动态下发。

## 分布式一致

### CAP 与 BASE 理论

*   [《从分布式一致性谈到CAP理论、BASE理论》](http://www.cnblogs.com/szlbm/p/5588543.html)
    *   一致性分类：强一致(立即一致)；弱一致(可在单位时间内实现一致，比如秒级)；最终一致(弱一致的一种，一定时间内最终一致)
    *   CAP：一致性、可用性、分区容错性(网络故障引起)
    *   BASE：Basically Available（基本可用）、Soft state（软状态）和Eventually consistent（最终一致性）
    *   BASE理论的核心思想是：即使无法做到强一致性，但每个应用都可以根据自身业务特点，采用适当的方式来使系统达到最终一致性。

### 分布式锁

*   [《分布式锁的几种实现方式》](http://www.hollischuang.com/archives/1716)
    *   基于数据库的分布式锁：优点：操作简单、容易理解。缺点：存在单点问题、数据库性能够开销较大、不可重入；
    *   基于缓存的分布式锁：优点：非阻塞、性能好。缺点：操作不好容易造成锁无法释放的情况。
    *   Zookeeper 分布式锁：通过有序临时节点实现锁机制，自己对应的节点需要最小，则被认为是获得了锁。优点：集群可以透明解决单点问题，避免锁不被释放问题，同时锁可以重入。缺点：性能不如缓存方式，吞吐量会随着zk集群规模变大而下降。

*   [《基于Zookeeper的分布式锁》](https://www.tuicool.com/articles/VZJr6fY)
    *   清楚的原理描述 + Java 代码示例。

*   [《jedisLock—redis分布式锁实现》](https://www.cnblogs.com/0201zcr/p/5942748.html)
    *   基于 setnx(set if ont exists)，有则返回false，否则返回true。并支持过期时间。

*   [《Memcached 和 Redis 分布式锁方案》](https://blog.csdn.net/albertfly/article/details/77412333)
    *   利用 memcached 的 add（有别于set）操作，当key存在时，返回false。

### 分布式一致性算法

#### PAXOS

*   [《分布式系列文章——Paxos算法原理与推导》](https://www.cnblogs.com/linbingdong/p/6253479.html)
*   [《Paxos-->Fast Paxos-->Zookeeper分析》](https://blog.csdn.net/u010039929/article/details/70171672)
*   [《【分布式】Zookeeper与Paxos》](https://www.cnblogs.com/leesf456/p/6012777.html)

#### Zab

*   [《Zab：Zookeeper 中的分布式一致性协议介绍》](https://www.jianshu.com/p/fb527a64deee)

#### Raft

*   [《Raft 为什么是更易理解的分布式一致性算法》](http://www.cnblogs.com/mindwind/p/5231986.html)
    *   三种角色：Leader（领袖）、Follower（群众）、Candidate（候选人）
    *   通过随机等待的方式发出投票，得票多的获胜。

#### Gossip

*   [《Gossip算法》](http://blog.51cto.com/tianya23/530743)

#### 两阶段提交、多阶段提交

*   [《关于分布式事务、两阶段提交协议、三阶提交协议》](http://blog.jobbole.com/95632/)

### 幂等

*   [《分布式系统---幂等性设计》](https://www.cnblogs.com/wxgblogs/p/6639272.html)
    *   幂等特性的作用：该资源具备幂等性，请求方无需担心重复调用会产生错误。
    *   常见保证幂等的手段：MVCC（类似于乐观锁）、去重表(唯一索引)、悲观锁、一次性token、序列号方式。

### 分布式一致方案

*   [《分布式系统事务一致性解决方案》](http://www.infoq.com/cn/articles/solution-of-distributed-system-transaction-consistency)
*   [《保证分布式系统数据一致性的6种方案》](https://weibo.com/ttarticle/p/show?id=2309403965965003062676)

### 分布式 Leader 节点选举

*   [《利用zookeeper实现分布式leader节点选举》](https://blog.csdn.net/johnson_moon/article/details/78809995)

### TCC(Try/Confirm/Cancel) 柔性事务

*   [《传统事务与柔性事务》](https://www.jianshu.com/p/ab1a1c6b08a1)
    *   基于BASE理论：基本可用、柔性状态、最终一致。
    *   解决方案：记录日志+补偿（正向补充或者回滚）、消息重试(要求程序要幂等)；“无锁设计”、采用乐观锁机制。

## 分布式文件系统

*   [说说分布式文件存储系统-基本架构](https://zhuanlan.zhihu.com/p/27666295) ？
*   [《各种分布式文件系统的比较》](https://blog.csdn.net/gatieme/article/details/44982961) ？
    *   HDFS：大批量数据读写，用于高吞吐量的场景，不适合小文件。
    *   FastDFS：轻量级、适合小文件。

## 唯一ID 生成

### 全局唯一ID

*   [《高并发分布式系统中生成全局唯一Id汇总》](https://www.cnblogs.com/baiwa/p/5318432.html)
    *   Twitter 方案（Snowflake 算法）：41位时间戳+10位机器标识（比如IP，服务器名称等）+12位序列号(本地计数器)
    *   Flicker 方案：MySQL自增ID + "REPLACE INTO XXX:SELECT LAST\_INSERT\_ID();"
    *   UUID：缺点，无序，字符串过长，占用空间，影响检索性能。
    *   MongoDB 方案：利用 ObjectId。缺点：不能自增。

*   [《TDDL 在分布式下的SEQUENCE原理》](https://blog.csdn.net/hdu09075340/article/details/79103851)
    *   在数据库中创建 sequence 表，用于记录，当前已被占用的id最大值。
    *   每台客户端主机取一个id区间（比如 1000~2000）缓存在本地，并更新 sequence 表中的id最大值记录。
    *   客户端主机之间取不同的id区间，用完再取，使用乐观锁机制控制并发。

## 一致性Hash算法

*   [《一致性哈希算法》](https://coderxing.gitbooks.io/architecture-evolution/di-san-pian-ff1a-bu-luo/631-yi-zhi-xing-ha-xi.html)

# 设计思想 & 开发模式

## DDD(Domain-driven Design - 领域驱动设计)

*   [《浅谈我对DDD领域驱动设计的理解》](https://www.cnblogs.com/netfocus/p/5548025.html)
    *   概念：DDD 主要对传统软件开发流程(分析-设计-编码)中各阶段的割裂问题而提出，避免由于一开始分析不明或在软件开发过程中的信息流转不一致而造成软件无法交付（和需求方设想不一致）的问题。DDD 强调一切以领域（Domain）为中心，强调领域专家（Domain Expert）的作用，强调先定义好领域模型之后在进行开发，并且领域模型可以指导开发（所谓的驱动）。
    *   过程：理解领域、拆分领域、细化领域，模型的准确性取决于模型的理解深度。
    *   设计：DDD 中提出了建模工具，比如聚合、实体、值对象、工厂、仓储、领域服务、领域事件来帮助领域建模。

*   [《领域驱动设计的基础知识总结》](https://www.cnblogs.com/butterfly100/p/7827870.html)
    *   领域（Doamin）本质上就是问题域，比如一个电商系统，一个论坛系统等。
    *   界限上下文（Bounded Context）：阐述子域之间的关系，可以简单理解成一个子系统或组件模块。
    *   领域模型（Domain Model）：DDD的核心是建立（用通用描述语言、工具—领域通用语言）正确的领域模型；反应业务需求的本质，包括实体和过程；其贯穿软件分析、设计、开发 的整个过程；常用表达领域模型的方式：图、代码或文字；
    *   领域通用语言：领域专家、开发设计人员都能理解的语言或工具。
    *   经典分层架构：用户界面/展示层、应用层、领域层、基础设施层，是四层架构模式。
    *   使用的模式：
        *   关联尽量少，尽量单项，尽量降低整体复杂度。
        *   实体（Entity）：领域中的唯一标示，一个实体的属性尽量少，少则清晰。
        *   值对象（Value Object）：没有唯一标识，且属性值不可变，小而简单的对象，比如Date。
        *   领域服务（Domain Service）： 协调多个领域对象，只有方法没有状态(不存数据)；可以分为应用层服务，领域层服务、基础层服务。
        *   聚合及聚合根（Aggregate，Aggregate Root）：聚合定义了一组具有内聚关系的相关对象的集合；聚合根是对聚合引用的唯一元素；当修改一个聚合时，必须在事务级别；大部分领域模型中，有70%的聚合通常只有一个实体，30%只有2~3个实体；如果一个聚合只有一个实体，那么这个实体就是聚合根；如果有多个实体，那么我们可以思考聚合内哪个对象有独立存在的意义并且可以和外部直接进行交互；
        *   工厂（Factory）：类似于设计模式中的工厂模式。
        *   仓储（Repository）：持久化到DB，管理对象，且只对聚合设计仓储。

*   [《领域驱动设计(DDD)实现之路》](http://www.cnblogs.com/Leo_wl/p/3866629.html)
    *   聚合：比如一辆汽车（Car）包含了引擎（Engine）、车轮（Wheel）和油箱（Tank）等组件，缺一不可。

*   [《领域驱动设计系列（2）浅析VO、DTO、DO、PO的概念、区别和用处》](http://www.hollischuang.com/archives/553)

### 命令查询职责分离(CQRS)

CQRS — Command Query Responsibility Seperation

*   [《领域驱动设计系列 (六)：CQRS》](https://www.cnblogs.com/cnblogsfans/p/4551990.html)
    *   核心思想：读写分离（查询和更新在不同的方法中），不同的流程只是不同的设计方式，CQ代码分离，分布式环境中会有明显体现（有冗余数据的情况下），目的是为了高性能。

*   [《DDD CQRS架构和传统架构的优缺点比较》](http://www.techweb.com.cn/network/system/2017-07-07/2553563.shtml)
    *   最终一致的设计理念；依赖于高可用消息中间件。

*   [《CQRS架构简介》](http://www.cnblogs.com/netfocus/p/4055346.html)
    *   一个实现 CQRS 的抽象案例。

*   [《深度长文：我对CQRS/EventSourcing架构的思考》](http://www.uml.org.cn/zjjs/201609221.asp)
    *   CQRS 模式分析 + 12306 抢票案例

### 贫血，充血模型

*   [《贫血，充血模型的解释以及一些经验》](https://kb.cnblogs.com/page/520743/)
    *   失血模型：老子和儿子分别定义，相互不知道，二者实体定义中完全没有业务逻辑，通过外部Service进行关联。
    *   贫血模型：老子知道儿子，儿子也知道老子；部分业务逻辑放到实体中；优点：各层单项依赖，结构清楚，易于维护；缺点：不符合OO思想，相比于充血模式，Service层较为厚重；
    *   充血模型：和贫血模型类似，区别在于如何划分业务逻辑。优点：Service层比较薄，只充当Facade的角色，不和DAO打交道、复合OO思想；缺点：非单项依赖，DO和DAO之间双向依赖、和Service层的逻辑划分容易造成混乱。
    *   肿胀模式：是一种极端情况，取消Service层、全部业务逻辑放在DO中；优点：符合OO思想、简化了分层；缺点：暴露信息过多、很多非DO逻辑也会强行并入DO。这种模式应该避免。
    *   作者主张使用贫血模式。

## Actor 模式

TODO

## 响应式编程

### Reactor

TODO

### RxJava

TODO

### Vert.x

TODO

## DODAF2.0

*   [《DODAF2.0方法论》](http://www.360doc.com/content/16/0627/19/33945750_571201779.shtml)
*   [《DODAF2.0之能力视角如何落地》](http://blog.51cto.com/xiaoyong/1553164)

## Serverless

无需过多关系服务器的服务架构理念。

*   [《什么是Serverless无服务器架构？》](http://www.jdon.com/soa/serverless.html)
    *   Serverless 不代表出去服务器，而是去除对服务器运行状态的关心。
    *   Serverless 代表一思维方式的转变，从“构建一套服务在一台服务器上，对对个事件进行响应转变为构建一个为服务器，来响应一个事件”。
    *   Serverless 不代表某个具体的框架。

*   [《如何理解Serverless？》](http://www.infoq.com/cn/news/2017/10/how-to-understand-serverless)
    *   依赖于 Baas （(Mobile) Backend as a Service） 和 Faas （Functions as a service）

## Service Mesh

*   [《什么是Service Mesh？》](https://time.geekbang.org/article/2355)
*   [《初识 Service Mesh》](https://www.jianshu.com/p/e23e3e74538e)

# 项目管理

## 架构评审

*   [《架构设计之如何评审架构设计说明书》](http://developer.51cto.com/art/201506/478486.htm)
*   [《人人都是架构师：非功能性需求》](https://blog.csdn.net/wireless_com/article/details/45935591)

## 重构

*   [《架构之重构的12条军规》](http://www.infoq.com/cn/articles/architect-12-rules-complete/)

## 代码规范

*   [《阿里巴巴Java开发手册》](https://github.com/alibaba/p3c)

## 代码 Review

制度还是制度!
另外，每个公司需要根据自己的需求和目标制定自己的 check list

*   [《为什么你做不好 Code Review？》](http://www.sohu.com/a/229745352_181657)
    *   代码 review 做的好，在于制度建设。

*   [《从零开始Code Review》](https://blog.csdn.net/uxyheaven/article/details/49773619)

*   [《Code Review Checklist》](https://www.cnblogs.com/zuoping/p/5477047.html)

*   [《Java Code Review Checklist》](https://dzone.com/articles/java-code-review-checklist)

*   [《如何用 gitlab 做 code review》](https://blog.csdn.net/legend0011/article/details/45585575)

## RUP

*   [《运用RUP 4+1视图方法进行软件架构设计》](https://blog.csdn.net/apanious/article/details/51011946)

## 看板管理

*   [《说说看板在项目中的应用》](https://blog.csdn.net/tkchen/article/details/51637643)

## SCRUM

SCRUM - 争球

*   3个角色:Product Owner(PO) 产品负责人;Scrum Master（SM），推动Scrum执行;Team 开发团队。

*   3个工件：Product Backlog 产品TODOLIST，含优先级;Sprint Backlog 功能开发 TODO LIST；燃尽图；

*   五个价值观：专注、勇气、公开、承诺、尊重。

*   [《敏捷项目管理流程-Scrum框架最全总结！》](https://blog.csdn.net/inny100_100/article/details/54633757)

*   [《敏捷其实很简单3---敏捷方法之scrum》](https://blog.csdn.net/superkunkun/article/details/52951142)

## 敏捷开发

TODO

## 极限编程（XP）

XP - eXtreme Programming

*   [《主流敏捷开发方法：极限编程XP》](http://www.woshipm.com/pmd/406917.html)
    *   是一种指导开发人员的方法论。
    *   4大价值：
        *   沟通：鼓励口头沟通，提高效率。
        *   简单：够用就好。
        *   反馈：及时反馈、通知相关人。
        *   勇气：提倡拥抱变化，敢于重构。
    *   5个原则：快速反馈、简单性假设、逐步修改、提倡更改（小步快跑）、优质工作（保证质量的前提下保证小步快跑）。
    *   5个工作：阶段性冲刺；冲刺计划会议；每日站立会议；冲刺后review；回顾会议。

## 结对编程

边写码，边review。能够增强代码质量、减少bug。

*   [《结对编程》](http://www.baike.com/wiki/%E7%BB%93%E5%AF%B9%E7%BC%96%E7%A8%8B)

## PDCA 循环质量管理

P——PLAN 策划，D——DO 实施，C——CHECK 检查，A——ACT 改进

*   [《PDCA》](http://www.baike.com/wiki/PDCA)

## FMEA管理模式

TODO

# 通用业务术语

TODO

# 技术趋势

TODO

# 政策、法规

## 法律

*   [《中华人民共和国网络安全法》](https://baike.baidu.com/item/%E4%B8%AD%E5%8D%8E%E4%BA%BA%E6%B0%91%E5%85%B1%E5%92%8C%E5%9B%BD%E7%BD%91%E7%BB%9C%E5%AE%89%E5%85%A8%E6%B3%95/16843044)
    *   2016年11月7日发布，自2017年6月1日起施行

*   [《个人信息保护法》](https://baike.baidu.com/item/个人信息保护法/8343360)
    *   个人信息保护法是一部保护个人信息的法律条款，现尚在制订中，2019全国两会信息安全相关提案中，有政协委员呼吁关注大数据时代隐私保护，加速立法。

*   [《最高人民法院、最高人民检察院关于办理侵犯公民个人信息刑事案件适用法律若干问题的解释》](https://baike.baidu.com/item/最高人民法院、最高人民检察院关于办理侵犯公民个人信息刑事案件适用法律若干问题的解释/20497481)
    *   《解释》共十三条，自2017年6月1日起施行
    > *   1、对于行踪轨迹信息、通信内容、征信信息、财产信息，非法获取、出售或者提供50条以上即算“情节严重”；
    > *   2、对于住宿信息、通信记录、健康生理信息、交易信息等其他可能影响人身、财产安全的公民个人信息，标准则是 500条以上；
    > *   3、对于其他公民个人信息，标准为 5000条以上。

*   [《中华人民共和国电子商务法》](https://baike.baidu.com/item/中华人民共和国电子商务法/16467544)
    *   2018年8月31日，十三届全国人大常委会第五次会议表决通过《电子商务法》，自2019年1月1日起施行
    *   [解读电子商务法（一）什么是电商](https://v.youku.com/v_show/id_XNDAzNjAyNDM0MA==.html)
    *   [解读电子商务法（二）电商经营者](https://v.youku.com/v_show/id_XNDA1OTc0OTQ5Mg==.html)
    *   [解读电子商务法（三）电商行为规范](https://v.youku.com/v_show/id_XNDA4NzIyNjI4MA==.html)
    *   [解读电子商务法（四）电商的法律关系](https://v.qq.com/x/page/e08443fc1cr.html)
    *   [解读电子商务法（外传）电商挣钱的秘密](https://v.youku.com/v_show/id_XNDA4MTQ2Nzk4NA==.html)
    *   [解读电子商务法（外传）电商模式](https://v.qq.com/x/page/j0844twjwr5.html)

*   [程序员需要知道的法律常识](https://blog.csdn.net/a331685690/article/details/79917772)

*   [白话法律42讲-为程序员打造的专属法律武器](https://time.geekbang.org/column/132)

### 严格遵守刑法253法条

我国刑法第253条之一规定：

> *   国家机关或者金融、电信、交通、教育、医疗等单位的工作人员，违反国家规定，将本单位在履行职责或者提供服务过程中获得的公民个人信息，出售或者非法提供给他人，情节严重的，处3年以下有期徒刑或者拘役，并处或者单处罚金。
> *   窃取或者以其他方法非法获取上述信息，情节严重的，依照前款的规定处罚。
> *   单位犯前两款罪的，对单位判处罚金，并对其直接负责的主管人员和其他直接责任人员，依照各该款的规定处罚。

最高人民法院、最高人民检察院关于执行《中华人民共和国刑法》确定罪名的补充规定（四）规定：触犯刑法第253条之一第1款之规定，构成“出售、非法提供公民个人信息罪”；触犯刑法第253条之一第2款之规定，构成“非法获取公民个人信息罪”

*   [《非法获取公民个人信息罪》](https://baike.baidu.com/item/%E9%9D%9E%E6%B3%95%E8%8E%B7%E5%8F%96%E5%85%AC%E6%B0%91%E4%B8%AA%E4%BA%BA%E4%BF%A1%E6%81%AF%E7%BD%AA)

### 避风港原则

“避风港”原则是指在发生著作权侵权案件时，当ISP（网络服务提供商）只提供空间服务，并不制作网页内容，如果ISP被告知侵权，则有删除的义务，否则就被视为侵权。如果侵权内容既不在ISP的服务器上存储，又没有被告知哪些内容应该删除，则ISP不承担侵权责任。 后来避风港原则也被应用在搜索引擎、网络存储、在线图书馆等方面。

*   [《避风港原则》](https://baike.baidu.com/item/%E9%81%BF%E9%A3%8E%E6%B8%AF%E5%8E%9F%E5%88%99/588459?fr=aladdin)

# 架构师素质

*   [《架构师画像》](http://hellojava.info/?p=430)
    *   业务理解和抽象能力
    *   NB的代码能力
    *   全面：1. 在面对业务问题上，架构师脑海里是否会浮现出多种技术方案；2. 在做系统设计时是否考虑到了足够多的方方面面；3. 在做系统设计时是否考虑到了足够多的方方面面；
    *   全局：是否考虑到了对上下游的系统的影响。
    *   权衡：权衡投入产出比；优先级和节奏控制；

*   [《关于架构优化和设计，架构师必须知道的事情》](http://www.infoq.com/cn/articles/architecture-optimization-and-design-the-architect-must-know)
    *   要去考虑的细节：模块化、轻耦合、无共享架构；减少各个组件之前的依赖、注意服务之间依赖所有造成的链式失败及影响等。
    *   基础设施、配置、测试、开发、运维综合考虑。
    *   考虑人、团队、和组织的影响。

*   [《如何才能真正的提高自己，成为一名出色的架构师？》](https://www.zhihu.com/question/19841397)

*   [《架构师的必备素质和成长途径》](https://blog.csdn.net/sanbingyutuoniao123/article/details/54144129)
    *   素质：业务理解、技术广度、技术深度、丰富经验、沟通能力、动手能力、美学素养。
    *   成长路径：2年积累知识、4年积累技能和组内影响力、7年积累部门内影响力、7年以上积累跨部门影响力。

*   [《架构设计师—你在哪层楼？》](http://blog.51cto.com/frankfan/1248401)
    *   第一层的架构师看到的只是产品本身
    *   第二层的架构师不仅看到自己的产品，还看到了整体的方案
    *   第三层的架构师看到的是商业价值

# 团队管理

TODO

## 招聘

# 资讯

## 行业资讯

*   [36kr](http://36kr.com/)
*   [Techweb](http://www.techweb.com.cn/)

## 公众号列表

TODO

## 博客

### 团队博客

*   [阿里中间件博客](http://jm.taobao.org/)
*   [美团点评技术团队博客](https://tech.meituan.com)

### 个人博客

*   [阮一峰的网络日志](http://www.ruanyifeng.com/)
*   [酷壳 - COOLSHELL-陈皓](https://coolshell.cn/)
*   [hellojava-阿里毕玄](http://hellojava.info/)
*   [Cm's Blog](http://cmsblogs.com/)
*   [程序猿DD-翟永超-《Spring Cloud微服务实战》作者](http://blog.didispace.com/)

## 综合门户、社区

**国内：**

*   [CSDN](http://csdn.net)
    老牌技术社区、不必解释。

*   [51cto.com](http://www.51cto.com/)

*   [ITeye](http://www.iteye.com/)
    *   偏 Java 方向

*   [博客园](https://www.cnblogs.com)

*   [ChinaUnix](http://www.chinaunix.net/)
    *   偏 Linux 方向

*   [开源中国社区](https://www.oschina.net/)

*   [InfoQ](https://www.infoq.cn/)

*   [深度开源](http://www.open-open.com/)

*   [伯乐在线](http://www.jobbole.com/)
    *   涵盖 IT职场、Web前端、后端、移动端、数据库等方面内容，偏技术端。

*   [ITPUB](http://www.itpub.net/)

*   [腾讯云— 云+社区](https://cloud.tencent.com/developer/column)

*   [阿里云— 云栖社区](https://yq.aliyun.com/)

*   [IBM DeveloperWorks](https://www.ibm.com/developerworks/cn/)

*   [开发者头条](https://toutiao.io/)

*   [LinkedKeeper](http://www.linkedkeeper.com)

**国外：**

*   [DZone](https://dzone.com)
*   [Reddit](https://www.reddit.com)

## 问答、讨论类社区

*   [segmentfault](https://segmentfault.com)
    *   问答+专栏
*   [知乎](https://www.zhihu.com/)
*   [stackoverflow](https://stackoverflow.com/)

## 行业数据分析

*   [艾瑞网](http://report.iresearch.cn/)

*   [QUEST MOBILE](https://www.questmobile.com.cn)

*   [国家数据](http://data.stats.gov.cn/)

*   [TalkingData](http://www.talkingdata.com/)

## 专项网站

*   测试:
    *   [领测国际](http://www.ltesting.net/)
    *   [测试窝](https://www.testwo.com/)
    *   [TesterHome](https://testerhome.com)

*   运维:
    *   [运维派](http://www.yunweipai.com/)
    *   [Abcdocker](https://www.abcdocker.com/)

*   Java:
    *   [ImportNew](http://www.importnew.com/)
        *   专注于 Java 技术分享
    *   [HowToDoInJava](https://howtodoinjava.com/)
        *   英文博客

*   安全
    *   [红黑联盟](https://www.2cto.com/)
    *   [FreeBuf](http://www.freebuf.com/)

*   大数据
    *   [中国大数据](http://www.thebigdata.cn/)

*   其他专题网站：
    *   [InfoQ](http://www.infoq.com/cn/)
        *   偏重于基础架构、运维方向
    *   [DockerInfo](http://www.dockerinfo.net/)
        *   专注于 Docker 应用及咨询、教程的网站
    *   [Linux公社](https://www.linuxidc.com/)
        *   Linux 主题社区

## 其他类

*   [程序员技能图谱](https://github.com/TeamStuQ/skill-map)

## 推荐参考书

### 在线电子书

*   [《深入理解Spring Cloud与微服务构建》](https://github.com/forezp/SpringCloudLearning)

*   [《阿里技术参考图册-研发篇》](http://techforum-img.cn-hangzhou.oss-pub.aliyun-inc.com/1523849261680/AliTech101_RD.pdf)

*   [《阿里技术参考图册-算法篇》](http://techforum-img.cn-hangzhou.oss-pub.aliyun-inc.com/1523848064814/AliTech101_Algorithms.pdf)

*   [《2018美团点评技术年货（合辑）》70M](http://dpurl.cn/n/1lqcX)

*   [InfoQ《架构师》月刊](http://www.infoq.com/cn/architect/)

*   [《架构师之路》](https://www.w3cschool.cn/architectroad/)

### 纸质书

<b style="color:red">更多架构方面书籍参考:</b> [awesome-java-books](https://github.com/sorenduan/awesome-java-books/blob/master/README.md#%E6%9E%B6%E6%9E%84)

#### 开发方面

*   《阿里巴巴Java开发手册》[详情](https://www.coderxing.com/r.php?r=https://union-click.jd.com/jdc?d=BfL5CR)

#### 架构方面

*   《软件架构师的12项修炼：技术技能篇》[详情](https://www.coderxing.com/r.php?r=https://union-click.jd.com/jdc?d=rTlo0m)

*   《架构之美》[详情](https://www.coderxing.com/r.php?r=https://union-click.jd.com/jdc?d=1KECBZ)

*   《分布式服务架构》[详情](https://www.coderxing.com/r.php?r=https://union-click.jd.com/jdc?d=hkzqtK)

*   《聊聊架构》 [详情](https://www.coderxing.com/r.php?r=https://union-click.jd.com/jdc?d=A8Nd6Z)

*   《云原生应用架构实践》[详情](https://www.coderxing.com/r.php?r=https://union-click.jd.com/jdc?d=D4WCpd)

*   《亿级流量网站架构核心技术》[详情](https://www.coderxing.com/r.php?r=https://union-click.jd.com/jdc?d=Rdmd21)

*   《淘宝技术这十年》[详情](https://www.coderxing.com/r.php?r=https://union-click.jd.com/jdc?d=CoUdGG)

*   《企业IT架构转型之道-中台战略思想与架构实战》 [详情](https://www.coderxing.com/r.php?r=https://union-click.jd.com/jdc?d=BxS6eI)

*   《高可用架构（第1卷）》[详情](https://www.coderxing.com/r.php?r=https://union-click.jd.com/jdc?d=BcjUwS)

#### 技术管理方面

*   《CTO说》[详情](https://www.coderxing.com/r.php?r=https://union-click.jd.com/jdc?d=Gl3QAo)
*   《技术管理之巅》[详情](https://www.coderxing.com/r.php?r=https://union-click.jd.com/jdc?d=MeloLt)
*   《网易一千零一夜：互联网产品项目管理实战》[详情](https://www.coderxing.com/r.php?r=https://union-click.jd.com/jdc?d=qPuqMg)

#### 基础理论

*   《数学之美》[详情](https://www.coderxing.com/r.php?r=https://union-click.jd.com/jdc?d=0seUpO)
*   《编程珠玑》[详情](https://www.coderxing.com/r.php?r=https://union-click.jd.com/jdc?d=I7jj9r)

#### 工具方面

TODO

#### 大数据方面

# 技术资源

## 开源资源

*   [github](https://github.com)

*   [Apache 软件基金会](https://www.apache.org/index.html)

## 手册、文档、教程

**国内：**

*   [W3Cschool](http://w3cschool.cn)

*   [Runoob.com](http://www.runoob.com/)
    *   HTML 、 CSS、XML、Java、Python、PHP、设计模式等入门手册。

*   [Love2.io](https://love2.io/)
    *   很多很多中文在线电子书，是一个全新的开源技术文档分享平台。

*   [gitbook.cn](http://gitbook.cn/)
    *   付费电子书。

*   [ApacheCN](http://www.apachecn.org/)
    *   AI、大数据方面系列中文文档。

**国外：**

*   [Quick Code](http://www.quickcode.co/)
    *   免费在线技术教程。
*   [gitbook.com](http://gitbook.com)
    *   有部分中文电子书。
*   [Cheatography](https://www.cheatography.com/)
    *   Cheat Sheets 大全，单页文档网站。
*   [Tutorialspoint](https://www.tutorialspoint.com/index.htm)
    *   知名教程网站，提供Java、Python、JS、SQL、大数据等高质量入门教程。
*   [LeetCode](https://leetcode.com/problemset/all/)
    *   知名题库网站，提供Java、Python、C#、C++、算法、SQL、等高质量各程度题库和解决办法。

## 在线课堂

*   [学徒无忧](http://www.xuetuwuyou.com/)
*   [极客时间](https://time.geekbang.org/)
*   [segmentfault](https://segmentfault.com/lives)
*   [斯达克学院](https://new.stuq.org/course/explore)
*   [牛客网](http://nowcoder.com)
*   [极客学院](https://www.jikexueyuan.com/)
*   [51CTO学院](http://edu.51cto.com/)

## 会议、活动

*   [QCon](http://www.infoq.com/cn/qcon/)
*   [ArchSummit](https://archsummit.com)
*   [GITC全球互联网技术大会](http://www.thegitc.com/)

**活动发布平台:**

*   [活动行](http://www.huodongxing.com/)

## 常用APP

*   [极客时间](https://time.geekbang.org)
*   [得到](https://www.igetget.com)

## 找工作

*   [Boss直聘](https://www.zhipin.com)
*   [拉勾网](https://www.lagou.com)
*   [猎聘](https://www.liepin.com)
*   [100Offer](https://cn.100offer.com/)

## 工具

*   [极客搜索](https://s.geekbang.org/)
    *   技术文章搜索引擎。

## 代码托管

*   [Coding](https://coding.net)
*   [码云](https://gitee.com/)

## 文件服务

*   七牛
*   又拍云

## 综合云服务商

*   阿里云
*   [腾讯云](https://cloud.tencent.com/redirect.php?redirect=1012\&cps_key=c2665015d90871c0cb20fef91b7afc3c)
*   百度云
*   新浪云
*   金山云
*   [亚马逊云(AWS)](https://amazonaws-china.com/cn/)
*   [谷歌云](https://cloud.google.com/?hl=zh-cn)
*   [微软云](https://azure.microsoft.com/zh-cn/)

### VPS

*   [Linode](http://linode.com)
*   [DigitalOcean](https://www.digitalocean.com)
*   [Vultr](https://www.vultr.com/)

## 入门书籍

*   [《明解Java》](https://www.coderxing.com/r.php?r=https://u.jd.com/TA6z3m) - 豆瓣评分 8.5
*   [《Java从入门到精通（第4版 附光盘）》](https://www.coderxing.com/r.php?r=https://u.jd.com/7urNtH) - 豆瓣评分 6
*   [《入门很简单丛书：Java Web开发入门很简单》](https://www.coderxing.com/r.php?r=https://u.jd.com/2dDnsY)
*   [《程序员炼成记 从小白到工程师》](https://www.coderxing.com/r.php?r=https://u.jd.com/7zm17P)
*   [《Java从小白到大牛》](https://www.coderxing.com/r.php?r=https://u.jd.com/ZCbVjQ)
*   [《JavaWeb项目开发实战入门（全彩版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/mnkAJR)
*   [《Java精彩编程200例（全彩版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/9TGA0S)
*   [《Java轻松学》](https://www.coderxing.com/r.php?r=https://u.jd.com/zMDeI7)
*   [《大话Java：程序设计从入门到精通（含DVD光盘1张）》](https://www.coderxing.com/r.php?r=https://u.jd.com/td3bUo)
*   [《Java语言袖珍指南（第二版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/HOFu01)

## 基础书籍

*   [《Java编程思想（第4版） \[thinking in java\]》](https://www.coderxing.com/r.php?r=https://u.jd.com/ajylTp) - 豆瓣评分 9.1
*   [《Java核心技术 卷I：基础知识（原书第10版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/tp87o1) - 豆瓣评分 8.2
*   [《Java核心技术卷II：高级特性（原书第10版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/fYGMsC) - 豆瓣评分 7.7

### 多线程与并发

*   [《华章专业开发者丛书·Java并发编程实战》](https://www.coderxing.com/r.php?r=https://u.jd.com/ERgtGV) - 豆瓣评分 9.1
*   [《Java多线程编程实战指南（设计模式篇）》](https://www.coderxing.com/r.php?r=https://u.jd.com/XRUB8H) - 豆瓣评分 8.5
*   [《图解Java多线程设计模式》](https://www.coderxing.com/r.php?r=https://u.jd.com/LDOFjh) - 豆瓣评分 8.4
*   [《实战Java高并发程序设计》](https://www.coderxing.com/r.php?r=https://u.jd.com/WXhQuO) - 豆瓣评分 8.3
*   [《Java高并发编程详解：多线程与架构设计》](https://www.coderxing.com/r.php?r=https://u.jd.com/e5tZdf) - 豆瓣评分 7.6
*   [《Java核心技术系列：Java多线程编程核心技术 \[Java Multi-thread Programming\]》](https://www.coderxing.com/r.php?r=https://u.jd.com/5p2KoJ) - 豆瓣评分 5.1
*   [《Java并发编程：核心方法与框架》](https://www.coderxing.com/r.php?r=https://u.jd.com/RQu2W6)
*   [《Java多线程与Socket：实战微服务框架》](https://www.coderxing.com/r.php?r=https://u.jd.com/fkn9NP)
*   [《NIO与Socket编程技术指南》](https://www.coderxing.com/r.php?r=https://u.jd.com/ZwyPCp)
*   [《Java并发编程之美》](https://www.coderxing.com/r.php?r=https://u.jd.com/vB6BA2)
*   [《实战Java高并发程序设计（第2版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/fthTzf)

### 网络编程

*   [《Java网络编程（第四版） \[Java network programming, forth edition\]》](https://www.coderxing.com/r.php?r=https://u.jd.com/osowEq) - 豆瓣评分 7.6

### 数据结构

*   [《数据结构与算法分析：Java语言描述（原书第3版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/wdrJls) - 豆瓣评分 8.3
*   [《图解数据结构：使用Java》](https://www.coderxing.com/r.php?r=https://u.jd.com/9GKS26)
*   [《数据结构与算法Java语言描述》](https://www.coderxing.com/r.php?r=https://u.jd.com/DCJzy6)

### 语言基础

*   [《Java 8实战》](https://www.coderxing.com/r.php?r=https://u.jd.com/MNwLHg) - 豆瓣评分 9.2
*   [《Java函数式编程》](https://www.coderxing.com/r.php?r=https://u.jd.com/M6XqLp) - 豆瓣评分 8.9
*   [《Java编程的逻辑》](https://www.coderxing.com/r.php?r=https://u.jd.com/YApFXv) - 豆瓣评分 8.9
*   [《O'Reilly：Head First Java（中文版 第2版 涵盖Java5.0）》](https://www.coderxing.com/r.php?r=https://u.jd.com/UZgI0F) - 豆瓣评分 8.7
*   [《写给大忙人看的Java核心技术》](https://www.coderxing.com/r.php?r=https://u.jd.com/ZCMWOr) - 豆瓣评分 7.1
*   [《精通lambda表达式：Java多核编程 \[Mastering Lambdas: Java Programming in a Multicore\]》](https://www.coderxing.com/r.php?r=https://u.jd.com/ajoGad)
*   [《Java 9模块化开发：核心原则与实践》](https://www.coderxing.com/r.php?r=https://u.jd.com/5HXsKg)
*   [《Java JDK 9学习笔记》](https://www.coderxing.com/r.php?r=https://u.jd.com/l7fy1C)
*   [《Java 9编程参考官方大全（第10版） \[Java：Thte Complete Reference，Tenth Edition\]》](https://www.coderxing.com/r.php?r=https://u.jd.com/CqmtBM)
*   [《写给大忙人的Java SE 9核心技术》](https://www.coderxing.com/r.php?r=https://u.jd.com/JMdy64)

## 进阶

*   [《深入分析Java Web技术内幕（修订版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/MBhyO7) - 豆瓣评分 7.5
*   [《Java RESTful Web Service实战（第2版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/GEdlD0)

### 性能优化

*   [《Java性能优化权威指南 \[Java performance\]》](https://www.coderxing.com/r.php?r=https://u.jd.com/qTFNCP) - 豆瓣评分 8.4
*   [《Java程序性能优化：让你的Java程序更快、更稳定》](https://www.coderxing.com/r.php?r=https://u.jd.com/6CYRQi) - 豆瓣评分 8.1
*   [《Java性能权威指南》](https://www.coderxing.com/r.php?r=https://u.jd.com/KmJo2x) - 豆瓣评分 8.1
*   [《51CTO学院系列丛书·实战Java虚拟机：JVM故障诊断与性能优化》](https://www.coderxing.com/r.php?r=https://u.jd.com/GKe55M) - 豆瓣评分 8
*   [《Java性能调优指南》](https://www.coderxing.com/r.php?r=https://u.jd.com/sQPN8w) - 豆瓣评分 7
*   [《大话Java性能优化》](https://www.coderxing.com/r.php?r=https://u.jd.com/Uqaj5n) - 豆瓣评分 4.4

### 响应式编程

*   [《响应式架构：消息模式Actor实现与Scala、Akka应用集成》](https://www.coderxing.com/r.php?r=https://u.jd.com/nvsfLb) - 豆瓣评分 8.1
*   [《RxJava响应式编程》](https://www.coderxing.com/r.php?r=https://u.jd.com/HeIp16)
*   [《RxJava 2.x 实战》](https://www.coderxing.com/r.php?r=https://u.jd.com/iIZc0A)

### JVM虚拟机

*   [《深入理解Java虚拟机：JVM高级特性与最佳实践（第2版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/DgTnN2) - 豆瓣评分 8.9
*   [《Java核心技术系列：Java虚拟机规范（Java SE 8版） \[The Java Virtual Machine Specification Jave SE 8 Edition\]》](https://www.coderxing.com/r.php?r=https://u.jd.com/73DIJB) - 豆瓣评分 8.3
*   [《揭秘Java虚拟机：JVM设计原理与实现》](https://www.coderxing.com/r.php?r=https://u.jd.com/ct4KRw) - 豆瓣评分 7.9
*   [《HotSpot实战》](https://www.coderxing.com/r.php?r=https://u.jd.com/xJZjRH) - 豆瓣评分 7.1
*   [《Java从入门到动手写虚拟机1（套装共2册）》](https://www.coderxing.com/r.php?r=https://u.jd.com/0ZMjqZ)

### 代码&设计优化

*   [《重构 改善既有代码的设计 Java语言版》](https://www.coderxing.com/r.php?r=https://u.jd.com/QSoCEv) - 豆瓣评分 9.3
*   [《代码大全（第2版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/wxQc3i) - 豆瓣评分 9.3
*   [《Effective Java中文版（原书第3版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/syzAFD) - 豆瓣评分 9
*   [《代码整洁之道 程序员的职业素养》](https://www.coderxing.com/r.php?r=https://u.jd.com/Rt31CM) - 豆瓣评分 8.8
*   [《代码整洁之道 \[Clean Code A Handbook of Agile Software Craftsmanship\]》](https://www.coderxing.com/r.php?r=https://u.jd.com/XBQxz8) - 豆瓣评分 8.6
*   [《Spring实战（第4版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/ld8p0r) - 豆瓣评分 8.3
*   [《代码不朽：编写可维护软件的10大要则（Java版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/0hnAnw) - 豆瓣评分 7
*   [《Java代码与架构之完美优化 实战经典》](https://www.coderxing.com/r.php?r=https://u.jd.com/tyYWro)

## 设计模式

*   [《反应式设计模式》](https://www.coderxing.com/r.php?r=https://u.jd.com/SJWtpV) - 豆瓣评分 9.3
*   [《O'Reilly：Head First设计模式（中文版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/IGKmVq) - 豆瓣评分 9.2
*   [《设计模式：可复用面向对象软件的基础》](https://www.coderxing.com/r.php?r=https://u.jd.com/D59mge) - 豆瓣评分 9.1
*   [《实现领域驱动设计 \[Implementing Domain-Driven Design\]》](https://www.coderxing.com/r.php?r=https://u.jd.com/lFwQdc) - 豆瓣评分 8.7
*   [《原创精品系列：设计模式之禅（第2版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/yxTBEJ) - 豆瓣评分 8.7
*   [《图解设计模式》](https://www.coderxing.com/r.php?r=https://u.jd.com/H9tRFl) - 豆瓣评分 8.7
*   [《大话设计模式》](https://www.coderxing.com/r.php?r=https://u.jd.com/qfAaGS) - 豆瓣评分 8.3
*   [《领域驱动设计 软件核心复杂性应对之道 修订版》](https://www.coderxing.com/r.php?r=https://u.jd.com/PllZtF) - 豆瓣评分 8
*   [《Java测试驱动开发》](https://www.coderxing.com/r.php?r=https://u.jd.com/xRo8Ur) - 豆瓣评分 6.6

## 框架与中间件

### 数据库

*   [《高性能MySQL（第3版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/i4KCQO) - 豆瓣评分 9.3
*   [《MySQL技术内幕：InnoDB存储引擎（第2版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/Th90ra) - 豆瓣评分 8.6
*   [《大型网站系统与Java中间件实践》](https://www.coderxing.com/r.php?r=https://u.jd.com/YivOvQ) - 豆瓣评分 7.9
*   [《深入浅出MySQL 数据库开发 优化与管理维护 第2版》](https://www.coderxing.com/r.php?r=https://u.jd.com/HjaHc2) - 豆瓣评分 7.5
*   [《PostgreSQL修炼之道：从小工到专家》](https://www.coderxing.com/r.php?r=https://u.jd.com/oYHlHw) - 豆瓣评分 7.3
*   [《PostgreSQL技术内幕：查询优化深度探索》](https://www.coderxing.com/r.php?r=https://u.jd.com/hKsMRX)

### 缓存与NoSQL

*   [《Redis 深度历险：核心原理与应用实践》](https://www.coderxing.com/r.php?r=https://u.jd.com/uZirI6) - 豆瓣评分 9
*   [《Redis实战》](https://www.coderxing.com/r.php?r=https://u.jd.com/VMo7w2) - 豆瓣评分 8
*   [《Redis入门指南（第2版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/GmFr7B) - 豆瓣评分 7.6
*   [《深入分布式缓存：从原理到实践》](https://www.coderxing.com/r.php?r=https://u.jd.com/TKeCR2) - 豆瓣评分 7.1
*   [《人人都是架构师：分布式系统架构落地与瓶颈突破》](https://www.coderxing.com/r.php?r=https://u.jd.com/8DuE9W) - 豆瓣评分 6.7
*   [《MongoDB应用设计模式》](https://www.coderxing.com/r.php?r=https://u.jd.com/qd9tLA) - 豆瓣评分 6.1
*   [《MongoDB实战 架构、开发与管理》](https://www.coderxing.com/r.php?r=https://u.jd.com/Mlefug)
*   [《NoSQL数据库入门与实践（基于MongoDB、Redis）》](https://www.coderxing.com/r.php?r=https://u.jd.com/1QhhB6)

### 消息队列

*   [《RabbitMQ实战指南》](https://www.coderxing.com/r.php?r=https://u.jd.com/4SyxGo) - 豆瓣评分 9.1
*   [《Kafka权威指南》](https://www.coderxing.com/r.php?r=https://u.jd.com/qIwmGY) - 豆瓣评分 8.9
*   [《Kafka入门与实践》](https://www.coderxing.com/r.php?r=https://u.jd.com/hqBGgy) - 豆瓣评分 7.7
*   [《RocketMQ实战与原理解析》](https://www.coderxing.com/r.php?r=https://u.jd.com/vyU3eK) - 豆瓣评分 7.2
*   [《Kafka技术内幕 图文详解Kafka源码设计与实现》](https://www.coderxing.com/r.php?r=https://u.jd.com/GZh0yK) - 豆瓣评分 6.9
*   [《深入理解Kafka：核心设计与实践原理》](https://www.coderxing.com/r.php?r=https://u.jd.com/sTtFQn)
*   [《分布式消息中间件实践》](https://www.coderxing.com/r.php?r=https://u.jd.com/GzBNOZ)

### ORM框架

*   [《MyBatis从入门到精通》](https://www.coderxing.com/r.php?r=https://u.jd.com/0GXsRh) - 豆瓣评分 7.7

### Spring家族

*   [《Spring微服务实战》](https://www.coderxing.com/r.php?r=https://u.jd.com/ohN8uh) - 豆瓣评分 8.3
*   [《Spring Cloud微服务实战》](https://www.coderxing.com/r.php?r=https://u.jd.com/z1QvAP) - 豆瓣评分 7.9
*   [《深入理解Spring Cloud与微服务构建》](https://www.coderxing.com/r.php?r=https://u.jd.com/FfCbxt) - 豆瓣评分 7.7
*   [《MyBatis技术内幕》](https://www.coderxing.com/r.php?r=https://u.jd.com/wAPeEw) - 豆瓣评分 7.6
*   [《Spring Boot实战》](https://www.coderxing.com/r.php?r=https://u.jd.com/BcQznU) - 豆瓣评分 7.2
*   [《深入浅出Spring Boot 2.x》](https://www.coderxing.com/r.php?r=https://u.jd.com/k0xgoA) - 豆瓣评分 7
*   [《JavaEE开发的颠覆者：Spring Boot实战》](https://www.coderxing.com/r.php?r=https://u.jd.com/4Rtvg3) - 豆瓣评分 6.3
*   [《Spring技术内幕：深入解析Spring架构与设计原理（第2版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/2rz8BY) - 豆瓣评分 5.9
*   [《Spring Boot 2精髓：从构建小系统到架构分布式大系统》](https://www.coderxing.com/r.php?r=https://u.jd.com/xrNcv1) - 豆瓣评分 4.8
*   [《Spring 5开发大全》](https://www.coderxing.com/r.php?r=https://u.jd.com/dtDOqc)
*   [《Spring Cloud微服务架构进阶》](https://www.coderxing.com/r.php?r=https://u.jd.com/oFsaYt)
*   [《Spring源码深度解析 第2版》](https://www.coderxing.com/r.php?r=https://u.jd.com/SdhhtK)
*   [《Spring MVC实战》](https://www.coderxing.com/r.php?r=https://u.jd.com/ghc04R)
*   [《Spring Boot编程思想（核心篇）（限量版亲笔签名书签 随机发售）》](https://www.coderxing.com/r.php?r=https://u.jd.com/fCZpVU)
*   [《互联网轻量级SSM框架解密：Spring、Spring MVC、MyBatis源码深度剖析》](https://www.coderxing.com/r.php?r=https://u.jd.com/HO244A)
*   [《Spring学习指南 第3版》](https://www.coderxing.com/r.php?r=https://u.jd.com/O9L5Nb)
*   [《精通Spring MVC 4》](https://www.coderxing.com/r.php?r=https://u.jd.com/k4WSg3)

### 高并发

*   [《Netty实战》](https://www.coderxing.com/r.php?r=https://u.jd.com/htIJgi) - 豆瓣评分 7.8
*   [《七周七并发模型》](https://www.coderxing.com/r.php?r=https://u.jd.com/81Pbod) - 豆瓣评分 7.8
*   [《Netty权威指南（第2版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/7tGXx5) - 豆瓣评分 6.9
*   [《Netty进阶之路：跟着案例学Netty》](https://www.coderxing.com/r.php?r=https://u.jd.com/VBYLE0)

### 分布式

*   [《从Paxos到Zookeeper分布式一致性原理与实践》](https://www.coderxing.com/r.php?r=https://u.jd.com/3rp1Hv) - 豆瓣评分 7.8
*   [《ZooKeeper：分布式过程协同技术详解》](https://www.coderxing.com/r.php?r=https://u.jd.com/LAyupw) - 豆瓣评分 7.2

### 搜索引擎

*   [《从Lucene到Elasticsearch：全文检索实战》](https://www.coderxing.com/r.php?r=https://u.jd.com/IdftoH)

### 大数据

*   [《Hadoop权威指南：大数据的存储与分析(第4版)》](https://www.coderxing.com/r.php?r=https://u.jd.com/BlEDc7) - 豆瓣评分 8.7
*   [《Hadoop构建数据仓库实践》](https://www.coderxing.com/r.php?r=https://u.jd.com/dW1kpa) - 豆瓣评分 8.3
*   [《HBase权威指南 \[HBase： The Definitive Guide\]》](https://www.coderxing.com/r.php?r=https://u.jd.com/wqb9z0) - 豆瓣评分 8.1
*   [《图解Spark：核心技术与案例实战》](https://www.coderxing.com/r.php?r=https://u.jd.com/azPD8S) - 豆瓣评分 7.6
*   [《Hive编程指南 \[Programming Hive\]》](https://www.coderxing.com/r.php?r=https://u.jd.com/bd1YCS) - 豆瓣评分 7.4
*   [《HBase应用架构》](https://www.coderxing.com/r.php?r=https://u.jd.com/kFRuj2)

## 架构

*   [《Web性能权威指南》](https://www.coderxing.com/r.php?r=https://u.jd.com/pTZ8xk) - 豆瓣评分 8.8
*   [《从零开始学架构：照着做，你也能成为架构师》](https://www.coderxing.com/r.php?r=https://u.jd.com/7tOuAz) - 豆瓣评分 8.5
*   [《Java应用架构设计：模块化模式与OSGi》](https://www.coderxing.com/r.php?r=https://u.jd.com/Qs9SXn) - 豆瓣评分 6.9
*   [《大型网站技术架构演进与性能优化》](https://www.coderxing.com/r.php?r=https://u.jd.com/GVYZr9) - 豆瓣评分 6.8
*   [《高可用架构（第1卷）》](https://www.coderxing.com/r.php?r=https://u.jd.com/7y5NpR) - 豆瓣评分 6.3
*   [《Java架构师指南》](https://www.coderxing.com/r.php?r=https://u.jd.com/kPGIoj)
*   [《大话代码架构（项目实战版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/Bc2TLN)
*   [《小团队构建大网站：中小研发团队架构实践》](https://www.coderxing.com/r.php?r=https://u.jd.com/mzqn7f)
*   [《未来架构 从服务化到云原生(限量签名 随机发放)》](https://www.coderxing.com/r.php?r=https://u.jd.com/zDMNQs)

### 分布式架构

*   [《可伸缩架构：面向增长应用的高可用》](https://www.coderxing.com/r.php?r=https://u.jd.com/zpE3MI) - 豆瓣评分 7.4
*   [《分布式服务架构：原理、设计与实战》](https://www.coderxing.com/r.php?r=https://u.jd.com/HQHcMY) - 豆瓣评分 7.2
*   [《亿级流量网站架构核心技术 跟开涛学搭建高可用高并发系统》](https://www.coderxing.com/r.php?r=https://u.jd.com/9JXTi8) - 豆瓣评分 6.6
*   [《大型分布式网站架构设计与实践》](https://www.coderxing.com/r.php?r=https://u.jd.com/zzctjK) - 豆瓣评分 6.2
*   [《可伸缩服务架构：框架与中间件》](https://www.coderxing.com/r.php?r=https://u.jd.com/l4UA35) - 豆瓣评分 5.9
*   [《架构探险：从零开始写分布式服务框架》](https://www.coderxing.com/r.php?r=https://u.jd.com/1YUJxK) - 豆瓣评分 5.9
*   [《Cloud Native分布式架构原理与实践》](https://www.coderxing.com/r.php?r=https://u.jd.com/4trb76)
*   [《分布式系统常用技术及案例分析（第2版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/QWumiy)
*   [《云原生Java：Spring Boot、Spring Cloud与Cloud Foundry弹性系统设计》](https://www.coderxing.com/r.php?r=https://u.jd.com/53hDaR)

### 微服务架构

*   [《微服务设计》](https://www.coderxing.com/r.php?r=https://u.jd.com/5KB81a) - 豆瓣评分 8.2
*   [《生产微服务》](https://www.coderxing.com/r.php?r=https://u.jd.com/LF3vzd) - 豆瓣评分 8
*   [《架构解密：从分布式到微服务》](https://www.coderxing.com/r.php?r=https://u.jd.com/xoCkW1) - 豆瓣评分 5.8
*   [《Java微服务》](https://www.coderxing.com/r.php?r=https://u.jd.com/jk1V1F) - 豆瓣评分 5.3
*   [《Spring Cloud 微服务架构开发实战（全新升级版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/QvfyPI)
*   [《微服务实践》](https://www.coderxing.com/r.php?r=https://u.jd.com/DyZQbc)

### 架构方法论

*   [《架构整洁之道》](https://www.coderxing.com/r.php?r=https://u.jd.com/k8yxj0) - 豆瓣评分 8.8
*   [《企业应用架构模式 \[Patterns of Enterprise Application Architecture\]》](https://www.coderxing.com/r.php?r=https://u.jd.com/pQOd7z) - 豆瓣评分 8.3
*   [《企业IT架构转型之道 阿里巴巴中台战略思想与架构实战》](https://www.coderxing.com/r.php?r=https://u.jd.com/ipHhzt) - 豆瓣评分 8.2
*   [《聊聊“架构”》](https://www.coderxing.com/r.php?r=https://u.jd.com/jRMw2b) - 豆瓣评分 7.6
*   [《架构真经：互联网技术架构的设计原则（原书第2版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/1gr9nd) - 豆瓣评分 7.5
*   [《软件架构设计：程序员向架构师转型必备（第2版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/4Y77J0) - 豆瓣评分 7.4
*   [《恰如其分的软件架构 \[Just Enough Software Architecture\]》](https://www.coderxing.com/r.php?r=https://u.jd.com/XOr8py) - 豆瓣评分 7.3
*   [《软件架构设计：大型网站技术架构与业务架构融合之道》](https://www.coderxing.com/r.php?r=https://u.jd.com/lSUYn8)

## JVM周边语言

*   [《Scala编程（第3版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/R0JT1a) - 豆瓣评分 9.4
*   [《Groovy程序设计》](https://www.coderxing.com/r.php?r=https://u.jd.com/AMZkGX) - 豆瓣评分 8.2
*   [《快学Scala（第2版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/h6Gnct) - 豆瓣评分 8
*   [《Kotlin极简教程》](https://www.coderxing.com/r.php?r=https://u.jd.com/loJfwO)
*   [《Scala集合技术手册》](https://www.coderxing.com/r.php?r=https://u.jd.com/WvMNgs)

## 项目管理&领导力&流程

*   [《构建之法 现代软件工程（第三版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/5OmcTI) - 豆瓣评分 9
*   [《精益思想（白金版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/gcHfSY) - 豆瓣评分 8.2
*   [《给产品经理讲技术》](https://www.coderxing.com/r.php?r=https://u.jd.com/uZ2nZV)

### 项目管理

*   [《持续交付：发布可靠软件的系统方法》](https://www.coderxing.com/r.php?r=https://u.jd.com/TzKtiz) - 豆瓣评分 8.7
*   [《名家经典系列：人件（原书第3版） \[Peopleware: Productive Projects and Teams\]》](https://www.coderxing.com/r.php?r=https://u.jd.com/qEOLhm) - 豆瓣评分 8.4
*   [《硝烟中的Scrum和XP：我们如何实施Scrum》](https://www.coderxing.com/r.php?r=https://u.jd.com/gc719a) - 豆瓣评分 8.4
*   [《敏捷软件开发实践 估算与计划》](https://www.coderxing.com/r.php?r=https://u.jd.com/ZHeyFS) - 豆瓣评分 8.4
*   [《人月神话（40周年中文纪念版） \[The Mythical Man-Month：Essays on Software Engineering Anniversary Edition\]》](https://www.coderxing.com/r.php?r=https://u.jd.com/mUkwcD) - 豆瓣评分 8.3
*   [《Scrum敏捷软件开发》](https://www.coderxing.com/r.php?r=https://u.jd.com/T9HSMS) - 豆瓣评分 8
*   [《用户故事与敏捷方法 \[User Stories Applied:For Agile Software Development\]》](https://www.coderxing.com/r.php?r=https://u.jd.com/D8oZoG) - 豆瓣评分 8
*   [《用户故事地图 \[User Story Mapping\]》](https://www.coderxing.com/r.php?r=https://u.jd.com/P6RDR3) - 豆瓣评分 7.4
*   [《知行合一 实现价值驱动的敏捷和精益开发》](https://www.coderxing.com/r.php?r=https://u.jd.com/1zgjNd)
*   [《互联网项目管理实践精粹》](https://www.coderxing.com/r.php?r=https://u.jd.com/Dtrvqn)

### 团队管理

*   [《卓有成效的管理者（珍藏版） \[The Effective Executive\]》](https://www.coderxing.com/r.php?r=https://u.jd.com/f2kMe8) - 豆瓣评分 8.8
*   [《跃迁：从技术到管理的硅谷路径》](https://www.coderxing.com/r.php?r=https://u.jd.com/xLBU9J) - 豆瓣评分 8.4
*   [《告别失控 软件开发团队管理必读》](https://www.coderxing.com/r.php?r=https://u.jd.com/w4p97S) - 豆瓣评分 7.9
*   [《赋能：打造应对不确定性的敏捷团队 \[Team of Teams\]》](https://www.coderxing.com/r.php?r=https://u.jd.com/K5DiJn) - 豆瓣评分 7.6
*   [《OKR工作法：谷歌、领英等顶级公司的高绩效秘籍 \[Radical Focus\]》](https://www.coderxing.com/r.php?r=https://u.jd.com/8Gsrin) - 豆瓣评分 7.6
*   [《CTO说》](https://www.coderxing.com/r.php?r=https://u.jd.com/PchUJJ) - 豆瓣评分 7.3
*   [《轻流程 IT团队的积分式绩效管理》](https://www.coderxing.com/r.php?r=https://u.jd.com/wGQe5I) - 豆瓣评分 7
*   [《技术领导力：程序员如何才能带团队》](https://www.coderxing.com/r.php?r=https://u.jd.com/spqdp1) - 豆瓣评分 5.4
*   [《敏捷文化：如何打造优秀的高效能团队 \[The Agile Culture: Leading through Trust and Owner\]》](https://www.coderxing.com/r.php?r=https://u.jd.com/pSHHhA)

## 数学与算法

### 数学

*   [《数学之美（第二版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/lcuOQq) - 豆瓣评分 8.9
*   [《程序员的数学2 概率统计》](https://www.coderxing.com/r.php?r=https://u.jd.com/Yte3WW) - 豆瓣评分 8.7
*   [《程序员的数学3 线性代数》](https://www.coderxing.com/r.php?r=https://u.jd.com/WiKN9k) - 豆瓣评分 8.6
*   [《程序员的数学》](https://www.coderxing.com/r.php?r=https://u.jd.com/iwv4Zd) - 豆瓣评分 7.2
*   [《程序员的数学思维修炼（趣味解读）》](https://www.coderxing.com/r.php?r=https://u.jd.com/qhD5IJ) - 豆瓣评分 5.4
*   [《统计之美：人工智能时代的科学思维》](https://www.coderxing.com/r.php?r=https://u.jd.com/vBLDyU)
*   [《统计思维：程序员数学之概率统计（第2版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/iCEv9a)

### 算法

*   [《算法导论（原书第3版）/计算机科学丛书 \[Introduction to Algorithms, third edition\]》](https://www.coderxing.com/r.php?r=https://u.jd.com/AmwANr) - 豆瓣评分 9.3
*   [《算法图解》](https://www.coderxing.com/r.php?r=https://u.jd.com/J7HWa6) - 豆瓣评分 8.4
*   [《漫画算法：小灰的算法之旅（全彩）》](https://www.coderxing.com/r.php?r=https://u.jd.com/Jt8KBI)

## 职业素养与个人成长

*   [《我编程，我快乐：程序员职业规划之道》](https://www.coderxing.com/r.php?r=https://u.jd.com/DGNxfn) - 豆瓣评分 7.9
*   [《程序员的自我修养》](https://www.coderxing.com/r.php?r=https://u.jd.com/THQJSq) - 豆瓣评分 6.5

### 职业素养提升

*   [《码农翻身：用故事给技术加点料》](https://www.coderxing.com/r.php?r=https://u.jd.com/J7iABA) - 豆瓣评分 9.1
*   [《程序员修炼之道：从小工到专家》](https://www.coderxing.com/r.php?r=https://u.jd.com/TL272C) - 豆瓣评分 8.8
*   [《极客与团队：软件工程师的团队生存秘笈》](https://www.coderxing.com/r.php?r=https://u.jd.com/mAbLoA) - 豆瓣评分 8.3
*   [《程序员思维修炼(修订版)》](https://www.coderxing.com/r.php?r=https://u.jd.com/8l5o8l) - 豆瓣评分 8.2
*   [《高效能程序员的修炼》](https://www.coderxing.com/r.php?r=https://u.jd.com/s1OiZc) - 豆瓣评分 8.2
*   [《O'Reilly：卓有成效的程序员 \[Productive programmer\]》](https://www.coderxing.com/r.php?r=https://u.jd.com/XxVx3J) - 豆瓣评分 8.1
*   [《Java工程师修炼之道》](https://www.coderxing.com/r.php?r=https://u.jd.com/ODjq2h) - 豆瓣评分 7.8
*   [《程序员的成长课》](https://www.coderxing.com/r.php?r=https://u.jd.com/DKrbwc) - 豆瓣评分 7.6
*   [《高效程序员的45个习惯：敏捷开发修炼之道(修订版)》](https://www.coderxing.com/r.php?r=https://u.jd.com/y36OqE) - 豆瓣评分 7.6
*   [《温伯格技术思想三部曲：颠覆完美软件 软件测试必须知道的几件事》](https://www.coderxing.com/r.php?r=https://u.jd.com/JKgll1) - 豆瓣评分 7.5
*   [《温伯格技术思想三部曲：程序开发心理学（银年纪念版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/0K8XDo) - 豆瓣评分 7.4
*   [《软件开发本质论：追求简约、体现价值、逐步构建》](https://www.coderxing.com/r.php?r=https://u.jd.com/AlxMcW) - 豆瓣评分 7.3
*   [《内外兼修：程序员的成长之路》](https://www.coderxing.com/r.php?r=https://u.jd.com/W0uA76) - 豆瓣评分 6.6

### 个人软技能

*   [《把时间当作朋友（第3版 全彩）》](https://www.coderxing.com/r.php?r=https://u.jd.com/I3D7Z0) - 豆瓣评分 8.5
*   [《暗时间》](https://www.coderxing.com/r.php?r=https://u.jd.com/GZgwi5) - 豆瓣评分 8.4
*   [《关键对话：如何高效能沟通（原书第2版） \[Crucial Conversations: Tools for Talking When Stak\]》](https://www.coderxing.com/r.php?r=https://u.jd.com/jpIkyt) - 豆瓣评分 8.1
*   [《温伯格技术思想三部曲：成为技术领导者 掌握全面解决问题的方法》](https://www.coderxing.com/r.php?r=https://u.jd.com/N6YwQD) - 豆瓣评分 8
*   [《软技能 代码之外的生存指南》](https://www.coderxing.com/r.php?r=https://u.jd.com/KkL3kA) - 豆瓣评分 8
*   [《程序员健康指南》](https://www.coderxing.com/r.php?r=https://u.jd.com/8YQH5T) - 豆瓣评分 7.5
*   [《如何把事情做到最好：改变全球9800万人的人生指导书 \[Mastery\]》](https://www.coderxing.com/r.php?r=https://u.jd.com/NS6cLf) - 豆瓣评分 7.2
*   [《程序员的英语》](https://www.coderxing.com/r.php?r=https://u.jd.com/Gt5VDT) - 豆瓣评分 5.9
*   [《高效能人士的七个习惯（30周年纪念版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/oG641c)

## 大厂出品

### 阿里巴巴技术丛书

*   [《码出高效：Java开发手册》](https://www.coderxing.com/r.php?r=https://u.jd.com/mIi1ic) - 豆瓣评分 8.8
*   [《大数据之路 阿里巴巴大数据实践》](https://www.coderxing.com/r.php?r=https://u.jd.com/4888rh) - 豆瓣评分 7.8
*   [《技术之瞳 阿里巴巴技术笔试心得》](https://www.coderxing.com/r.php?r=https://u.jd.com/xHqHfG) - 豆瓣评分 7.7
*   [《淘宝技术这十年》](https://www.coderxing.com/r.php?r=https://u.jd.com/uZYvrV) - 豆瓣评分 7.3
*   [《尽在双11 阿里巴巴技术演进与超越》](https://www.coderxing.com/r.php?r=https://u.jd.com/VA9xEV) - 豆瓣评分 7.1
*   [《逆流而上：阿里巴巴技术成长之路》](https://www.coderxing.com/r.php?r=https://u.jd.com/5NdzxY) - 豆瓣评分 6.9

### 京东技术丛书

*   [《京东基础架构建设之路（全彩）》](https://www.coderxing.com/r.php?r=https://u.jd.com/ET1NkI) - 豆瓣评分 6.2
*   [《京东系统质量保障技术实战》](https://www.coderxing.com/r.php?r=https://u.jd.com/0OOBCc) - 豆瓣评分 6.1
*   [《京东技术解密》](https://www.coderxing.com/r.php?r=https://u.jd.com/V6tLFs) - 豆瓣评分 6.1

## 工具书

*   [《Linux命令行与shell脚本编程大全（第3版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/5U9zkK) - 豆瓣评分 9.1
*   [《阿里巴巴Java开发手册》](https://www.coderxing.com/r.php?r=https://u.jd.com/28U5lx) - 豆瓣评分 8.3
*   [《SQL即查即用 （全彩版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/d5ADPR)
*   [《Linux命令速查手册（第三版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/VgrIgv)

## 面试求职

*   [《剑指Offer：名企面试官精讲典型编程题（第2版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/IgfC55) - 豆瓣评分 9.1
*   [《编程之美：微软技术面试心得》](https://www.coderxing.com/r.php?r=https://u.jd.com/E4WimD) - 豆瓣评分 8.4
*   [《Java程序员面试笔试宝典》](https://www.coderxing.com/r.php?r=https://u.jd.com/UqcYlU) - 豆瓣评分 7.6
*   [《Java程序员面试宝典（第4版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/tm79JE) - 豆瓣评分 5
*   [《编程之法：面试和算法心得》](https://www.coderxing.com/r.php?r=https://u.jd.com/7ujWIz)
*   [《Java程序员面试算法宝典》](https://www.coderxing.com/r.php?r=https://u.jd.com/eE9uWg)
*   [《Java程序员面试笔试真题库》](https://www.coderxing.com/r.php?r=https://u.jd.com/Jc9Xlt)
*   [《Java程序员面试笔试真题与解析》](https://www.coderxing.com/r.php?r=https://u.jd.com/VqoEj5)
*   [《Java核心技术及面试指南》](https://www.coderxing.com/r.php?r=https://u.jd.com/pfIsU6)
*   [《解忧程序员：高薪编程、求职面试与成长转型宝典》](https://www.coderxing.com/r.php?r=https://u.jd.com/j0XMdh)

## 格局与视野

*   [《全球科技通史》](https://www.coderxing.com/r.php?r=https://u.jd.com/bgG9yE) - 豆瓣评分 9.4
*   [《浪潮之巅 第三版 套装上下册》](https://www.coderxing.com/r.php?r=https://u.jd.com/koCTxD) - 豆瓣评分 9.3
*   [《黑客与画家：硅谷创业之父Paul Graham文集 \[Hackers and Painters Big Ldeas From the Computer Age\]》](https://www.coderxing.com/r.php?r=https://u.jd.com/KbwmLQ) - 豆瓣评分 8.8
*   [《软件随想录 卷1》](https://www.coderxing.com/r.php?r=https://u.jd.com/EcKZym) - 豆瓣评分 8.8
*   [《软件随想录 卷2》](https://www.coderxing.com/r.php?r=https://u.jd.com/px8Sgu) - 豆瓣评分 8.7
*   [《编程人生：15位软件先驱访谈录》](https://www.coderxing.com/r.php?r=https://u.jd.com/6jRwgY) - 豆瓣评分 8.5
*   [《大教堂与集市（最新版） \[The Cathedral & the Bazaar\]》](https://www.coderxing.com/r.php?r=https://u.jd.com/6Y4Mcd) - 豆瓣评分 8.4
*   [《硅谷之谜：浪潮之巅 续集》](https://www.coderxing.com/r.php?r=https://u.jd.com/3yyV1D) - 豆瓣评分 8.4
*   [《原则 \[Principles\]》](https://www.coderxing.com/r.php?r=https://u.jd.com/M7OrgY) - 豆瓣评分 8.4
*   [《精益创业》](https://www.coderxing.com/r.php?r=https://u.jd.com/PxHueV) - 豆瓣评分 8.4
*   [《态度：吴军博士新书》](https://www.coderxing.com/r.php?r=https://u.jd.com/rdipjJ) - 豆瓣评分 8.1
*   [《见识》](https://www.coderxing.com/r.php?r=https://u.jd.com/cP4xDs) - 豆瓣评分 8.1
*   [《极限创新 35岁之前改变世界的全球科技精英》](https://www.coderxing.com/r.php?r=https://u.jd.com/oGJFTx) - 豆瓣评分 7.3
*   [《大学的终结：泛在大学与高等教育革命》](https://www.coderxing.com/r.php?r=https://u.jd.com/FBINiB) - 豆瓣评分 7.2
*   [《未来版图 全球聪明公司的科技创新趋势和商业化路径》](https://www.coderxing.com/r.php?r=https://u.jd.com/ZfHw4B) - 豆瓣评分 7.1
*   [《你好哇，程序员——漫话程序员面试求职、升职加薪、创业与生活》](https://www.coderxing.com/r.php?r=https://u.jd.com/cNCbEF) - 豆瓣评分 6.5
*   [《图灵和ACM图灵奖（1966-2015 第五版） 纪念计算机诞生70周年》](https://www.coderxing.com/r.php?r=https://u.jd.com/S1ZQhz)
*   [《文明之光（全彩印刷套装1-4册）入选2014中国好书/第六届中华优秀出版物获奖图书》](https://www.coderxing.com/r.php?r=https://u.jd.com/M3PkIU)
*   [《大师访谈录：成就非凡的软件人生》](https://www.coderxing.com/r.php?r=https://u.jd.com/JHxmei)

## Java之外

*   [《计算机科学丛书：计算机程序的构造和解释（原书第2版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/RCgC9H) - 豆瓣评分 9.5
*   [《计算机科学丛书：编译原理（第2版） \[Compilers:Principle,Techniques and Tools\]》](https://www.coderxing.com/r.php?r=https://u.jd.com/URRIW5) - 豆瓣评分 9.1
*   [《一个APP的诞生——从零开始设计你的手机应用》](https://www.coderxing.com/r.php?r=https://u.jd.com/fbemS8) - 豆瓣评分 6.3
*   [《大型网站性能优化实战：从前端、网络、CDN到后端、大促的全链路性能优化详解》](https://www.coderxing.com/r.php?r=https://u.jd.com/F4SUYQ)

### 网络知识

*   [《图解HTTP》](https://www.coderxing.com/r.php?r=https://u.jd.com/q3lNRK) - 豆瓣评分 8.1
*   [《图解TCP/IP 第5版》](https://www.coderxing.com/r.php?r=https://u.jd.com/Ip1U7X) - 豆瓣评分 7.8

### 安全知识

*   [《白帽子讲Web安全（纪念版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/6oCOp8) - 豆瓣评分 7.4
*   [《Web安全攻防：渗透测试实战指南》](https://www.coderxing.com/r.php?r=https://u.jd.com/gecmeS)

### 工具

*   [《Maven实战》](https://www.coderxing.com/r.php?r=https://u.jd.com/Fv9ksZ) - 豆瓣评分 8.2
*   [《大象：Thinking in UML（第2版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/JvxLfz) - 豆瓣评分 8.2
*   [《Git学习指南》](https://www.coderxing.com/r.php?r=https://u.jd.com/x06AA6) - 豆瓣评分 6.7
*   [《UML基础、案例与应用（第3版 修订版）》](https://www.coderxing.com/r.php?r=https://u.jd.com/W50GoO)

### 运维\&DevOps

*   [《编码：隐匿在计算机软硬件背后的语言 \[Code:The Hidden Language of Computer Hardware and Software\]》](https://www.coderxing.com/r.php?r=https://u.jd.com/3ejMcd) - 豆瓣评分 9.3
*   [《DevOps实践指南》](https://www.coderxing.com/r.php?r=https://u.jd.com/pVBguN) - 豆瓣评分 9
*   [《性能之巅：洞悉系统、企业与云计算》](https://www.coderxing.com/r.php?r=https://u.jd.com/RXZBkB) - 豆瓣评分 8.7
*   [《鸟哥的Linux私房菜 基础学习篇 第四版》](https://www.coderxing.com/r.php?r=https://u.jd.com/kzDG88) - 豆瓣评分 8.2
*   [《DevOps开发运维训练营》](https://www.coderxing.com/r.php?r=https://u.jd.com/Slnb59)

# 国内低代码平台

## 全栈平台

*   阿里-云凤蝶
    *   [蚂蚁杨周璇：我做前端这十多年来的感悟](https://mp.weixin.qq.com/s/GiFpswpm_N_5MlnBywRTgw)
    *   [云凤蝶可视化搭建的推导与实现](https://zhuanlan.zhihu.com/p/101665976)
    *   [云凤蝶中台研发提效实践](https://zhuanlan.zhihu.com/p/78425921)
    *   [中台建站的智能化探索](https://zhuanlan.zhihu.com/p/54422324)
    *   [云凤蝶如何打造媲美 sketch 的自由画布](https://zhuanlan.zhihu.com/p/92469406)
    *   [云凤蝶自由画布之道：分层模型](https://zhuanlan.zhihu.com/p/97768853)
*   阿里-金蝉
    *   [长夜未央——企业级研发提效的下一阶段](https://zhuanlan.zhihu.com/p/66474056)
    *   [十倍效能提升——Web 基础研发体系的建立](https://zhuanlan.zhihu.com/p/34790596)
    *   [前端服务化——页面搭建工具的死与生](https://www.cnblogs.com/sskyy/p/6496287.html)
*   [阿里-宜搭](https://www.aliwork.com/)
*   阿里-通用低代码基础设施
    *   [低代码引擎搭建协议规范](https://lowcode-engine.cn/lowcode) | [低代码引擎物料协议规范](https://lowcode-engine.cn/material) | [低代码引擎资产包协
        议规范](https://lowcode-engine.cn/assets)
    *   [阿里开源的低代码引擎](https://github.com/alibaba/lowcode-engine) | [官网](https://lowcode-engine.cn)
    *   [阿里低代码引擎和生态建设实战及思考](https://mp.weixin.qq.com/s/MI6MrUKKydtnSdO4xq6jwA)
*   阿里-天马
    *   [如何设计阿里经济体都在用的搭建服务—天马](https://zhuanlan.zhihu.com/p/137470317)
*   腾讯-积木
    *   [积木系统v2@江源.pptx](https://vdisk.weibo.com/s/cSKQveSBDMPco)
    *   [积木系统，将运营系统做到极致](https://cloud.tencent.com/developer/article/1055079)
*   腾讯-lowcode
    *   [腾讯云开发低码平台](https://console.cloud.tencent.com/lowcode)
    *   [腾讯无极低码平台](https://wujicode.cn)
*   葡萄城-活字格
    *   [活字格企业级低代码开发平台](https://www.grapecity.com.cn/solutions/huozige)
    *   [活字格产品经理胡耀：看活字格低代码平台是如何诞生的](https://www.soft6.com/news/2021/08/24/377493.html)
    *   [驳“低代码开发取代程序员”论 为什么专业开发者也需要低代码？](https://segmentfault.com/a/1190000040842990)
*   [无远开发平台](https://wuyuan.io/)
    *   [案例](https://wuyuan.io/case)
    *   [为什么专业开发者都选择无远](https://zhuanlan.zhihu.com/p/382493959)
*   [奥哲](https://www.authine.com/)
    *   [氚云](https://h3yun.com/index.php?g=Chuanyun\&m=Index\&a=index)
*   [ivx](https://www.ivx.cn/index)
    *   [关于iVX平台实现的总体技术栈【低代码/无代码、可视化开发语言】](https://blog.csdn.net/troymeng/article/details/110384703)
    *   [iVX是怎么开发出来的？0代码开发的理论基础是什么？](https://bbs.ivx.cn/1535)
    *   [iVX和其他低代码的开发平台区别究竟在哪里](https://bbs.ivx.cn/mobile/2746)
    *   [ih5](https://www.ih5.cn/)
*   [闪电数据管理](http://www.gitmen.com/lightning)
    *   [闪电数据管理 —— 无代码数据管理(开发)系统](https://zhuanlan.zhihu.com/p/162964986)
    *   [lightning —— 基于Django的无代码Admin及低代码开发框架](https://github.com/git-men/lightning)
*   [巴克云](https://www.buckycloud.com/)
*   [数式科技](https://shushi.pro/technology)
*   [明道云](https://www.mingdao.com/) 支持公共云和私有部署，私有部署在Github可获得[免费社区版下载](https://github.com/mingdaocom/private-deployment)
*   [轻流](https://qingflow.com/)
*   [速融云](https://www.surongyun.cn/)
*   [简道云](https://www.jiandaoyun.com/)
*   [启业云](https://www.qycloud.com.cn/)
*   [双链DaaS](https://github.com/doublechaintech/daas-start-kit)
    *   [直接通过Github Actions体验](https://github.com/doublechaintech/daas-with-github-actions)
    *   [大型系统构建案例-1.5K Stars](https://github.com/doublechaintech/scm-biz-suite)
    *   [包含实时预效果的KSML操练场-开发中](http://kg2x.doublechaintech.com/view/playground)
*   [炎黄盈动](https://www.actionsoft.com.cn/)
*   [广州天翎myApps](http://www.teemlink.com/)
*   [起步科技](http://www.wex5.com/)
*   [金蝶云-苍穹](http://www.kingdee.com/products/cosmic)
*   [普元](http://primeton.com/products/ep/overview.php)
*   OpsMind
    *   [OpsMind 前端低代码开发平台--MPlatform](https://mp.weixin.qq.com/s/gTVUii6ekVZNoX-6k5UCcg)
*   [xdeer](https://www.xdeer.cn/)
*   [湘北智造](https://www.xjrsoft.com/)
*   [表单大师](https://www.jsform.com/)
*   [Zion/载航](https://functorz.com/)
*   [Appsmith](https://www.appsmith.com/)（[Github](https://github.com/appsmithorg/appsmith)）
*   [ILLA Cloud/艾拉云](https://www.illacloud.com/)（[Github](https://github.com/illacloud/illa-builder)）
*   [白码](https://www.bnocode.com/product.html)
*   [捷码](https://gemcoder.com/)
    *   支持业务系统/管理系统、可视化大屏、3D园区低码快速开发
    *   支持离线部署
*   [明源云-天际开放平台](https://open.mingyuanyun.com)
    *   [移动平台](https://open.mingyuanyun.com/product/mpaas)
    *   [建模平台](https://open.mingyuanyun.com/product/platform)
*   [织信低代码平台](https://www.informat.cn/)
    *   [平台简介](https://www.informat.cn/promotion)
    *   [生产领域实践案例&君乐宝](https://www.informat.cn/case/jlb)
    *   [织信Informat携手低码星球探讨「企业数字化转型之路」](https://www.informat.cn/detail/248)
    *   [如何通过织信Informat快速搭建流程审批系统？](https://www.informat.cn/detail/228)
    *   [5K字深度讲解：如何用织信Informat搭建OA和进销存？](https://zhuanlan.zhihu.com/p/393588263)
*   [crudapi-增删改查接口平台](https://crudapi.cn)
    *   [无需编程，通过配置零代码生成crud增删改查RESTful API和UI](https://help.crudapi.cn/helloworld.html)
    *   [前端（开源）](https://github.com/crudapi/crudapi-admin-web)：Vue + Quasar实现Web管理UI，可任意修改。
    *   [后端（商业使用永久免费，无任何功能限制）](https://github.com/crudapi/crudapi-example)：Java + Jdbc实现Service，数据库支持MySQL、PostgreSQL、SQL Server和Oracle，支持二次开发和私有部署。
    *   [demo演示](https://demo.crudapi.cn/crudapi/)
*   [Gadmin企业级低代码开发平台](https://www.gadmin8.com/)
    *   [平台简介](https://www.gadmin8.com/index/about.html)
    *   [平台演示](https://demo.gadmin8.com/)
*   [象传智慧](https://www.iqka.com/docs/?engine)
    *   [Yao](https://yaoapps.com/)
*   [引迈信息](https://www.jnpfsoft.com/)
*   [兰途科技](http://www.app8848.com)
    *   [aPass软件工厂](https://www.yuque.com/books/share/9aab5860-6301-4519-a8ae-ac1d3b9dee11)
*   [矩阵低代码](https://www.deepmatrix.cn/) : 支持私有化部署，支持离线部署，私有化部署版本可跟随主版本免费升级
    *   [平台演示](https://server.deepmatrix.cn/) : 账户：15000000000 密码： 123456
    *   [平台介绍](https://www.deepmatrix.cn/)
    *   [系统文档](https://www.yuque.com/dawei-ktv92)
*   [星云座插件式低代码](https://www.xingyunzuo.com/)
    *   插件方式融入现有的业务系统，贯通用户权限和业务数据，赋能业务系统具备低代码开发能力
    *   支持开发平台/项目私有化部署，开发平台与项目相互独立互补依赖
    *   [产品介绍](https://mp.weixin.qq.com/s/3PyctlBCIbOQRiCunFlR3Q)
    *   [平台演示](https://dev.xingyunzuo.com/): 用户名：18888888888 密码：888888
    *   [产品视频](https://space.bilibili.com/2045740689)
*   [瓦立应用](https://www.waliapp.cn/)
    *   支持可视化小程序搭建、
    *   支持各种业务系统开发（具有表单、工作流、报表设计等模块）
    *   [系统文档](https://www.yuque.com/zhonglixunni/wali)
*   [瀚码工业低代码](https://www.hancode.com/products/lcdp)
    *   四大工业特性：工业组件（工艺流程图、工作日历、脑图、树形图、鱼骨头...）、工业模版（MES、TPM、QMS、WMS、AMES）、移动PDA支持、系统对接（PLC、CNC、注塑机、ERP...）
    *   模型驱动、应用可与开发平台分离【重点】
    *   [系统文档](https://hancode.yuque.com/ibi3kw/qzp9ku/ywwzqm)
    *   [产品介绍](https://www.zhihu.com/question/402663485/answer/2772342587)

## 页面搭建

仅包含前端部分的 low code 平台

*   [MAKA](http://maka.im/)

*   [易企秀](https://store.eqxiu.com/)

*   [上线了](https://www.sxl.cn/)

*   [兔展](https://www.rabbitpre.com/)

*   [稿定设计](https://m.gaoding.com/)

*   [壹伴](https://yiban.io/)

*   [创客贴](https://www.chuangkit.com/)

*   [点石](https://www.h5ds.com/)

*   腾讯-tmagic-editor
    *   [开源的页面可视化搭建编辑器tmagic-editor](https://github.com/Tencent/tmagic-editor)

*   京东-通天塔
    *   [京东商城活动页面构建系统——通天塔](https://blog.csdn.net/zl1zl2zl3/article/details/84661421)

*   [阿里-imgcook](https://imgcook.taobao.org/)

*   转转-魔方
    *   [持续迭代的电商可视化运营页面生成系统](https://www.cnblogs.com/zhuanzhuanfe/p/10500786.html)

*   人人贷-活动运营平台
    *   [活动运营自动化平台实践](https://zhuanlan.zhihu.com/p/68108055)

*   美团-乐高
    *   [美团外卖前端可视化界面组装平台 —— 乐高](https://zhuanlan.zhihu.com/p/27288444)

*   [百度-h5](https://h5.bce.baidu.com/)
    *   [前端即服务-通向零成本开发之路](https://os.alipayobjects.com/rmsportal/sJqXvOtwePsVWGNIwlas.pdf)

*   政采云-鲁班
    *   [前端工程实践之可视化搭建系统（一）](https://juejin.im/post/5d8774bff265da03ae78b2a1)

*   携程-民宿CMS
    *   [活动专题系统搭建过程中我的一些思考](https://www.dazhuanlan.com/2019/10/07/5d9a698bdde35/)

*   携程-乐高
    *   [干货 | 已配置4000+页面，携程前端组件化探索之“乐高”运营系统](https://mp.weixin.qq.com/s/WDCkXEBa0bA-h_8L6cBcJw)

*   云智慧-FlyFish
    *   [低门槛、高拓展性的低代码应用开发平台](https://www.cloudwise.ai/flyFish.html)

*   知乎-Versatile Editor
    *   [「可视化搭建系统」——从设计到架构，探索前端领域技术和业务价值](https://zhuanlan.zhihu.com/p/164558106)

*   [阿里-bi designer](https://github.com/dt-fe/weekly/blob/v2/164.%E7%B2%BE%E8%AF%BB%E3%80%8A%E6%95%B0%E6%8D%AE%E6%90%AD%E5%BB%BA%E5%BC%95%E6%93%8E%20bi-designer%20API-%E8%AE%BE%E8%AE%A1%E5%99%A8%E3%80%8B.md)

*   [360 - 即视](https://arena.360.cn/)

*   http://h5.dooring.cn/

*   https://quarkly.io/  No-code / Low-code platform for creating websites and web apps.

*   [乐搭云](https://ledayun.com.cn/)

*   [愚公](https://yugong.dawenxi.art/dashboard/#/project)

*   [榫卯（sunmao-ui）](https://sunmao-ui.com/)

## 店铺装修

非独立页面，依附于业务系统存在的页面搭建

*   [shopify](https://apps.shopify.com/browse/store-design-page-builders)
*   有赞-微页面
*   淘宝店铺装修

## ![Open Source Love svg3](https://badges.frapsoft.com/os/v3/open-source.svg?v=103)

*   [阿里-飞冰](https://ice.work/)
*   [阿里-formilyjs](https://formilyjs.org/)
    *   [MegaLayout - 下一代Formily表单布局解决方案](https://zhuanlan.zhihu.com/p/133906363)
    *   https://github.com/alibaba/designable
*   [阿里-gaea-editor](https://github.com/ascoders/gaea-editor)
    *   [可视化在线编辑器架构设计](https://juejin.cn/post/6844903455417434119)
*   [阿里-sula](https://github.com/umijs/sula)
*   [视搭-视频可视化搭建](https://github.com/tnfe/shida)
*   https://github.com/alibaba/lowcode-engine
*   [blockVisualEditor](https://github.com/sww1230/blockVisualEditor)
*   [pager](https://github.com/laispace/pager)
*   [运满满-码良](https://github.com/ymm-tech/gods-pen)
    *   [如何设计高扩展的在线网页制作平台](https://juejin.im/post/5bd83daee51d4524b50d23b5)
*   [X-Page-Editor](https://github.com/OXOYO/X-Page-Editor-Vue)
*   [Vue-Layout](https://github.com/jaweii/Vue-Layout)
*   [antd-visual-editor](https://github.com/xinyu198736/antd-visual-editor)
*   [pipeline-editor](https://github.com/page-pipepline/pipeline-editor)
    *   [【第1524期】页面可视化搭建工具技术要点](https://mp.weixin.qq.com/s/90JJAFhGokKmicOQZxdAGg)
*   [panel-magic](https://ricbet.github.io/panel-magic/)
    *   [基于 Angular 的小程序可视化编辑器 Panel-Magic 的实现解析](https://zhuanlan.zhihu.com/p/101677992)
*   [百度外卖-blocks](https://github.com/Eyot424/blocks)
    *   [百度外卖如何做到前端开发配置化](https://juejin.im/post/59536bad6fb9a06ba024d96d)
*   [Esview ](https://github.com/furioussoul/esview)
*   [gen](https://github.com/genany/gen)
*   [bee gen pro](https://gocn.vip/topics/10724)
*   [百度-amis](https://github.com/baidu/amis)
    *   [Ovine](https://github.com/CareyToboo/ovine)：基于 amis 补全了路由、权限相关的组件
    *   [爱速搭](https://suda.baidu.com/)
*   [唯品会-ams](https://github.com/vipshop/ams)
*   [vue-admin](https://github.com/jiangshanmeta/vue-admin)
*   [鲁班 H5](https://github.com/ly525/luban-h5)
*   [华炎魔方](https://github.com/steedos/steedos-platform/)
    *   [低代码 DevOps 平台协议](https://low-code-protocol.com/docs/overview)
*   [h5-factory](https://github.com/yangyuji/h5-factory)
    *   [一个简单易用的电商活动页面生成系统](https://juejin.im/post/5cf328706fb9a07f042030f0)
*   [vision](https://github.com/tuoxiansp/vision)
*   [brick-design](https://github.com/brick-design/react-visual-editor)
*   [随心秀](https://github.com/lzuntalented/lz-h5-edit)
*   [yh5](https://github.com/qq15725/yh5)
*   [rxeditor](https://github.com/rxwater/rxeditor)
*   [activity-YD](https://github.com/vkcyan/activity-YD)
*   [layoutit](https://github.com/justjavac/layoutit)
*   [Ramiko](https://github.com/fantasticit/ramiko)
    *   [使用 React 构建页面可视化搭建工具](https://www.v2ex.com/t/685143)
*   [jeecg-boot](https://github.com/zhangdaiscott/jeecg-boot)
*   [sparrow-js](https://github.com/sparrow-js/sparrow)
    *   [实时输出前端代码，折腾大半年的开源项目 sparrow-js](https://www.v2ex.com/t/718505)
*   [Tefact](https://github.com/staringos/tefact): Tefact 轻量级无代码/低代码，H5、表单编辑器
*   [星搭](https://staringos.com): 星搭无代码平台，快速构建中后台、小程序
*   [好未来晓黑板go-zero微服务框架](https://github.com/tal-tech/go-zero): 你不需要懂微服务，懂业务就行
*   [cube](https://github.com/fantasticit/cube)：快速搭建中后台页面
*   [react-visual-design](https://github.com/react-visual-design/react-visual-design): 基于react的h5组件搭建
*   [Web Designer](https://github.com/xiaoai7904/web_designer)
*   [h5maker](https://github.com/zhengguorong/h5maker)
*   [pl-drag-template](https://github.com/livelyPeng/pl-drag-template)
*   [form-generator](https://github.com/JakHuang/form-generator)：Element UI表单设计及代码生成器
*   [form-render](https://github.com/alibaba/form-render)：通过 JSON Schema 生成标准 Form，基于React
*   [Vue Json Design](https://github.com/fyl080801/vjdesign)
*   [rebuild](https://gitee.com/getrebuild/rebuild)
*   [W5 SOAR](https://github.com/w5teams/w5)
*   [Moria - Lowcode development platform](https://github.com/MudOnTire/moria)
*   [nocobase](https://github.com/nocobase/nocobase)
*   [Mall-Cook](https://github.com/wangyuan389/mall-cook)
*   [全象低代码平台渲染引擎 Artery Renderer](https://github.com/quanxiang-cloud/one-for-all/tree/main/packages/artery-renderer)
*   https://github.com/bojue/Web-Editor
*   [OpenDataV - 基于Vue3的拖拽式、低代码数据可视化平台](https://github.com/AnsGoo/openDataV)
*   [StaringOS MtBird](https://github.com/staringos/mtbird): 开源小程序、H5、网站低代码平台，无需代码，拖拽操作快速生成页面应用，数据可视化接入，定制业务自由拓展.

***

*   https://github.com/blocks/blocks
*   https://github.com/frappe/frappe
*   https://github.com/ipselon/structor
*   https://github.com/vigetlabs/colonel-kurtz
*   https://github.com/BuilderIO/builder
*   https://github.com/vuegg/vuegg
*   https://webcodesk.com/
*   https://github.com/odoo/odoo
*   https://github.com/imgcook/imove

## 办公/管理系统 a.k.a no-code

*   [黑帕云](https://hipacloud.com/)
*   [极星协作](https://app.bjx.cloud/template)
*   [维格表](https://vika.cn/)
*   [阿里云-Teambition](https://www.teambition.com/tour)
*   [阿里云-RPA](https://cn.aliyun.com/product/codestore)
*   [SeaTable](https://seatable.cn/)
*   [蒲公英-Tracup](https://www.tracup.com/)
*   [蒲公英-Seed](https://seed.pgyer.com/)
*   [伙伴云](https://www.huoban.com/)
*   [monday.com](https://monday.com/)
*   [Airtable](https://airtable.com/)
*   [Notion](https://www.notion.so/)
*   https://welovenocode.com/nocodelist
*   [Taskade](https://www.taskade.com/)

## 声明式编程

*   ["Probabilistic scripts for automating common-sense tasks" by Alexander Lew](https://www.youtube.com/watch?v=MiiWzJE0fEA)

## 行业综述

*   [Forrester《The State Of Low-Code Platforms In China》（中国低代码平台发展报告）](https://zhuanlan.zhihu.com/p/436106248)
*   [精读《对低代码搭建的理解》](https://zhuanlan.zhihu.com/p/161783546)
*   [页面可视化搭建工具前生今世](https://zhuanlan.zhihu.com/p/37171897)
*   [React.js 可视化编辑工具](https://juejin.im/post/5d7ae944f265da03c5033e38)
*   [对低代码、零代码产品的一些看法](https://zhuanlan.zhihu.com/p/156887528)
*   [对 aPaaS 的产品认知](https://zhuanlan.zhihu.com/p/149801853)
*   [无代码编程](https://zhuanlan.zhihu.com/p/61288928)
*   [万物代码化：从低代码、云开发到云研发的思考](https://zhuanlan.zhihu.com/p/141742525)
*   [《早早聊搞搭建》搞过搭建的我收获了什么？](https://juejin.im/post/6844904106767695880)
*   [工程化之低代码体系](https://juejin.cn/post/6913698066935578631)
*   [LowCode平台前端实战之京东投放素材中心](https://zhuanlan.zhihu.com/p/386761240)

## 技术点

*   可逆计算
    *   [可逆计算：下一代软件构造理论](https://zhuanlan.zhihu.com/p/64004026)
    *   [从可逆计算看声明式编程](https://zhuanlan.zhihu.com/p/85492497)
*   [161.精读《可视化搭建思考 - 富文本搭建》](https://github.com/dt-fe/weekly/issues/262)
*   [面向 Model 编程的前端架构设计](https://zhuanlan.zhihu.com/p/144157268)
*   [流动的数据——使用 RxJS 构造复杂单页应用的数据逻辑](https://github.com/xufei/blog/issues/38)
*   [使用 React 写个简单的活动页面运营系统 - 设计篇](https://segmentfault.com/a/1190000004540256)
*   [【电商】用可视化编辑，解构看起来非常炫酷的专题页面](https://www.jianshu.com/p/c4359a7338d3)
*   [如何搭建一个功能复杂的前端配置化框架(一)](https://www.cnblogs.com/wukong-holmes/p/9287763.html)
*   [可视化拖拽组件库一些技术要点原理分析](https://juejin.cn/post/6908502083075325959)
*   [可视化拖拽组件库一些技术要点原理分析（二）](https://juejin.cn/post/6918881497264947207)
*   [可视化拖拽组件库一些技术要点原理分析（三）](https://juejin.cn/post/6929302655118344200)
*   [可视化拖拽组件库一些技术要点原理分析（四）](https://juejin.cn/post/7129311619963682830)
*   [揭秘活字格最受程序员喜爱的三大功能背后的设计思路](https://www.grapecity.com.cn/blogs/huozige-the-three-most-popular-features-for-programmers)

## 国外

*   https://www.honeycode.aws/
*   https://developers.google.com/appmaker
*   https://powerapps.microsoft.com/zh-cn/
*   https://www.zoho.com/creator/
*   https://www.salesforce.com/
*   https://www.appian.com/
*   https://bubble.io/
*   https://www.adalo.com/
*   https://thunkable.com/
*   http://www.vvveb.com/vvvebjs/editor.html
*   https://www.forestadmin.com/
*   https://mobirise.com/
*   https://paperbits.io/
*   https://builderx.io/
*   https://grapesjs.com/
*   https://reactstudio.com/
*   https://www.wix.com/
*   https://university.webflow.com/
*   https://www.squarespace.com/
*   https://www.framer.com/
*   https://www.figma.com/
*   https://linx.software/
*   https://www.mendix.com/zh/
*   https://www.outsystems.com/
*   https://retool.com/
*   https://www.quickbase.com/
*   https://layoutit.com/
*   https://www.claris.com/zh/filemaker/
*   FoC 聊天记录：https://marianoguerra.github.io/future-of-coding-weekly/history/?fromDate=2017-06-13\&toDate=2017-06-14\&channel=general\&filter=
*   https://www.joget.com/
*   https://help.appsheet.com/en/
*   https://appery.io/
*   [ERD Lab](https://www.erdlab.io/) - Free cloud based entity relationship diagram (ERD) tool made for developers.

# 一切改进都是源自于人类的缺陷

## How we think

*   人脑是串行的，无法有效并行思考多条线索
    *   人脑不适合思考并行执行的多线程
        *   【单线程】把共享变量的编程模式改成事务整体提交的模式
    *   人脑不适合思考同时呈现在屏幕上的多个独立的业务流程
        *   代码是按发生时间组织的，在一起的代码未必是逻辑上有关联的业务流程
            *   【按业务切分文件】阅读者应该可以按照自己的任务目标来跟踪索引，而不是默认一个按钮点击引起的处理逻辑都一定要写在一个大文件里
            *   【按变更频率切分文件】业务变更是阅读的首要原因，代码应该按照业务变更的频率来组织。会同时变更的代码应该放在一起
    *   人脑很难管理多份独立可变的状态，本质上每个独立变化的状态就是一个独立的线程
        *   驱动状态数量熵增的三大因素：
            *   因为交互体验的要求，从后端到富客户端到3d动画，状态被复制多份，越来越靠近展示层
            *   因为硬件物理的约束，内存从CPU统一寻址，到异构计算，CUDA，每个硬件核都有一层自己的内存
            *   因为数据量的增长，从统一的OLAP从库，到Data Lake，Data Mart，数据被复制成越来越多份，流水线越来越长
        *   对抗状态数量熵增的手段：
            *   【声明式数据联动】减少独立变化的状态，用表达式来表达 derived state
            *   【全局虚拟数据层】借鉴Unix的统一文件抽象，引入一层统一的虚拟数据层。尽可能把状态转化成 cache
    *   人脑很难理解新增对原有行为的剧烈变化，更习惯逐层稳定叠加。也就是人更希望“控制变量”
        *   css 最大的难度在于不正交，新增一条对规则会引起意想不到的效果
            *   【局部化布局】swiftui 的 HStack/VStack/ZStack 布局规则数量少，每条规则作用都是局部的稳定的叠加
        *   性能优化往往需要破坏局部性，因为局部的自治容易引起重复劳动
            *   【局部化IO】系统自动实现 I/O 的批量等可以自动化做的全局优化
            *   【局部化IO】业务写成自治的，但是可以附加额外的手工全局调优。而不是强制要求把业务逻辑从局部抽出去

## How we perceive

*   人眼只能在狭窄的感受野里获得信息
    *   人对时间的感知是来自于对空间的感知
    *   人希望在一个屏幕内从上往下的获取时间顺序上从早到晚的信息
        *   callback 的编程方式破坏了屏幕上的顺序和时间顺序的直接映射关系
            *   【协程式IO】用协程取代 callback，把屏幕上的代码撸直
        *   通过 status 字段驱动的业务状态机破坏了屏幕上的顺序和时间顺序的直接映射关系
            *   【协程式业务流程】用协程取代 status 状态机，把屏幕上的代码撸直
    *   因为感受野的限制，源代码没有空间展示所有的细节
        *   类型定义，内存分配等“细节”占用了大量的视觉区域
            *   【IDE细节隐藏】在文本上省略掉细节，由 IDE 进行补全，当鼠标移动上去的时候才展示出来
        *   人最习惯的空间整理方式仍然是层状的文件夹
            *   所有的“架构”设计，最终都是对文件夹和文件的设计。但是一个维度的静态索引（文件夹嵌套）无法满足所有可能的检索需求
                *   【IDE按需索引】由 IDE 来补全文件夹分类不能满足的索引需求，针对阅读者的任务来设计IDE索引
    *   视杆细胞容易忽略形状和顺序的差异，但是对颜色更敏感
        *   语法高亮占用了宝贵的资源，但是并没有考虑阅读者的诉求
            *   【IDE按需高亮】对于不同的任务，阅读者希望找到的重点是不同的，语法高亮应该结合任务来做

## How we collaborate

*   人与人之间最高效的沟通的方式是面对面的交互式声波震动
    *   人类低下的沟通带宽根本上限制了一个团队的规模
        *   上线速度要求越快越好，但是加人带来的边际效益递减
            *   减少开会拉齐，团队应该尽可能地自治，而不是什么都要靠 feature team 横向拉通
                *   高内聚，低耦合
                    *   【静态链接包】编程工具应该提供更多的组合可能，而不是所有的组合都要在运行时用面向对象的多态来实现
                    *   【按变更频率切分包】分工应该按照变更频率来确定，分工应该是明确的
    *   尽可能由最终用户，或者靠近最终用户的团队来解决问题，而不是长距离传递需求
        *   最终用户编程：直接让需求提出者自己来实现需求
            *   把“学习”内置到工具里，需要内置一个教学工具
                *   最终用户的编程工具开发难度高，成本高，投入超过了单个软件的回报
                    *   【编辑器预制】把“公式编辑”，“店铺装修”等常见共性需求提前预制
            *   教学工具的目标是教学，而不是把自己标杆为更先进的生产力
                *   【教学内置】提供教学模式和生产力模式的无缝切换
        *   低代码编程：通过提前预制，把工作量前置，减少应用开发者的规模，从而可以在组织架构上把开发者内置到用户组织内部。与此相对应的是文档驱动的外包式开发。
            *   “预制”来自于对共性需求的提前预判
                *   【非功能性需求云化】非功能性需求的实现，都是运行在相似的机器上
                    *   操作系统
                    *   k8s
                    *   RPC 框架
                *   开发者都是人类
                    *   编程工具
                    *   沟通工具
                *   用户都是人类
                    *   【SaaS组件】IM / 电话 / 短信
                    *   【Ui组件】字处理器 / 表格
                    *   【CRUD生成】惯用的展现和交互
                        *   列表详情
                        *   树状层级
                        *   表格结构
                        *   可拖拽白板
                *   【SaaS组件】相对稳定的业务流程
                    *   登录注册
                    *   支付
                *   行业内相对稳定的业务共性流程
                    *   电商
                    *   HR / 招聘
                    *   销售管理 / CRM

## How we learn

*   人的“归纳/理解/学习”能力高度依赖于可视化交互式地操纵与反馈
    *   帮助应该放在任务执行的地方，与其说“可视化”，不如说是“可发现”
        *   【填空题变选择题】单独的语法手册是不好使的，必须提供界面上的按钮，把填空题变成选择题，这样才能启发学习
            *   GUI 设计器 / 店铺装修
            *   公式编辑器
            *   审批 / 工作流设计器
            *   trigger 流程设计器
    *   人习惯于用手触碰一下对象，然后观测其反馈，从而归纳学习
        *   不可观测的行为无法学习
            *   生产环境的bug无法本地复现，我怎么找规律？
                *   【TestInProduction】tracing，大量的 tracing，流量回放
            *   lowcode 平台的bug没有任何线索，除了找平台开发者，我能怎么办？
                *   不能要求用户了解所有的内部细节，“平台”要做到可依赖
                *   业务逻辑问题的定位和生产环境的bug定位一样，靠 tracing
        *   反馈太慢的行为给人的负面感受是指数增加的
            *   本地机器太慢了跑不起来，需要上公司的沙盒环境来复现问题
                *   【云IDE】
            *   改完了代码需要重新编译重新加载
                *   【LanguageServer】交互式开发的时候跳过不必要的编译
                *   【所见即所得】所见即所得的 GUI 开发，本质上就是用解释器执行，换取编译时间的缩减
                *   【HMR】重加载的时候保持页面状态

# no code / low code / pro code

一切的改进都是源自于人类的缺陷

*   no code：自己编程给自己用，给用户的感觉是一个更强大的办公/实用软件。主要的手段是用图形化操作等方式降低学习曲线。no code 一定要面向非常固定的领域才能做到好用。
*   low code：编程给其他人用，为此创造了一个 citizen developer 的概念。主要的手段是平台预制好常见的需求，减少需要从头写的代码。low code 也要面向指定的领域才能让平台提前预测需求，但相比 no code 可以不把使用场景限定得那么死。
*   pro code：low code 的平台自己不会选择 low code 来创建这个平台本身，因为 low code 并没有降低从头构建一个系统的成本。但是 pro code 的平台自己会选择 pro code 来创建这个平台本身，比如 react 开发者会选择用 react 来创建自己的开发工具，因为 pro code 的工具和平台都是以从根本上降低从头构建一个系统的复杂度为目标的。

## Table of Contents

*   [Dart](#dart)
*   [Java](#java)
*   [Vue](#vue)
*   [Objective-C](#objective-c)
*   [JavaScript](#javascript)
*   [TypeScript](#typescript)
*   [Shell](#shell)
*   [Go](#go)
*   [Python](#python)
*   [Dockerfile](#dockerfile)
*   [miscellaneous](#miscellaneous)
*   [Kotlin](#kotlin)
*   [Jupyter Notebook](#jupyter-notebook)
*   [HTML](#html)
*   [Starlark](#starlark)
*   [Groovy](#groovy)
*   [Rust](#rust)
*   [Ruby](#ruby)
*   [C](#c)
*   [C++](#c-1)
*   [CSS](#css)
*   [PHP](#php)
*   [OCaml](#ocaml)
*   [Markdown](#markdown)
*   [Bikeshed](#bikeshed)
*   [CoffeeScript](#coffeescript)
*   [SCSS](#scss)
*   [Stylus](#stylus)
*   [Less](#less)
*   [Thanks](#thanks)

## Dart

*   [YeFei572/him-demo-flutter](https://github.com/YeFei572/him-demo-flutter) - socket + websocket + protobuf 即时通讯IM

*   [ReberSincar/Flutter-WebRTC-Socketio-Video-Call](https://github.com/ReberSincar/Flutter-WebRTC-Socketio-Video-Call) -

*   [nikkon404/quick-chat-flutter](https://github.com/nikkon404/quick-chat-flutter) - Flutter app for chatting (based on socket.io and Node.js)

*   [AhmedAbouelkher/flutter\_socket\_io\_chat](https://github.com/AhmedAbouelkher/flutter_socket_io_chat) -

*   [GeekAbdelouahed/Flutter-Socket-IO-Chat](https://github.com/GeekAbdelouahed/Flutter-Socket-IO-Chat) - Flutter chat applications using Socket IO

*   [afgprogrammer/Flutter-Complete-e-commerce](https://github.com/afgprogrammer/Flutter-Complete-e-commerce) - Flutter e-commerce Application  design and Animation - day 16-17

*   [Sky24n/flustars](https://github.com/Sky24n/flustars) - 🔥🔥🔥  Flutter common utils library. SpUtil, ScreenUtil,WidgetUtil.  也许是目前最好用的SharedPreferences工具类。WidgetUtil 获取图片尺寸宽高, View尺寸&在屏幕上的坐标。

*   [firgia/FD-Marketplace](https://github.com/firgia/FD-Marketplace) - Create mobile marketplace design using Flutter

*   [DelinQu/Flutter-SpringBoot-Login-Register-CRUD](https://github.com/DelinQu/Flutter-SpringBoot-Login-Register-CRUD) - 这是编程务实实验lab4，我使用SpringBoot + Flutter技术实现了一个具有登录，注册，邮箱验证，增删改查页面，社区功能，个人中心功能的APP。

*   [wuyuanwuhui99/flutter-movie-app-ui](https://github.com/wuyuanwuhui99/flutter-movie-app-ui) - 基于flutter开发的混合电影app，后端采用springboot+mybatis+mysql开发，有react-native版本，参见个人主页springboot和react-native项目包括底部tab导航,，首页，电影，电视剧，我的，搜索页，分类页，电影详情页，播放页，登录，注册，浏览记录，播放记录，收藏，缓存，电影排行榜等页面和模块，功能齐全完善，所有数据来自python爬虫程序，抓取爱奇艺和第三方电影网站实时电影数据，每周更新影片两只三次，持续更新中...

*   [flyerhq/flutter\_firebase\_chat\_core](https://github.com/flyerhq/flutter_firebase_chat_core) - Actively maintained, community-driven Firebase BaaS for chat applications with an optional chat UI.

*   [huangruiLearn/flutter\_hrlweibo](https://github.com/huangruiLearn/flutter_hrlweibo) - Flutter仿微博客户端,  包含首页、视频、发现、消息(仿微博聊界面)及个人中心模块

*   [rohan20/flutter-in-app-localisation](https://github.com/rohan20/flutter-in-app-localisation) - In app localisation demo in Flutter

*   [rohan20/flutter-chat-app](https://github.com/rohan20/flutter-chat-app) - A chat app built on Flutter with firebase authentication and image sharing capability.

*   [flyerhq/flutter\_chat\_ui](https://github.com/flyerhq/flutter_chat_ui) - Actively maintained, community-driven chat UI implementation with an optional Firebase BaaS.

*   [martin-ngigi/chatgpt\_flutter\_ai\_chatbot](https://github.com/martin-ngigi/chatgpt_flutter_ai_chatbot) - Open AI Chat Bot using Chat-GPT in Flutter

*   [huangzhiwu1023/flutter\_Drawer](https://github.com/huangzhiwu1023/flutter_Drawer) -

*   [vegasandroid/tesla-app](https://github.com/vegasandroid/tesla-app) - This mobile project created by flutter using Provider.

*   [IZriouil/coffee\_app](https://github.com/IZriouil/coffee_app) -

*   [swenes/chat\_message\_app\_FLUTTER](https://github.com/swenes/chat_message_app_FLUTTER) - this is a message/chat app with light and dark theme options

*   [firgia/FD-Project-Management](https://github.com/firgia/FD-Project-Management) - Create responsive dashboard Project Management design using Flutter

*   [mpflutter/mpflutter](https://github.com/mpflutter/mpflutter) - MPFlutter 是一个跨平台 Flutter 开发框架，可用于微信、飞书、字节小程序以及 Web 应用开发。如果您觉得该项目还不错，可以考虑点个 Star 或者通过这个页面 https://mpflutter.com/zh/docs/support-us 支持我们哦。

*   [mrezkys/marketky](https://github.com/mrezkys/marketky) - MarketKy is a Free Flutter E-Commerce App Starter Template that can help you develop an E-Commerce / Market application much faster.

*   [ferdirhyme/marketplace](https://github.com/ferdirhyme/marketplace) -

*   [dart-lang/site-www](https://github.com/dart-lang/site-www) - Source for Dart website

*   [flutter/samples](https://github.com/flutter/samples) - A collection of Flutter examples and demos

*   [flutter/packages](https://github.com/flutter/packages) - A collection of useful packages maintained by the Flutter team

*   [marcojakob/dart-event-bus](https://github.com/marcojakob/dart-event-bus) - An Event Bus using Dart Streams for decoupling applications

*   [xuexiangjys/flutter\_xupdate](https://github.com/xuexiangjys/flutter_xupdate) - A Flutter plugin for XUpdate(Android Version Update Library)

*   [rrousselGit/provider](https://github.com/rrousselGit/provider) - InheritedWidgets, but simple

*   [Baseflow/flutter\_cached\_network\_image](https://github.com/Baseflow/flutter_cached_network_image) - Download, cache and show images in a flutter app

*   [xuelongqy/flutter\_easy\_refresh](https://github.com/xuelongqy/flutter_easy_refresh) - A flutter widget that provides pull-down refresh and pull-up load.

*   [xuexiangjys/flutter\_template](https://github.com/xuexiangjys/flutter_template) - The project of the empty template with Flutter has built the basic framework to realize the functions of internationalization, theme peeling, login and registration, etc.(Flutter空壳模板工程，已搭建基础框架，实现国际化、主题换肤、登录注册、自动路由注册等功能，可在此基础上简单修改实现自己的应用功能)

*   [webVueBlog/egg-flutter-templates](https://github.com/webVueBlog/egg-flutter-templates) - A new Flutter project.

*   [CarGuo/gsy\_github\_app\_flutter](https://github.com/CarGuo/gsy_github_app_flutter) - Flutter 超完整的开源项目，功能丰富，适合学习和日常使用。GSYGithubApp系列的优势：我们目前已经拥有Flutter、Weex、ReactNative、kotlin 四个版本。 功能齐全，项目框架内技术涉及面广，完成度高，持续维护，配套文章，适合全面学习，对比参考。跨平台的开源Github客户端App，更好的体验，更丰富的功能，旨在更好的日常管理和维护个人Github，提供更好更方便的驾车体验Σ(￣。￣ﾉ)ﾉ。同款Weex版本 ： https://github.com/CarGuo/GSYGithubAppWeex    、同款React Native版本 ： https://github.com/CarGuo/GSYGithubApp 、原生 kotlin 版本 https://github.com/CarGuo/GSYGithubAppKotlin

*   [meetqy/flutter\_dating\_template](https://github.com/meetqy/flutter_dating_template) - flutter 版本的交友 app 模板，总计页面35个，测试数据基于 mockjs 创建（A dating app template for The Flutter version, with a total of 35 pages, was created based on MockJS.）

*   [yukilzw/dy\_flutter](https://github.com/yukilzw/dy_flutter) - 斗鱼直播APP :rocket: 多元化Flutter开源项目。涵盖礼物特效、手势动画、弹幕池、抽奖、鱼吧等（另提供服务端Mock接口）

*   [meetqy/flutter\_luckin\_coffee](https://github.com/meetqy/flutter_luckin_coffee) - flutter luckin coffee application（仿瑞幸咖啡）

*   [kaina404/FlutterDouBan](https://github.com/kaina404/FlutterDouBan) - 🔥🔥🔥Flutter豆瓣客户端,Awesome Flutter Project,全网最100%还原豆瓣客户端。首页、书影音、小组、市集及个人中心，一个不拉。（ https://img.xuvip.top/douyademo.mp4）

*   [flutter-stripe/flutter\_stripe](https://github.com/flutter-stripe/flutter_stripe) - Flutter SDK for Stripe.

*   [robertodevs/flutter\_ecommerce\_template](https://github.com/robertodevs/flutter_ecommerce_template) - This is an eCommerce minimalist template with a clean and beautiful design for Flutter.

*   [jogboms/flutter\_spinkit](https://github.com/jogboms/flutter_spinkit) - ✨ A collection of loading indicators animated with flutter. Heavily Inspired by http://tobiasahlin.com/spinkit.

*   [dnfield/flutter\_svg](https://github.com/dnfield/flutter_svg) - SVG parsing, rendering, and widget library for Flutter

*   [Baseflow/flutter-permission-handler](https://github.com/Baseflow/flutter-permission-handler) - Permission plugin for Flutter. This plugin provides a cross-platform (iOS, Android) API to request and check permissions.

*   [cfug/dio](https://github.com/cfug/dio) - A powerful HTTP client for Dart and Flutter, which supports global settings, Interceptors, FormData, aborting and canceling a request, files uploading and downloading, requests timeout, custom adapters, etc.

*   [AppsFlyerSDK/appsflyer-flutter-plugin](https://github.com/AppsFlyerSDK/appsflyer-flutter-plugin) - Flutter Plugin for AppsFlyer SDK

*   [letsar/flutter\_staggered\_grid\_view](https://github.com/letsar/flutter_staggered_grid_view) - A Flutter staggered grid view

*   [shichunlei/flutter\_app](https://github.com/shichunlei/flutter_app) - 🔥🔥🔥本项目包括各种基本控件使用（Text、TextField、Icon、Image、Listview、Gridview、Picker、Stepper、Dialog、Slider、Row、Appbar、Sizebox、BottomSheet、Chip、Dismissible、FlutterLogo、Check、Switch、TabBar、BottomNavigationBar、Sliver等）、豆瓣电影、tubitv、每日一文、和天气、百姓生活、随机诗词、联系人、句子迷、好奇心日报、有道精品课、高德定位、音乐播放器🎵、追书神器等板块

*   [TheAlphamerc/flutter\_smart\_home\_app](https://github.com/TheAlphamerc/flutter_smart_home_app) - Smart home app designed in flutter

*   [TheAlphamerc/flutter\_news\_app](https://github.com/TheAlphamerc/flutter_news_app) - A Simple News App built with Flutter.

*   [TheAlphamerc/flutter\_wallet\_app](https://github.com/TheAlphamerc/flutter_wallet_app) - Wallet app built in flutter

*   [TheAlphamerc/flutter\_twitter\_clone](https://github.com/TheAlphamerc/flutter_twitter_clone) - Fully functional Twitter clone built in  flutter framework using Firebase realtime database and storage

*   [syncfusion/flutter-examples](https://github.com/syncfusion/flutter-examples) - This repository contains the Syncfusion Flutter UI widgets examples and the guide to use them.

*   [abuanwar072/Flutter-Responsive-Admin-Panel-or-Dashboard](https://github.com/abuanwar072/Flutter-Responsive-Admin-Panel-or-Dashboard) - Responsive Admin Panel or Dashboard using Flutter

*   [yubo725/flutter-osc](https://github.com/yubo725/flutter-osc) - 基于Google Flutter的开源中国客户端，支持Android和iOS。

*   [Sub6Resources/flutter\_html](https://github.com/Sub6Resources/flutter_html) - A Flutter widget for rendering static html as Flutter widgets (Will render over 80 different html tags!)

*   [xujiyou/zhihu-flutter](https://github.com/xujiyou/zhihu-flutter) - Flutter 高仿知乎 UI，非常漂亮，也非常流畅。

*   [jayden320/flutter\_shuqi](https://github.com/jayden320/flutter_shuqi) - 高仿书旗小说 Flutter版，支持iOS、Android

*   [fluttercandies/flutter-interactive-chart](https://github.com/fluttercandies/flutter-interactive-chart) - A candlestick chart that supports pinch-to-zoom and panning.

*   [fluttercandies/flutter\_wechat\_assets\_picker](https://github.com/fluttercandies/flutter_wechat_assets_picker) - An image picker (also with videos and audios) for Flutter projects based on the WeChat's UI.

*   [fluttercandies/extended\_image](https://github.com/fluttercandies/extended_image) - A powerful official extension library of image, which support placeholder(loading)/ failed state, cache network, zoom pan image, photo view, slide out page, editor(crop,rotate,flip), paint custom etc.

*   [fluttercandies/extended\_text\_field](https://github.com/fluttercandies/extended_text_field) - extended official text field to quickly build special text like inline image, @somebody, custom background etc.

*   [bluefireteam/audioplayers](https://github.com/bluefireteam/audioplayers) - A Flutter package to play multiple audio files simultaneously (Android/iOS/web/Linux/Windows/macOS)

*   [lukepighetti/fluro](https://github.com/lukepighetti/fluro) - Fluro is a Flutter routing library that adds flexible routing options like wildcards, named parameters and clear route definitions.

*   [best-flutter/flutter\_swiper](https://github.com/best-flutter/flutter_swiper) - The best swiper for flutter , with multiple layouts, infinite loop. Compatible with Android & iOS.

*   [ibhavikmakwana/FlutterPlayground](https://github.com/ibhavikmakwana/FlutterPlayground) - Playground app for Flutter

*   [OpenFlutter/fluwx](https://github.com/OpenFlutter/fluwx) - Flutter版微信SDK.WeChat SDK for flutter.

*   [nisrulz/flutter-examples](https://github.com/nisrulz/flutter-examples) - \[Examples] Simple basic isolated apps, for budding flutter devs.

*   [FilledStacks/flutter-tutorials](https://github.com/FilledStacks/flutter-tutorials) - The repo contains the source code for all the tutorials on the FilledStacks Youtube channel.

*   [JideGuru/FlutterSocialAppUIKit](https://github.com/JideGuru/FlutterSocialAppUIKit) - Flutter representation of a Social App Concept.

*   [JideGuru/FlutterEbookApp](https://github.com/JideGuru/FlutterEbookApp) - A simple Flutter app to Read and Download eBooks.

*   [JideGuru/FlutterFoodybite](https://github.com/JideGuru/FlutterFoodybite) - Flutter representation of a Restaurant app UI.

*   [simplezhli/flutter\_deer](https://github.com/simplezhli/flutter_deer) - 🦌 Flutter 练习项目(包括集成测试、可访问性测试)。内含完整UI设计图，更贴近真实项目的练习。Flutter practice project (including integration testing and accessibility testing). Contains complete UI design drawings for a more realistic practice project.

*   [OpenFlutter/Flutter-Notebook](https://github.com/OpenFlutter/Flutter-Notebook) - FlutterDemo合集，今天你fu了吗

*   [flutterchina/nine\_grid\_view](https://github.com/flutterchina/nine_grid_view) - Flutter NineGridView & DragSortView. Similar to Weibo / WeChat nine grid view controls to display pictures. Flutter仿微信/微博九宫格、拖拽排序，微信群组，钉钉群组，QQ讨论组头像。

*   [Sky24n/common\_utils](https://github.com/Sky24n/common_utils) - Dart common utils library. DateUtil, EncryptUtil, JsonUtil, LogUtil, MoneyUtil, NumUtil, ObjectUtil,  RegexUtil, TextUtil, TimelineUtil, TimerUtil. 包含日期，正则，倒计时，时间轴等工具类。

*   [AweiLoveAndroid/Flutter-learning](https://github.com/AweiLoveAndroid/Flutter-learning) - :octocat::fire: :+1:  :star2:  :star: :star::star: Flutter all you want.Flutter install,flutter samples,Flutter projects,Flutter plugin,Flutter problems,Dart codes,etc.Flutter安装和配置，Flutter开发遇到的难题，Flutter示例代码和模板，Flutter项目实战，Dart语言学习示例代码。

*   [mitesh77/Best-Flutter-UI-Templates](https://github.com/mitesh77/Best-Flutter-UI-Templates) - completely free for everyone. Its build-in Flutter Dart.

*   [toly1994328/FlutterUnit](https://github.com/toly1994328/FlutterUnit) - 【Flutter 集录指南 App】The unity of flutter, The unity of coder.

*   [firebase/flutterfire](https://github.com/firebase/flutterfire) - 🔥 A collection of Firebase plugins for Flutter apps.

*   [samarthagarwal/FlutterScreens](https://github.com/samarthagarwal/FlutterScreens) - A collection of Screens and attractive UIs built with Flutter ready to be used in your applications. No external libraries are used. Just download, add to your project and use.

*   [iampawan/FlutterExampleApps](https://github.com/iampawan/FlutterExampleApps) - \[Example APPS] Basic Flutter apps, for flutter devs.

*   [flutter/plugins](https://github.com/flutter/plugins) - Plugins for Flutter maintained by the Flutter team

*   [Solido/awesome-flutter](https://github.com/Solido/awesome-flutter) - An awesome list that curates the best Flutter libraries, tools, tutorials, articles and more.

*   [flutter/flutter](https://github.com/flutter/flutter) - Flutter makes it easy and fast to build beautiful apps for mobile and beyond

## Java

*   [codecentric/spring-boot-admin](https://github.com/codecentric/spring-boot-admin) - Admin UI for administration of spring boot applications

*   [apache/hbase](https://github.com/apache/hbase) - Apache HBase

*   [alibaba/canal](https://github.com/alibaba/canal) - 阿里巴巴 MySQL binlog 增量订阅&消费组件

*   [seata/seata](https://github.com/seata/seata) - :fire: Seata is an easy-to-use, high-performance, open source distributed transaction solution.

*   [projectlombok/lombok](https://github.com/projectlombok/lombok) - Very spicy additions to the Java programming language.

*   [logfellow/logstash-logback-encoder](https://github.com/logfellow/logstash-logback-encoder) - Logback JSON encoder and appenders

*   [jwtk/jjwt](https://github.com/jwtk/jjwt) - Java JWT: JSON Web Token for Java and Android

*   [aliyun/aliyun-oss-java-sdk](https://github.com/aliyun/aliyun-oss-java-sdk) - Aliyun OSS SDK for Java

*   [alibaba/druid](https://github.com/alibaba/druid) - 阿里云计算平台DataWorks(https://help.aliyun.com/document\_detail/137663.html) 团队出品，为监控而生的数据库连接池

*   [elastic/elasticsearch](https://github.com/elastic/elasticsearch) - Free and Open, Distributed, RESTful Search Engine

*   [crossoverJie/cim](https://github.com/crossoverJie/cim) - 📲cim(cross IM) 适用于开发者的分布式即时通讯系统

*   [lenve/tienchin](https://github.com/lenve/tienchin) -

*   [jeequan/jeepay](https://github.com/jeequan/jeepay) - Jeepay是一套适合互联网企业使用的开源支付系统，支持多渠道服务商和普通商户模式。已对接微信支付，支付宝，云闪付官方接口，支持聚合码支付。

*   [dromara/lamp-cloud](https://github.com/dromara/lamp-cloud) - lamp-cloud 基于Jdk11 + SpringCloud + SpringBoot 开发的微服务中后台快速开发平台，专注于多租户(SaaS架构)解决方案，亦可作为普通项目（非SaaS架构）的基础开发框架使用，目前已实现插拔式数据库隔离、SCHEMA隔离、字段隔离 等租户隔离方案。

*   [alibaba/spring-cloud-alibaba](https://github.com/alibaba/spring-cloud-alibaba) - Spring Cloud Alibaba provides a one-stop solution for application development for the distributed solutions of Alibaba middleware.

*   [spring-cloud/spring-cloud-netflix](https://github.com/spring-cloud/spring-cloud-netflix) - Integration with Netflix OSS components

*   [spring-projects/spring-framework](https://github.com/spring-projects/spring-framework) - Spring Framework

*   [spring-projects/spring-boot](https://github.com/spring-projects/spring-boot) - Spring Boot

*   [pagehelper/Mybatis-PageHelper](https://github.com/pagehelper/Mybatis-PageHelper) - Mybatis通用分页插件

*   [mybatis/mybatis-3](https://github.com/mybatis/mybatis-3) - MyBatis SQL mapper framework for Java

*   [yangzongzhuan/RuoYi-Vue](https://github.com/yangzongzhuan/RuoYi-Vue) - :tada: (RuoYi)官方仓库 基于SpringBoot，Spring Security，JWT，Vue & Element 的前后端分离权限管理系统，同时提供了 Vue3 的版本

*   [woodwhales/woodwhales-springboot-xss](https://github.com/woodwhales/woodwhales-springboot-xss) - SpringBoot Xss 防御 DEMO 示例

*   [YunaiV/yudao-cloud](https://github.com/YunaiV/yudao-cloud) - ruoyi-vue-pro 全新 Cloud 版本，优化重构所有功能。基于 Spring Cloud Alibaba + MyBatis Plus + Vue & Element 实现的后台管理系统 + 用户小程序，支持 RBAC 动态权限、多租户、数据权限、工作流、三方登录、支付、短信、商城等功能。你的 ⭐️ Star ⭐️，是作者生发的动力！

*   [thymeleaf/thymeleaf](https://github.com/thymeleaf/thymeleaf) - Thymeleaf is a modern server-side Java template engine for both web and standalone environments.

*   [wuyouzhuguli/SpringAll](https://github.com/wuyouzhuguli/SpringAll) - 循序渐进，学习Spring Boot、Spring Boot & Shiro、Spring Batch、Spring Cloud、Spring Cloud Alibaba、Spring Security & Spring Security OAuth2，博客Spring系列源码：https://mrbird.cc

*   [xkcoding/spring-boot-demo](https://github.com/xkcoding/spring-boot-demo) - 🚀一个用来深入学习并实战 Spring Boot 的项目。

*   [527515025/springBoot](https://github.com/527515025/springBoot) - springboot 框架与其它组件结合如 jpa、mybatis、websocket、security、shiro、cache等

*   [codedrinker/community](https://github.com/codedrinker/community) - 开源论坛、问答系统，现有功能提问、回复、通知、最新、最热、消除零回复功能。功能持续更新中…… 技术栈 Spring、Spring Boot、MyBatis、MySQL/H2、Bootstrap

*   [Heeexy/SpringBoot-Shiro-Vue](https://github.com/Heeexy/SpringBoot-Shiro-Vue) - 提供一套基于Spring Boot-Shiro-Vue的权限管理思路.前后端都加以控制,做到按钮/接口级别的权限。（当前新版本已移除shiro依赖，简化了配置）

*   [yangzongzhuan/RuoYi-Vue-fast](https://github.com/yangzongzhuan/RuoYi-Vue-fast) - :tada: (RuoYi)官方仓库 基于SpringBoot，Spring Security，JWT，Vue & Element 的前后端分离权限管理系统

*   [apache/zookeeper](https://github.com/apache/zookeeper) - Apache ZooKeeper

*   [apache/kafka](https://github.com/apache/kafka) - Mirror of Apache Kafka

*   [alibaba/nacos](https://github.com/alibaba/nacos) - an easy-to-use dynamic service discovery, configuration and service management platform for building cloud native applications.

*   [fluttercommunity/flutter\_webview\_plugin](https://github.com/fluttercommunity/flutter_webview_plugin) - Community WebView Plugin - Allows Flutter to communicate with a native WebView.

*   [RAOE/show-videos](https://github.com/RAOE/show-videos) - 🍭短视频社交软件 ，微信小程序，后台管理系统，专科毕业设计，仿抖音，springcloud+springboot+springmvc+mybatis+docker+bootstrap+h plus+微信小程序

*   [apache/dubbo](https://github.com/apache/dubbo) - Apache Dubbo is a high-performance, java based, open source RPC framework.

*   [CarGuo/GSYVideoPlayer](https://github.com/CarGuo/GSYVideoPlayer) - 视频播放器（IJKplayer、ExoPlayer、MediaPlayer），HTTPS，支持弹幕，外挂字幕，支持滤镜、水印、gif截图，片头广告、中间广告，多个同时播放，支持基本的拖动，声音、亮度调节，支持边播边缓存，支持视频自带rotation的旋转（90,270之类），重力旋转与手动旋转的同步支持，支持列表播放 ，列表全屏动画，视频加载速度，列表小窗口支持拖动，动画效果，调整比例，多分辨率切换，支持切换播放器，进度条小窗口预览，列表切换详情页面无缝播放，rtsp、concat、mpeg。

*   [elunez/eladmin](https://github.com/elunez/eladmin) - 项目基于 Spring Boot 2.1.0 、 Jpa、 Spring Security、redis、Vue的前后端分离的后台管理系统，项目采用分模块开发方式， 权限控制采用 RBAC，支持数据字典与数据权限管理，支持一键生成前后端代码，支持动态路由

*   [ityouknow/spring-boot-examples](https://github.com/ityouknow/spring-boot-examples) - about learning Spring Boot via examples. Spring Boot 教程、技术栈示例代码，快速简单上手教程。

*   [newbee-ltd/newbee-mall](https://github.com/newbee-ltd/newbee-mall) - 🔥 🎉newbee-mall是一套电商系统，包括基础版本(Spring Boot+Thymeleaf)、前后端分离版本(Spring Boot+Vue 3+Element-Plus+Vue-Router 4+Pinia+Vant 4) 、秒杀版本、Go语言版本、微服务版本(Spring Cloud Alibaba+Nacos+Sentinel+Seata+Spring Cloud Gateway+OpenFeign+ELK)。 前台商城系统包含首页门户、商品分类、新品上线、首页轮播、商品推荐、商品搜索、商品展示、购物车、订单结算、订单流程、个人订单管理、会员中心、帮助中心等模块。 后台管理系统包含数据面板、轮播图管理、商品管理、订单管理、会员管理、分类管理、设置等模块。

*   [YunaiV/ruoyi-vue-pro](https://github.com/YunaiV/ruoyi-vue-pro) - 🔥 官方推荐 🔥 RuoYi-Vue 全新 Pro 版本，优化重构所有功能。基于 Spring Boot + MyBatis Plus + Vue & Element 实现的后台管理系统 + 微信小程序，支持 RBAC 动态权限、数据权限、SaaS 多租户、Flowable 工作流、三方登录、支付、短信、商城等功能。你的 ⭐️ Star ⭐️，是作者生发的动力！

*   [yudaocode/SpringBoot-Labs](https://github.com/yudaocode/SpringBoot-Labs) - 一个涵盖六个专栏：Spring Boot 2.X、Spring Cloud、Spring Cloud Alibaba、Dubbo、分布式消息队列、分布式事务的仓库。希望胖友小手一抖，右上角来个 Star，感恩 1024

*   [CodingDocs/springboot-guide](https://github.com/CodingDocs/springboot-guide) - SpringBoot2.0+从入门到实战！

*   [hustcc/JS-Sorting-Algorithm](https://github.com/hustcc/JS-Sorting-Algorithm) - 一本关于排序算法的 GitBook 在线书籍 《十大经典排序算法》，多语言实现。

*   [facebook/react-native](https://github.com/facebook/react-native) - A framework for building native applications using React

*   [macrozheng/mall](https://github.com/macrozheng/mall) - mall项目是一套电商系统，包括前台商城系统及后台管理系统，基于SpringBoot+MyBatis实现，采用Docker容器化部署。 前台商城系统包含首页门户、商品推荐、商品搜索、商品展示、购物车、订单流程、会员中心、客户服务、帮助中心等模块。 后台管理系统包含商品管理、订单管理、会员管理、促销管理、运营管理、内容管理、统计报表、财务管理、权限管理、设置等模块。

*   [justauth/JustAuth](https://github.com/justauth/JustAuth) - 🏆Gitee 最有价值开源项目 🚀:100: 小而全而美的第三方登录开源组件。目前已支持Github、Gitee、微博、钉钉、百度、Coding、腾讯云开发者平台、OSChina、支付宝、QQ、微信、淘宝、Google、Facebook、抖音、领英、小米、微软、今日头条、Teambition、StackOverflow、Pinterest、人人、华为、企业微信、酷家乐、Gitlab、美团、饿了么、推特、飞书、京东、阿里云、喜马拉雅、Amazon、Slack和 Line 等第三方平台的授权登录。 Login, so easy!

*   [dromara/Sa-Token](https://github.com/dromara/Sa-Token) - 这可能是史上功能最全的Java权限认证框架！目前已集成——登录认证、权限认证、分布式Session会话、微服务网关鉴权、单点登录、OAuth2.0、踢人下线、Redis集成、前后台分离、记住我模式、模拟他人账号、临时身份切换、账号封禁、多账号认证体系、注解式鉴权、路由拦截式鉴权、花式token生成、自动续签、同端互斥登录、会话治理、密码加密、jwt集成、Spring集成、WebFlux集成...

*   [lenve/vhr](https://github.com/lenve/vhr) - 微人事是一个前后端分离的人力资源管理系统，项目采用SpringBoot+Vue开发。

*   [ifnoelse/pdf-bookmark](https://github.com/ifnoelse/pdf-bookmark) - pdf bookmark generator 目录 书签 大纲

*   [jeecgboot/JimuReport](https://github.com/jeecgboot/JimuReport) - 🔥「低代码可视化报表」类似excel操作风格，在线拖拽完成设计！功能涵盖: 报表设计、图形报表、打印设计、大屏设计等，完全免费！秉承“简单、易用、专业”的产品理念，极大的降低报表开发难度、缩短开发周期、解决各类报表难题。

*   [GrowingGit/GitHub-Chinese-Top-Charts](https://github.com/GrowingGit/GitHub-Chinese-Top-Charts) - :cn: GitHub中文排行榜，各语言分设「软件 | 资料」榜单，精准定位中文好项目。各取所需，高效学习。

*   [MisterBooo/LeetCodeAnimation](https://github.com/MisterBooo/LeetCodeAnimation) - Demonstrate all the questions on LeetCode in the form of animation.（用动画的形式呈现解LeetCode题目的思路）

*   [xiaoqi6666/NYCSDE](https://github.com/xiaoqi6666/NYCSDE) - 公众号【码农田小齐】的分类合集

*   [geekxh/hello-algorithm](https://github.com/geekxh/hello-algorithm) - 🌍 针对小白的算法训练 | 包括四部分：①.大厂面经 ②.力扣图解  ③.千本开源电子书 ④.百张技术思维导图（项目花了上百小时，希望可以点 star 支持，🌹感谢~）推荐免费ChatGPT使用网站

*   [xenv/gushici](https://github.com/xenv/gushici) - 一言·古诗词 API (Hitokoto API)，随机返回一条古诗词名句。采用  Vert.x + Redis 全异步开发，毫秒级稳定响应。

## Vue

*   [roncoo/roncoo-education-web](https://github.com/roncoo/roncoo-education-web) - 《领课教育》的前端门户系统。领课教育系统（roncoo-education）是基于领课网络多年的在线教育平台开发和运营经验打造出来的产品，致力于打造一个全行业都适用的分布式在线教育系统。

*   [roncoo/roncoo-education-admin](https://github.com/roncoo/roncoo-education-admin) - 《领课教育》的后台管理系统。领课教育系统（roncoo-education）是基于领课网络多年的在线教育平台开发和运营经验打造出来的产品，致力于打造一个全行业都适用的分布式在线教育系统。

*   [likaia/chat-system](https://github.com/likaia/chat-system) - 本项目是一个在线聊天系统，最大程度的还原了Mac客户端QQ。

*   [reinerBa/Vue-Responsive](https://github.com/reinerBa/Vue-Responsive) - A plugin for responsive handling with vue.js

*   [Rudeus3Greyrat/vue3-element-admin](https://github.com/Rudeus3Greyrat/vue3-element-admin) - A vue3 version of vue-element-admin

*   [umicro/uView2.0](https://github.com/umicro/uView2.0) - uView UI，是全面兼容nvue的uni-app生态框架，全面的组件和便捷的工具会让您信手拈来，如鱼得水

*   [AnsGoo/openDataV](https://github.com/AnsGoo/openDataV) - OpenDataV 是一个纯前端的拖拽式、可视化、低代码数据可视化🌈开发平台，你可以用它自由的拼接成各种✨炫酷的大屏，同时支持用户方便的开发自己的组件并接入平台。

*   [yangzongzhuan/RuoYi-Vue3](https://github.com/yangzongzhuan/RuoYi-Vue3) - :tada: (RuoYi)官方仓库 基于SpringBoot，Spring Security，JWT，Vue3 & Vite、Element Plus 的前后端分离权限管理系统

*   [DataV-Team/DataV](https://github.com/DataV-Team/DataV) - Vue数据可视化组件库（类似阿里DataV，大屏数据展示），提供SVG的边框及装饰、图表、水位图、飞线图等组件，简单易用，长期更新(React版已发布)

*   [Armour/vue-typescript-admin-template](https://github.com/Armour/vue-typescript-admin-template) - 🖖 A vue-cli 3.0 + typescript minimal admin template

*   [webVueBlog/vue3-vite-pinia-template](https://github.com/webVueBlog/vue3-vite-pinia-template) - 企业级前端开发与构建框架 Vite + Vue3 + TypeScript + Vue-Router4 + Pinia + Tailwind CSS + ant-design-vueTemplate.

*   [webVueBlog/uui](https://github.com/webVueBlog/uui) - 🖖 【uui组件库】A vue-cli 3.0 + vue + typeScript + babel + eslint + unit-mocha + scss + chai + karma。

*   [hinesboy/mavonEditor](https://github.com/hinesboy/mavonEditor) - mavonEditor - A markdown editor based on Vue that supports a variety of personalized features

*   [kailong321200875/vue-element-plus-admin](https://github.com/kailong321200875/vue-element-plus-admin) - A set of background integration scheme based on vue3, element-plus, typescript4 and vite4

*   [webVueBlog/vue3-vite2-ts4](https://github.com/webVueBlog/vue3-vite2-ts4) - 🎲一套规范的vue3+vite2+ts4前端工程化项目环境 https://webvueblog.github.io/vue3-vite2-ts4/

*   [yleencc/vue-barrage-videoplayer](https://github.com/yleencc/vue-barrage-videoplayer) - vue-弹幕视频播放器，一个基于Vue的弹幕视频播放器组件

*   [buqiyuan/vite-vue3-admin](https://github.com/buqiyuan/vite-vue3-admin) - 基于vite2.x + vue3.x + ant-design-vue3.x + typescript hooks 的基础后台管理系统模板 RBAC的权限系统, JSON Schema动态表单,动态表格,漂亮锁屏界面

*   [lybenson/bilibili-vue](https://github.com/lybenson/bilibili-vue) - 前端vue+后端koa，全栈式开发bilibili首页

*   [jeecgboot/jeecgboot-vue3](https://github.com/jeecgboot/jeecgboot-vue3) - 🔥JeecgBoot—Vue3版前端源码，采用 Vue3.0+TypeScript+Vite+Ant-Design-Vue等新技术方案，包括二次封装组件、utils、hooks、动态菜单、权限校验、按钮级别权限控制等功能。 是JeecgBoot低代码平台的vue3技术栈的全新UI版本，功能强于vue2版。

*   [Codennnn/vue-color-avatar](https://github.com/Codennnn/vue-color-avatar) - An online avatar generator just for fun | 一个纯前端实现的头像生成网站

*   [joyceworks/flowchart-vue](https://github.com/joyceworks/flowchart-vue) - Flowchart & designer component for Vue.js.

*   [doocs/md](https://github.com/doocs/md) - ✍ WeChat Markdown Editor | 一款高度简洁的微信 Markdown 编辑器：支持 Markdown 语法、色盘取色、多图上传、一键下载文档、自定义 CSS 样式、一键重置等特性

*   [PanJiaChen/vue-element-admin](https://github.com/PanJiaChen/vue-element-admin) - :tada: A magical vue admin                                                                https://panjiachen.github.io/vue-element-admin

*   [vuese/vuese-explorer](https://github.com/vuese/vuese-explorer) - 🏄An online experience playground for vuese

*   [varletjs/varlet-vue2](https://github.com/varletjs/varlet-vue2) - Material design mobile component library for Vue2 / 基于 Vue2 的 Material design 风格移动端组件库

*   [varletjs/varlet](https://github.com/varletjs/varlet) - Material design mobile component library for Vue3

*   [sdras/cssgridgenerator](https://github.com/sdras/cssgridgenerator) - 🧮 Generate basic CSS Grid code to make dynamic layouts!

*   [learn-docs/vue-docs](https://github.com/learn-docs/vue-docs) - 🔥 vue-docs https://learn-docs.github.io/vue-docs/

*   [vbenjs/vue-vben-admin](https://github.com/vbenjs/vue-vben-admin) - A modern vue admin. It is based on Vue3, vite and TypeScript. It's fast！

*   [ppchart/ppchart](https://github.com/ppchart/ppchart) - http://ppchart.com

*   [pure-admin/vue-pure-admin](https://github.com/pure-admin/vue-pure-admin) - 🔥 ✨✨ ✨ Vue3+Vite4+Element-Plus+TypeScript编写的一款后台管理系统（兼容移动端）

*   [xiaokaike/vue-color](https://github.com/xiaokaike/vue-color) - :art: Vue Color Pickers for Sketch, Photoshop, Chrome & more   http://vue-color.surge.sh

*   [xlsdg/vue-countup-v2](https://github.com/xlsdg/vue-countup-v2) - Vue.js component wrap for countUp.js

*   [fu4303/vue-splitpanes](https://github.com/fu4303/vue-splitpanes) -

*   [Akryum/vue-virtual-scroller](https://github.com/Akryum/vue-virtual-scroller) - ⚡️ Blazing fast scrolling for any amount of data

*   [notadd/vue-screen-capture](https://github.com/notadd/vue-screen-capture) - 基于 html2canvas 的vue截图组件

*   [sdras/vue-sample-svg-icons](https://github.com/sdras/vue-sample-svg-icons) - An opinionated example of how to use SVG icons in a Vue.js application

*   [ITmonkey-cn/shopro-uniapp](https://github.com/ITmonkey-cn/shopro-uniapp) - Shopro分销商城 uniapp前端开源代码，一款落地生产的 基于uni-app的多端商城。使用文档：https://gitee.com/itmonkey-cn/shopro.git

*   [view-design/ViewUI](https://github.com/view-design/ViewUI) - A high quality UI Toolkit built on Vue.js 2.0

*   [vueComponent/ant-design-vue](https://github.com/vueComponent/ant-design-vue) - 🌈  An enterprise-class UI components based on Ant Design and Vue. 🐜

*   [chuzhixin/vue-admin-better](https://github.com/chuzhixin/vue-admin-better) - 🚀🚀🚀vue admin,vue3 admin,vue3.0 admin,vue后台管理,vue-admin,vue3.0-admin,admin,vue-admin,vue-element-admin,ant-design,vue-admin-beautiful-pro,vab admin pro,vab admin plus,vue admin plus,vue admin pro

*   [maomao1996/Vue-mmPlayer](https://github.com/maomao1996/Vue-mmPlayer) - 🎵 基于 Vue 的在线音乐播放器 Online music player

*   [vincentzyc/form-design](https://github.com/vincentzyc/form-design) - 动态表单页面设计--自动生成页面

*   [lin-xin/vue-manage-system](https://github.com/lin-xin/vue-manage-system) - 基于Vue3 + Element Plus 的后台管理系统解决方案

*   [caohuatao/vue-super-flow](https://github.com/caohuatao/vue-super-flow) - Flow chart component based on Vue。vue flowchart

*   [bailicangdu/vue2-elm](https://github.com/bailicangdu/vue2-elm) - Large single page application with 45 pages built on vue2 + vuex. 基于 vue2 + vuex 构建一个具有 45 个页面的大型单页面应用

*   [JakHuang/form-generator](https://github.com/JakHuang/form-generator) - :sparkles:Element UI表单设计及代码生成器

*   [ElemeFE/element](https://github.com/ElemeFE/element) - A Vue.js 2.0 UI Toolkit for Web

*   [sunniejs/vant-shop-demo](https://github.com/sunniejs/vant-shop-demo) - 商城常用的组件开发基于 vant ui 开发，让商城开发变得更简单

*   [ElemeFE/mint-ui](https://github.com/ElemeFE/mint-ui) - Mobile UI elements for Vue.js

*   [iview/iview-admin](https://github.com/iview/iview-admin) - Vue 2.0 admin management system template based on iView

*   [bailichen/vue-weixin](https://github.com/bailichen/vue-weixin) - Vue2 全家桶仿 微信App 项目，支持多人在线聊天和机器人聊天

## Objective-C

*   [ccgus/fmdb](https://github.com/ccgus/fmdb) - A Cocoa / Objective-C wrapper around SQLite

*   [fikovnik/ShiftIt](https://github.com/fikovnik/ShiftIt) - Managing windows size and position in OSX

## JavaScript

*   [dushixiang/kafka-map](https://github.com/dushixiang/kafka-map) - A beautiful, concise and powerful kafka web management tool. 一个美观简洁且强大的kafka web管理工具。

*   [swagger-api/swagger-ui](https://github.com/swagger-api/swagger-ui) - Swagger UI is a collection of HTML, JavaScript, and CSS assets that dynamically generate beautiful documentation from a Swagger-compliant API.

*   [google/zx](https://github.com/google/zx) - A tool for writing better scripts

*   [xcanwin/KeepChatGPT](https://github.com/xcanwin/KeepChatGPT) - 这是一个ChatGPT的畅聊与增强插件。开源免费。不仅能解决所有报错不再刷新，还有保持活跃、取消审计、克隆对话、净化首页、展示大屏、展示全屏、言无不尽、拦截跟踪、日新月异等多个高级功能。让我们的AI体验无比顺畅、丝滑、高效、简洁。

*   [chrisjpatty/crooks](https://github.com/chrisjpatty/crooks) - A collection of eclectic react hooks

*   [syhyz1990/baiduyun](https://github.com/syhyz1990/baiduyun) - 油猴脚本 - 一个免费开源的网盘下载助手

*   [bxm0927/canvas-special](https://github.com/bxm0927/canvas-special) - :octocat::alien::star2:超多经典 Canvas 实例，动态离子背景、炫彩小球、贪吃蛇、坦克大战、是男人就下100层、心形文字等。

*   [MatteoGabriele/vue-analytics](https://github.com/MatteoGabriele/vue-analytics) - Google Analytics plugin for Vue

*   [DataV-Team/datav.jiaminghi.com](https://github.com/DataV-Team/datav.jiaminghi.com) - DataV组件库文档

*   [yyhsong/iDataV](https://github.com/yyhsong/iDataV) - 大屏数据可视化 Big screen data visualization demo

*   [Sunny-117/js-challenges](https://github.com/Sunny-117/js-challenges) - ✨✨✨ 集锦 2022-2023年 前端JavaScript 手写题，编程题，Not just for interviews

*   [Jameszws/monitorjs\_horse](https://github.com/Jameszws/monitorjs_horse) - 前端异常监控、vue错误监控、js错误监控、页面性能监控、设备信息采集

*   [dunwu/nginx-tutorial](https://github.com/dunwu/nginx-tutorial) - 这是一个 Nginx 极简教程，目的在于帮助新手快速入门 Nginx。

*   [webVueBlog/nice-my-friend](https://github.com/webVueBlog/nice-my-friend) - 😳轻松查看和过滤所有关注和关注。通过 GitHub Action 自动更新。

*   [webVueBlog/WebGuideInterview](https://github.com/webVueBlog/WebGuideInterview) - 「WebGuideInterview学习」每日 3+1，以面试题来驱动学习，提倡每日学习与思考，每天进步一点！每天早上纯手工发布（死磕自己，愉悦大家）准备 前端 面试，首选 WebGuideInterview！面试题大收集，面试集锦 ❤ 💝 💘

*   [webVueBlog/koa2-login-registration](https://github.com/webVueBlog/koa2-login-registration) - koa2-login-registration Koa2实现基本的登录注册

*   [webVueBlog/file-breakpoint-continue](https://github.com/webVueBlog/file-breakpoint-continue) - 🐬 实现大文件📄上传，断点续传等💎

*   [webVueBlog/mini-vue](https://github.com/webVueBlog/mini-vue) - vue超详细逐行解析版源码，手写，算法，javascript等

*   [skys215/regexr-cn](https://github.com/skys215/regexr-cn) - RegExr 是一款用于测试和学习正则表达式的，基于 HTML/JS 的工具。

*   [FortAwesome/Font-Awesome](https://github.com/FortAwesome/Font-Awesome) - The iconic SVG, font, and CSS toolkit

*   [react-grid-layout/react-draggable](https://github.com/react-grid-layout/react-draggable) - React draggable component

*   [Shopify/draggable](https://github.com/Shopify/draggable) - The JavaScript Drag & Drop library your grandparents warned you about.

*   [luzhixing12345/ChatRoom](https://github.com/luzhixing12345/ChatRoom) - 微信小程序 在线聊天

*   [Meituan-Dianping/mpvue](https://github.com/Meituan-Dianping/mpvue) - 基于 Vue.js 的小程序开发框架，从底层支持 Vue.js 语法和构建工具体系。

*   [sequelize/sequelize](https://github.com/sequelize/sequelize) - Feature-rich ORM for modern Node.js and TypeScript, it supports PostgreSQL (with JSON and JSONB support), MySQL, MariaDB, SQLite, MS SQL Server, Snowflake, Oracle DB (v6), DB2 and DB2 for IBM i.

*   [ThatGuySam/doesitarm](https://github.com/ThatGuySam/doesitarm) - 🦾 A list of reported app support for Apple Silicon as well as Apple M2 and M1 Ultra Macs

*   [Akryum/vue-resize](https://github.com/Akryum/vue-resize) - A generic component to detect DOM elements resizing

*   [webVueBlog/electron-vue](https://github.com/webVueBlog/electron-vue) - electron-vue 实战

*   [webVueBlog/web-audio-video](https://github.com/webVueBlog/web-audio-video) - 📺 研究方向音视频相关领域

*   [webVueBlog/leetcode-javascript](https://github.com/webVueBlog/leetcode-javascript) - Collection of LeetCode questions to ace the coding interview!

*   [webVueBlog/Leetcode](https://github.com/webVueBlog/Leetcode) - 🎲【每日更新 question & answers】一个 ☝️ 正经的前端学习，每天进步一点点！手写源码，api，算法；包含JavaScript / Vue / React /  TypeScript /HTML / CSS / Nodejs / Leetcode……Suggest 👍

*   [webVueBlog/promise](https://github.com/webVueBlog/promise) - ♥ Bare bones Promises/A+ implementation 简单的 Promises/A+ 实现

*   [webVueBlog/tailwindcss-chinese](https://github.com/webVueBlog/tailwindcss-chinese) - 🤖 国内tailwindcss平台从业者交流，Github Actions自动化部署

*   [webVueBlog/todolist-vue](https://github.com/webVueBlog/todolist-vue) - 用 Todoist 组织一切，管理工作和生活的To Do List，使用 Vite、Vue 和 Vuex 构建的 TodoMVC

*   [webVueBlog/Vite-Vue3-TypeScript](https://github.com/webVueBlog/Vite-Vue3-TypeScript) - 🎲一套规范的 Vite + Vue3 + TypeScript 前端工程化项目环境

*   [eggjs/egg-sequelize](https://github.com/eggjs/egg-sequelize) - Sequelize for Egg.js

*   [eggjs/egg](https://github.com/eggjs/egg) - 🥚 Born to build better enterprise frameworks and apps with Node.js & Koa

*   [yukilzw/web\_channel](https://github.com/yukilzw/web_channel) - :pencil2: 搭建设计编辑器

*   [eggjs/egg-socket.io](https://github.com/eggjs/egg-socket.io) - socket.io plugin for eggjs.

*   [MetinSeylan/Vue-Socket.io](https://github.com/MetinSeylan/Vue-Socket.io) - 😻 Socket.io implementation for Vuejs and Vuex

*   [rzcoder/node-rsa](https://github.com/rzcoder/node-rsa) - Node.js RSA library

*   [node-formidable/formidable](https://github.com/node-formidable/formidable) - The most used, flexible, fast and streaming parser for multipart form data. Supports uploading to serverless environments, AWS S3, Azure, GCP or the filesystem. Used in production.

*   [chrisvfritz/prerender-spa-plugin](https://github.com/chrisvfritz/prerender-spa-plugin) - Prerenders static HTML in a single-page application.

*   [emmetio/codemirror](https://github.com/emmetio/codemirror) - Emmet plugin for CodeMirror online editor

*   [nhn/raphael](https://github.com/nhn/raphael) - JavaScript Vector Library

*   [goabstract/Awesome-Design-Tools](https://github.com/goabstract/Awesome-Design-Tools) - The best design tools and plugins for everything 👉

*   [jaywcjlove/awesome-mac](https://github.com/jaywcjlove/awesome-mac) -  Now we have become very big, Different from the original idea. Collect premium software in various categories.

*   [sindresorhus/clipboardy](https://github.com/sindresorhus/clipboardy) - Access the system clipboard (copy/paste)

*   [sindresorhus/open](https://github.com/sindresorhus/open) - Open stuff like URLs, files, executables. Cross-platform.

*   [hexojs/hexo](https://github.com/hexojs/hexo) - A fast, simple & powerful blog framework, powered by Node.js.

*   [strapi/strapi](https://github.com/strapi/strapi) - 🚀 Strapi is the leading open-source headless CMS. It’s 100% JavaScript, fully customizable and developer-first.

*   [apostrophecms/apostrophe](https://github.com/apostrophecms/apostrophe) - Apostrophe is a full-featured, open-source CMS built with Node.js that empowers organizations by combining in-context editing and headless architecture in a full-stack JS environment.

*   [coreybutler/node-windows](https://github.com/coreybutler/node-windows) - Windows support for Node.JS scripts (daemons, eventlog, UAC, etc).

*   [coreybutler/node-mac](https://github.com/coreybutler/node-mac) - Node utilities for Mac

*   [remy/nodemon](https://github.com/remy/nodemon) - Monitor for any changes in your node.js application and automatically restart the server - perfect for development

*   [Unitech/pm2](https://github.com/Unitech/pm2) - Node.js Production Process Manager with a built-in Load Balancer.

*   [bee-queue/bee-queue](https://github.com/bee-queue/bee-queue) - A simple, fast, robust job/task queue for Node.js, backed by Redis.

*   [smrchy/rsmq](https://github.com/smrchy/rsmq) - Redis Simple Message Queue

*   [OptimalBits/bull](https://github.com/OptimalBits/bull) - Premium Queue package for handling distributed jobs and messages in NodeJS.

*   [clean-css/clean-css](https://github.com/clean-css/clean-css) - Fast and efficient CSS optimizer for node.js and the Web

*   [mishoo/UglifyJS](https://github.com/mishoo/UglifyJS) -  JavaScript parser / mangler / compressor / beautifier toolkit

*   [animir/node-rate-limiter-flexible](https://github.com/animir/node-rate-limiter-flexible) - Count and limit requests by key with atomic increments in single process or distributed environment.

*   [mysqljs/mysql](https://github.com/mysqljs/mysql) - A pure node.js JavaScript Client implementing the MySQL protocol.

*   [sindresorhus/ipify](https://github.com/sindresorhus/ipify) - Get your public IP address

*   [esdoc/esdoc](https://github.com/esdoc/esdoc) - ESDoc - Good Documentation for JavaScript

*   [documentationjs/documentation](https://github.com/documentationjs/documentation) - :book: documentation for modern JavaScript

*   [vercel/next.js](https://github.com/vercel/next.js) - The React Framework

*   [GoogleChromeLabs/ndb](https://github.com/GoogleChromeLabs/ndb) - ndb is an improved debugging experience for Node.js, enabled by Chrome DevTools

*   [debug-js/debug](https://github.com/debug-js/debug) - A tiny JavaScript debugging utility modelled after Node.js core's debugging technique. Works in Node.js and web browsers

*   [kefirjs/kefir](https://github.com/kefirjs/kefir) - A Reactive Programming library for JavaScript

*   [mout/mout](https://github.com/mout/mout) - Modular JavaScript Utilities

*   [origamitower/folktale](https://github.com/origamitower/folktale) - \[not actively maintained!] A standard library for functional programming in JavaScript

*   [ramda/ramda](https://github.com/ramda/ramda) - :ram: Practical functional Javascript

*   [mafintosh/webcat](https://github.com/mafintosh/webcat) - Mad science p2p pipe across the web using webrtc that uses your Github private/public key for authentication and a signalhub for discovery

*   [Turfjs/turf](https://github.com/Turfjs/turf) - A modular geospatial engine written in JavaScript

*   [foliojs/pdfkit](https://github.com/foliojs/pdfkit) - A JavaScript PDF generation library for Node and the browser

*   [bitpay/bitcore](https://github.com/bitpay/bitcore) - A full stack for bitcoin and blockchain-based applications

*   [ipfs/js-ipfs](https://github.com/ipfs/js-ipfs) - IPFS implementation in JavaScript

*   [mafintosh/peerflix](https://github.com/mafintosh/peerflix) - Streaming torrent client for node.js

*   [webtorrent/webtorrent](https://github.com/webtorrent/webtorrent) - ⚡️ Streaming torrent client for the web

*   [DIYgod/DPlayer](https://github.com/DIYgod/DPlayer) - :lollipop: Wow, such a lovely HTML5 danmaku video player

*   [xinglie/page-designer](https://github.com/xinglie/page-designer) - 🚀 可视化、编辑器、页面设计，设计器、报表设计、组件化、表单设计、h5页面、调查问卷

*   [gaearon/overreacted.io](https://github.com/gaearon/overreacted.io) - Personal blog by Dan Abramov.

*   [shfshanyue/blog](https://github.com/shfshanyue/blog) - 在这里写一些工作中遇到的前端，后端以及运维的问题

*   [nefe/redux-in-chinese](https://github.com/nefe/redux-in-chinese) - Redux 中文文档

*   [nswbmw/N-blog](https://github.com/nswbmw/N-blog) - 《一起学 Node.js》

*   [gskinner/regexr](https://github.com/gskinner/regexr) - RegExr is a HTML/JS based tool for creating, testing, and learning about Regular Expressions.

*   [sudheerj/reactjs-interview-questions](https://github.com/sudheerj/reactjs-interview-questions) - List of top 500 ReactJS Interview Questions & Answers....Coding exercise questions are coming soon!!

*   [d3/d3](https://github.com/d3/d3) - Bring data to life with SVG, Canvas and HTML. :bar\_chart::chart\_with\_upwards\_trend::tada:

*   [webVueBlog/express-node](https://github.com/webVueBlog/express-node) - ⚡ express-node-mysql-react全家桶

*   [bostrt/wordcount.js](https://github.com/bostrt/wordcount.js) - Calculate file newlines, word, and byte counts on client side using HTML5 File API. (Emulates Linux's wc command)

*   [cpojer/vite-ts-react-tailwind-template](https://github.com/cpojer/vite-ts-react-tailwind-template) - Minimal, sensible defaults, fast.

*   [jondot/awesome-react-native](https://github.com/jondot/awesome-react-native) - Awesome React Native components, news, tools, and learning material!

*   [BetaSu/just-react](https://github.com/BetaSu/just-react) - 「React技术揭秘」  一本自顶向下的React源码分析书

*   [jaweii/Vue-Layout](https://github.com/jaweii/Vue-Layout) - 基于UI组件的Vue可视化布局工具

*   [tnfe/FFCreator](https://github.com/tnfe/FFCreator) - 一个基于node.js的高速视频制作库  A fast video processing library based on node.js

*   [gwuhaolin/ui-component-loader](https://github.com/gwuhaolin/ui-component-loader) - Modular UI component loader for webpack, a good alternative for babel-plugin-import.

*   [cherrry/ignore-loader](https://github.com/cherrry/ignore-loader) - Webpack loader to ignore certain package on build.

*   [webpack-contrib/i18n-loader](https://github.com/webpack-contrib/i18n-loader) - i18n loader module for webpack - UNMAINTAINED

*   [webpack-contrib/coverjs-loader](https://github.com/webpack-contrib/coverjs-loader) - coverjs loader module for webpack - UNMAINTAINED

*   [webpack-contrib/mocha-loader](https://github.com/webpack-contrib/mocha-loader) - Mocha Loader

*   [wbuchwalter/tslint-loader](https://github.com/wbuchwalter/tslint-loader) - tslint loader for webpack

*   [webpack-contrib/eslint-loader](https://github.com/webpack-contrib/eslint-loader) - \[DEPRECATED] A ESlint loader for webpack

*   [webpack-contrib/stylus-loader](https://github.com/webpack-contrib/stylus-loader) - :art: A stylus loader for webpack.

*   [webpack-contrib/less-loader](https://github.com/webpack-contrib/less-loader) - Compiles Less to CSS

*   [webpack-contrib/postcss-loader](https://github.com/webpack-contrib/postcss-loader) - PostCSS loader for webpack

*   [webpack-contrib/sass-loader](https://github.com/webpack-contrib/sass-loader) - Compiles Sass to CSS

*   [webpack-contrib/style-loader](https://github.com/webpack-contrib/style-loader) - Style Loader

*   [webpack-contrib/css-loader](https://github.com/webpack-contrib/css-loader) - CSS Loader

*   [webpack-contrib/coffee-loader](https://github.com/webpack-contrib/coffee-loader) - CoffeeScript Loader

*   [babel/babel-loader](https://github.com/babel/babel-loader) - 📦 Babel loader for webpack

*   [peerigon/markdown-loader](https://github.com/peerigon/markdown-loader) - markdown loader for webpack

*   [AlexanderPavlenko/haml-loader](https://github.com/AlexanderPavlenko/haml-loader) -

*   [difelice/ejs-loader](https://github.com/difelice/ejs-loader) - EJS (Underscore/LoDash Templates) loader for webpack

*   [pcardune/handlebars-loader](https://github.com/pcardune/handlebars-loader) - A handlebars template loader for webpack

*   [pugjs/pug-loader](https://github.com/pugjs/pug-loader) - Pug loader module for Webpack

*   [eemeli/yaml-loader](https://github.com/eemeli/yaml-loader) - YAML loader for webpack

*   [webpack-contrib/json-loader](https://github.com/webpack-contrib/json-loader) - json loader module for webpack - UNMAINTAINED

*   [tcoopman/image-webpack-loader](https://github.com/tcoopman/image-webpack-loader) - Image loader module for webpack

*   [webpack-contrib/node-loader](https://github.com/webpack-contrib/node-loader) - node loader for native modules

*   [webpack-contrib/svg-inline-loader](https://github.com/webpack-contrib/svg-inline-loader) - Inline SVG loader with cleaning-up functionality

*   [webpack-contrib/source-map-loader](https://github.com/webpack-contrib/source-map-loader) - extract sourceMappingURL comments from modules and offer it to webpack

*   [webpack-contrib/url-loader](https://github.com/webpack-contrib/url-loader) - A loader for webpack which transforms files into base64 URIs

*   [webpack-contrib/file-loader](https://github.com/webpack-contrib/file-loader) - File Loader

*   [webpack-contrib/raw-loader](https://github.com/webpack-contrib/raw-loader) -  A loader for webpack that allows importing files as a String

*   [gwuhaolin/web-webpack-plugin](https://github.com/gwuhaolin/web-webpack-plugin) - alternative for html-webpack-plugin

*   [webpack-contrib/i18n-webpack-plugin](https://github.com/webpack-contrib/i18n-webpack-plugin) - \[DEPRECATED] Embed localization into your bundle

*   [webpack-contrib/stylelint-webpack-plugin](https://github.com/webpack-contrib/stylelint-webpack-plugin) - A Stylelint plugin for webpack

*   [oliviertassinari/serviceworker-webpack-plugin](https://github.com/oliviertassinari/serviceworker-webpack-plugin) - Simplifies creation of a service worker to serve your webpack bundles. :recycle:

*   [Klathmon/imagemin-webpack-plugin](https://github.com/Klathmon/imagemin-webpack-plugin) - Plugin to compress images with imagemin

*   [mixtur/webpack-spritesmith](https://github.com/mixtur/webpack-spritesmith) - Webpack plugin that converts set of images into a spritesheet and SASS/LESS/Stylus mixins

*   [gdborton/webpack-parallel-uglify-plugin](https://github.com/gdborton/webpack-parallel-uglify-plugin) - A faster uglifyjs plugin.

*   [webpack-contrib/uglifyjs-webpack-plugin](https://github.com/webpack-contrib/uglifyjs-webpack-plugin) - \[deprecated] UglifyJS Plugin

*   [gajus/prepack-webpack-plugin](https://github.com/gajus/prepack-webpack-plugin) - A webpack plugin for prepack.

*   [webpack-contrib/extract-text-webpack-plugin](https://github.com/webpack-contrib/extract-text-webpack-plugin) - \[DEPRECATED] Please use https://github.com/webpack-contrib/mini-css-extract-plugin Extracts text from a bundle into a separate file

*   [miracle90/browser-render](https://github.com/miracle90/browser-render) - 用js模拟浏览器渲染流程

*   [diego3g/electron-typescript-react](https://github.com/diego3g/electron-typescript-react) - :electron: An Electron boilerplate including TypeScript, React, Jest and ESLint.

*   [Eschere/react-editor-component](https://github.com/Eschere/react-editor-component) - UEditor wrapped by React Component

*   [haochuan9421/vue-ueditor-wrap](https://github.com/haochuan9421/vue-ueditor-wrap) - 🚴Vue + 🚄UEditor + v-model双向绑定🚀

*   [withspectrum/spectrum](https://github.com/withspectrum/spectrum) - Simple, powerful online communities.

*   [fkling/astexplorer](https://github.com/fkling/astexplorer) - A web tool to explore the ASTs generated by various parsers.

*   [bbc/simorgh](https://github.com/bbc/simorgh) - The BBC's Open Source Single Page Application. Contributions welcome! Used on some of our biggest websites, e.g.

*   [gothinkster/react-redux-realworld-example-app](https://github.com/gothinkster/react-redux-realworld-example-app) - Exemplary real world application built with React + Redux

*   [oldboyxx/jira\_clone](https://github.com/oldboyxx/jira_clone) - A simplified Jira clone built with React/Babel (Client), and Node/TypeScript (API). Auto formatted with Prettier, tested with Cypress.

*   [Ma63d/kov-blog](https://github.com/Ma63d/kov-blog) - A blog platform built with koa,vue and mongoose. 使用 koa ,vue  和 mongo 搭建的博客页面和支持markdown语法的博客编写平台,自动保存草稿。博客地址:https://chuckliu.me

*   [dropzone/dropzone](https://github.com/dropzone/dropzone) - Dropzone is an easy to use drag'n'drop library. It supports image previews and shows nice progress bars.

*   [ruanyf/react-demos](https://github.com/ruanyf/react-demos) - a collection of simple demos of React.js

*   [MrXujiang/h5-Dooring](https://github.com/MrXujiang/h5-Dooring) - H5 Page Maker, H5 Editor, LowCode. Make H5 as easy as building blocks. | 让H5制作像搭积木一样简单, 轻松搭建H5页面, H5网站, PC端网站,LowCode平台.

*   [OBKoro1/koro1FileHeader](https://github.com/OBKoro1/koro1FileHeader) - VSCode插件：自动生成，自动更新VSCode文件头部注释, 自动生成函数注释并支持提取函数参数，支持所有主流语言，文档齐全，使用简单，配置灵活方便，持续维护多年。

*   [collab-project/videojs-wavesurfer](https://github.com/collab-project/videojs-wavesurfer) - video.js plugin that adds a navigable waveform for audio and video files

*   [koalaylj/xlsx2json](https://github.com/koalaylj/xlsx2json) - convert excel to json ,support object/array/number/bool data type.

*   [lodash/lodash](https://github.com/lodash/lodash) - A modern JavaScript utility library delivering modularity, performance, & extras.

*   [Inndy/vue-clipboard2](https://github.com/Inndy/vue-clipboard2) - A simple vue2 binding to clipboard.js

*   [zhangyuanliang/flowchart](https://github.com/zhangyuanliang/flowchart) - svg实现流程图绘制，导入导出json  \[正在重构项目flowchart-vue]，地址:

*   [OXOYO/X-Flowchart-Vue](https://github.com/OXOYO/X-Flowchart-Vue) - 基于G6和Vue的可视化图形编辑器。A visual graph editor based on G6 and Vue.

*   [jsdoc/jsdoc](https://github.com/jsdoc/jsdoc) - An API documentation generator for JavaScript.

*   [alibaba/rax](https://github.com/alibaba/rax) - 🐰 Rax is a progressive framework for building universal application. https://rax.js.org

*   [akveo/blur-admin](https://github.com/akveo/blur-admin) - AngularJS Bootstrap Admin Panel Framework

*   [bripkens/connect-history-api-fallback](https://github.com/bripkens/connect-history-api-fallback) - Fallback to index.html for applications that are using the HTML 5 history API

*   [zouyaoji/vue-cesium](https://github.com/zouyaoji/vue-cesium) - 🎉 Vue 3.x components for CesiumJS.

*   [CesiumGS/cesium](https://github.com/CesiumGS/cesium) - An open-source JavaScript library for world-class 3D globes and maps :earth\_americas:

*   [AsuraTeam/monitor](https://github.com/AsuraTeam/monitor) - The monitoring system, develop their own powerful and flexible configuration

*   [hyj1991/easy-monitor](https://github.com/hyj1991/easy-monitor) - 企业级 Node.js 应用性能监控与线上故障定位解决方案

*   [akira-cn/ICG-WebGL](https://github.com/akira-cn/ICG-WebGL) - 交互式计算机图形学——基于WebGL的自顶向下方法（第七版）的例子与练习题

*   [f2e-awesome/knowledge](https://github.com/f2e-awesome/knowledge) - 文档着重构建一个完整的「前端技术架构图谱」，方便 F2E(Front End Engineering又称FEE、F2E) 学习与进阶。

*   [wangweianger/zanePerfor](https://github.com/wangweianger/zanePerfor) - 前端性能监控系统,消息队列,高可用,集群等相关架构

*   [vitejs/awesome-vite](https://github.com/vitejs/awesome-vite) - ⚡️ A curated list of awesome things related to Vite.js

*   [photonstorm/phaser](https://github.com/photonstorm/phaser) - Phaser is a fun, free and fast 2D game framework for making HTML5 games for desktop and mobile web browsers, supporting Canvas and WebGL rendering.

*   [davidshimjs/qrcodejs](https://github.com/davidshimjs/qrcodejs) - Cross-browser QRCode generator for javascript

*   [requirejs/requirejs](https://github.com/requirejs/requirejs) - A file and module loader for JavaScript

*   [videojs/video.js](https://github.com/videojs/video.js) - Video.js - open source HTML5 video player

*   [cuth/postcss-pxtorem](https://github.com/cuth/postcss-pxtorem) - Convert pixel units to rem (root em) units using PostCSS

*   [eslint/eslint](https://github.com/eslint/eslint) - Find and fix problems in your JavaScript code.

*   [dvajs/dva](https://github.com/dvajs/dva) - 🌱 React and redux based, lightweight and elm-style framework. (Inspired by elm and choo)

*   [nice-people-frontend-community/nice-js-leetcode](https://github.com/nice-people-frontend-community/nice-js-leetcode) - 好青年 | leetcode 今日事今日毕（✅ Solutions to LeetCode by JavaScript, 100% test coverage, runtime beats 100% / LeetCode 题解 / GitHub Actions集成LeetCode每日一题至issues）

*   [pigcan/postcss-plugin-px2rem](https://github.com/pigcan/postcss-plugin-px2rem) - postcss plugin px2rem

*   [QasimWani/LeetHub](https://github.com/QasimWani/LeetHub) - Automatically sync your leetcode solutions to your github account - top 5 trending GitHub repository

*   [hotoo/pinyin](https://github.com/hotoo/pinyin) - :cn: 汉字拼音 ➜ hàn zì pīn yīn

*   [electron/electron-quick-start](https://github.com/electron/electron-quick-start) - Clone to try a simple Electron app

*   [qiushi123/cloud-email](https://github.com/qiushi123/cloud-email) - 微信小程序实现邮件发送，借助小程序云开发进行邮件验证码发送

*   [qiushi123/cloud-pay](https://github.com/qiushi123/cloud-pay) - 10行代码实现微信小程序支付，借助小程序云开发云函数实现微信支付

*   [binggg/tcb-subscribe-demo](https://github.com/binggg/tcb-subscribe-demo) - 小程序·云开发快速接入小程序订阅消息，开发开课提醒小程序

*   [Voyzz/Fruit-store-mp](https://github.com/Voyzz/Fruit-store-mp) - 🍊微信小程序-水果商城-云开发

*   [TencentCloudBase/tcb-demo-basic](https://github.com/TencentCloudBase/tcb-demo-basic) - 小程序·云开发系列教程——基础能力DEMO

*   [TencentCloudBase/mp-book](https://github.com/TencentCloudBase/mp-book) - 小程序·云开发系列教程

*   [nice-people-frontend-community/nice-handwriting-practice](https://github.com/nice-people-frontend-community/nice-handwriting-practice) -

*   [facebook/react](https://github.com/facebook/react) - The library for web and native user interfaces

*   [addyosmani/basket.js](https://github.com/addyosmani/basket.js) - A script and resource loader for caching & loading files with localStorage

*   [addyosmani/puppeteer-webperf](https://github.com/addyosmani/puppeteer-webperf) - Automating Web Performance testing with Puppeteer 🎪

*   [prettier/eslint-plugin-prettier](https://github.com/prettier/eslint-plugin-prettier) - ESLint plugin for Prettier formatting

*   [sinonjs/sinon](https://github.com/sinonjs/sinon) - Test spies, stubs and mocks for JavaScript.

*   [uuidjs/uuid](https://github.com/uuidjs/uuid) - Generate RFC-compliant UUIDs in JavaScript

*   [zloirock/core-js](https://github.com/zloirock/core-js) - Standard Library

*   [TheAlgorithms/JavaScript](https://github.com/TheAlgorithms/JavaScript) - Algorithms and Data Structures implemented in JavaScript for beginners, following best practices.

*   [ZijianHe/koa-router](https://github.com/ZijianHe/koa-router) - Router middleware for koa.

*   [moxiecode/plupload](https://github.com/moxiecode/plupload) - Plupload is JavaScript API for building file uploaders. It supports multiple file selection, file filtering, chunked upload, client side image downsizing and when necessary can fallback to alternative runtimes, like Flash and Silverlight.

*   [mde/ejs](https://github.com/mde/ejs) - Embedded JavaScript templates -- http://ejs.co

*   [pillarjs/cookies](https://github.com/pillarjs/cookies) - Signed and unsigned cookies based on Keygrip

*   [visionmedia/express-resource](https://github.com/visionmedia/express-resource) - Resourceful routing for Express

*   [koajs/examples](https://github.com/koajs/examples) - Example Koa apps

*   [koajs/koa](https://github.com/koajs/koa) - Expressive middleware for node.js using ES2017 async functions

*   [fex-team/kityminder](https://github.com/fex-team/kityminder) - 百度脑图

*   [fex-team/webuploader](https://github.com/fex-team/webuploader) - It's a new file uploader solution!

*   [wangwei1237/digital\_video\_concepts](https://github.com/wangwei1237/digital_video_concepts) - 数字视频相关技术和概念

*   [arackaf/customize-cra](https://github.com/arackaf/customize-cra) - Override webpack configurations for create-react-app 2.0

*   [vuejs/eslint-plugin-vue](https://github.com/vuejs/eslint-plugin-vue) - Official ESLint plugin for Vue.js

*   [shakacode/sass-resources-loader](https://github.com/shakacode/sass-resources-loader) - SASS resources (e.g. variables, mixins etc.) loader for Webpack. Also works with less, post-css, etc.

*   [conventional-changelog/standard-version](https://github.com/conventional-changelog/standard-version) - :trophy: Automate versioning and CHANGELOG generation, with semver.org and conventionalcommits.org

*   [bytedance/xgplayer](https://github.com/bytedance/xgplayer) - A HTML5 video player with a parser that saves traffic

*   [nuxt/vue-meta](https://github.com/nuxt/vue-meta) - Manage HTML metadata in Vue.js components with SSR support

*   [standard/standard](https://github.com/standard/standard) - 🌟 JavaScript Style Guide, with linter & automatic code fixer

*   [jwilber/roughViz](https://github.com/jwilber/roughViz) - Reusable JavaScript library for creating sketchy/hand-drawn styled charts in the browser.

*   [chartjs/Chart.js](https://github.com/chartjs/Chart.js) - Simple HTML5 Charts using the \<canvas> tag

*   [aliyun/oss-browser](https://github.com/aliyun/oss-browser) - OSS Browser 提供类似windows资源管理器功能。用户可以很方便的浏览文件，上传下载文件，支持断点续传等。

*   [jamiebuilds/the-super-tiny-compiler](https://github.com/jamiebuilds/the-super-tiny-compiler) - :snowman: Possibly the smallest compiler ever

*   [webpack/webpack-cli](https://github.com/webpack/webpack-cli) - Webpack's Command Line Interface

*   [emotion-js/emotion](https://github.com/emotion-js/emotion) - 👩‍🎤 CSS-in-JS library designed for high performance style composition

*   [preactjs/preact](https://github.com/preactjs/preact) - ⚛️ Fast 3kB React alternative with the same modern API. Components & Virtual DOM.

*   [facebook/create-react-app](https://github.com/facebook/create-react-app) - Set up a modern web app by running one command.

*   [phoboslab/jsmpeg](https://github.com/phoboslab/jsmpeg) - MPEG1 Video Decoder in JavaScript

*   [mrdoob/three.js](https://github.com/mrdoob/three.js) - JavaScript 3D Library.

*   [aframevr/aframe](https://github.com/aframevr/aframe) - :a: Web framework for building virtual reality experiences.

*   [webpack/webpack](https://github.com/webpack/webpack) - A bundler for javascript and friends. Packs many modules into a few bundled assets. Code Splitting allows for loading parts of the application on demand. Through "loaders", modules can be CommonJs, AMD, ES6 modules, CSS, Images, JSON, Coffeescript, LESS, ... and your custom stuff.

*   [cycjimmy/jsmpeg-player](https://github.com/cycjimmy/jsmpeg-player) - MPEG1 Video Player Based On JSMpeg.

*   [soyaine/JavaScript30](https://github.com/soyaine/JavaScript30) - 有关 @wesbos 的课程 JavaScript-30 的中文练习指南

*   [goldvideo/h265player](https://github.com/goldvideo/h265player) - 一套完整的Web版H.265播放器解决方案，非常适合学习交流和实际应用。基于JS码流解封装、WebAssembly(FFmpeg)视频解码，利用Canvas画布投影、AudioContext播放音频。

*   [lgwebdream/FE-Interview](https://github.com/lgwebdream/FE-Interview) - 🔥🔥🔥 前端面试，独有前端面试题详解，前端面试刷题必备，1000+前端面试真题，Html、Css、JavaScript、Vue、React、Node、TypeScript、Webpack、算法、网络与安全、浏览器

*   [atomiks/floating-ui](https://github.com/atomiks/floating-ui) - JavaScript positioning library for tooltips, popovers, dropdowns, and more

*   [dundalek/markmap](https://github.com/dundalek/markmap) - Visualize markdown documents as mindmaps

*   [ripplejs/ripple](https://github.com/ripplejs/ripple) - A tiny foundation for building reactive views

*   [JS-Hao/audio-sculptor](https://github.com/JS-Hao/audio-sculptor) - you can edit audio(such as clip, splice and replace) in browsers😊

*   [axios/axios](https://github.com/axios/axios) - Promise based HTTP client for the browser and node.js

*   [codemirror/codemirror5](https://github.com/codemirror/codemirror5) - In-browser code editor (version 5, legacy)

*   [webpack-contrib/compression-webpack-plugin](https://github.com/webpack-contrib/compression-webpack-plugin) - Prepare compressed versions of assets to serve them with Content-Encoding

*   [Rob--W/cors-anywhere](https://github.com/Rob--W/cors-anywhere) - CORS Anywhere is a NodeJS reverse proxy which adds CORS headers to the proxied request.

*   [bcle/fuse4js](https://github.com/bcle/fuse4js) - FUSE bindings for Javascript and node.js

*   [imagemin/imagemin](https://github.com/imagemin/imagemin) - \[Unmaintained] Minify images seamlessly

*   [imagemin/imagemin-mozjpeg](https://github.com/imagemin/imagemin-mozjpeg) - Imagemin plugin for mozjpeg

*   [huaxinjiayou/js-pinyin](https://github.com/huaxinjiayou/js-pinyin) - js汉字转拼音

*   [Kaifuny/pinyin4js](https://github.com/Kaifuny/pinyin4js) - A opensource javascript library for converting chinese to pinyin。welcome Star : P

*   [travist/jsencrypt](https://github.com/travist/jsencrypt) - A zero-dependency Javascript library to perform OpenSSL RSA Encryption, Decryption, and Key Generation.

*   [zaach/jsonlint](https://github.com/zaach/jsonlint) - A JSON parser and validator with a CLI.

*   [Stuk/jszip](https://github.com/Stuk/jszip) - Create, read and edit .zip files with Javascript

*   [amfe/lib-flexible](https://github.com/amfe/lib-flexible) - 可伸缩布局方案

*   [simple-statistics/simple-statistics](https://github.com/simple-statistics/simple-statistics) - simple statistics for node & browser javascript

*   [moment/moment](https://github.com/moment/moment) - Parse, validate, manipulate, and display dates in javascript.

*   [expressjs/morgan](https://github.com/expressjs/morgan) - HTTP request logger middleware for node.js

*   [rstacruz/nprogress](https://github.com/rstacruz/nprogress) - For slim progress bars like on YouTube, Medium, etc

*   [fent/randexp.js](https://github.com/fent/randexp.js) - Create random strings that match a given regular expression.

*   [yyx990803/register-service-worker](https://github.com/yyx990803/register-service-worker) - A script to simplify service worker registration with hooks for common events.

*   [que-etc/resize-observer-polyfill](https://github.com/que-etc/resize-observer-polyfill) - A polyfill for the Resize Observer API

*   [vuejs/vuex](https://github.com/vuejs/vuex) - 🗃️ Centralized State Management for Vue.js.

*   [webpack-contrib/webpack-bundle-analyzer](https://github.com/webpack-contrib/webpack-bundle-analyzer) - Webpack plugin and CLI utility that represents bundle content as convenient interactive zoomable treemap

*   [stefanpenner/es6-promise](https://github.com/stefanpenner/es6-promise) - A polyfill for ES6-style Promises

*   [ElemeFE/element-react](https://github.com/ElemeFE/element-react) - Element UI

*   [chalk/chalk](https://github.com/chalk/chalk) - 🖍 Terminal string styling done right

*   [sindresorhus/ora](https://github.com/sindresorhus/ora) - Elegant terminal spinner

*   [SBoudrias/Inquirer.js](https://github.com/SBoudrias/Inquirer.js) - A collection of common interactive command line user interfaces.

*   [tj/commander.js](https://github.com/tj/commander.js) - node.js command-line interfaces made easy

*   [nagaozen/markdown-it-toc-done-right](https://github.com/nagaozen/markdown-it-toc-done-right) - A table of contents (TOC) plugin for Markdown-it with focus on semantic and security. Made to work gracefully with markdown-it-anchor.

*   [valeriangalliat/markdown-it-anchor](https://github.com/valeriangalliat/markdown-it-anchor) - A markdown-it plugin that adds an `id` attribute to headings and optionally permalinks.

*   [Ovilia/ThreeExample.js](https://github.com/Ovilia/ThreeExample.js) - 《Three.js 入门指南》书例代码

*   [buuing/right-menu](https://github.com/buuing/right-menu) - 📜 @right-menu 是一个使用 TypeScript 开发的右键菜单插件, 🏆 可以在 JS / TS / Vue / React 等多端框架使用, 🦄 支持多级菜单 / 异步渲染 / 骨架Loading / 自适应主题 / mac黑夜模式

*   [kazupon/vue-i18n](https://github.com/kazupon/vue-i18n) - :globe\_with\_meridians: Internationalization plugin for Vue.js

*   [vuelidate/vuelidate](https://github.com/vuelidate/vuelidate) - Simple, lightweight model-based validation for Vue.js

*   [typescript-cheatsheets/react](https://github.com/typescript-cheatsheets/react) - Cheatsheets for experienced React developers getting started with TypeScript

*   [sumimakito/Awesome-qr.js](https://github.com/sumimakito/Awesome-qr.js) - An awesome QR code generator written in JavaScript.

*   [Chimeejs/chimee](https://github.com/Chimeejs/chimee) - a video player framework aims to bring wonderful experience on browser

*   [bilibili/flv.js](https://github.com/bilibili/flv.js) - HTML5 FLV Player

*   [ryouaki/ECMAScript2016-Design-Patterns](https://github.com/ryouaki/ECMAScript2016-Design-Patterns) - Design Patterns for ES6 (使用es6实现的设计模式)

*   [a597873885/webfunny\_monitor](https://github.com/a597873885/webfunny_monitor) - webfunny是一款轻量级的前端性能监控系统，也是一款埋点系统，私有化部署，简单易用。Webfunny is a lightweight front-end performance monitoring system and a burying point system, which is privatized and easy to use.

*   [Advanced-Frontend/Daily-Interview-Question](https://github.com/Advanced-Frontend/Daily-Interview-Question) - 我是依扬（木易杨），公众号「高级前端进阶」作者，每天搞定一道前端大厂面试题，祝大家天天进步，一年后会看到不一样的自己。

*   [stephentian/33-js-concepts](https://github.com/stephentian/33-js-concepts) - :scroll: 每个 JavaScript 工程师都应懂的33个概念 @leonardomso

*   [yangshun/front-end-interview-handbook](https://github.com/yangshun/front-end-interview-handbook) - ⚡️ Front End interview preparation materials for busy engineers

*   [30-seconds/30-seconds-of-interviews](https://github.com/30-seconds/30-seconds-of-interviews) - A curated collection of common interview questions to help you prepare for your next interview.

*   [wallstreetcn/vue-ssr-boilerplate](https://github.com/wallstreetcn/vue-ssr-boilerplate) - Vue.js Server Side Rendering Boilerplate without Polluting Vuex

*   [vuejs/eslint-config-vue](https://github.com/vuejs/eslint-config-vue) -

*   [zenorocha/clipboard.js](https://github.com/zenorocha/clipboard.js) - :scissors: Modern copy to clipboard. No Flash. Just 3kb gzipped :clipboard:

*   [PanJiaChen/vue-countTo](https://github.com/PanJiaChen/vue-countTo) - It's a vue component that will count to a target number at a specified duration https://panjiachen.github.io/countTo/demo/

*   [nuysoft/Mock](https://github.com/nuysoft/Mock) - A simulation data generator

*   [juliangarnier/anime](https://github.com/juliangarnier/anime) - JavaScript animation engine

*   [mathieudutour/medium-to-own-blog](https://github.com/mathieudutour/medium-to-own-blog) - Switch from Medium to your own blog in a few minutes

*   [facebookarchive/draft-js](https://github.com/facebookarchive/draft-js) - A React framework for building text editors.

*   [befinal/node-tenpay](https://github.com/befinal/node-tenpay) - 微信支付 for nodejs

*   [node-webot/wechat](https://github.com/node-webot/wechat) - 微信公共平台消息接口服务中间件

*   [SimulatedGREG/electron-vue](https://github.com/SimulatedGREG/electron-vue) - An Electron & Vue.js quick start boilerplate with vue-cli scaffolding, common Vue plugins, electron-packager/electron-builder, unit/e2e testing, vue-devtools, and webpack.

*   [lancedikson/bowser](https://github.com/lancedikson/bowser) - a browser detector

*   [fengyuanchen/compressorjs](https://github.com/fengyuanchen/compressorjs) - JavaScript image compressor.

*   [jaywcjlove/hotkeys-js](https://github.com/jaywcjlove/hotkeys-js) - ➷ A robust Javascript library for capturing keyboard input. It has no dependencies.

*   [sindresorhus/globby](https://github.com/sindresorhus/globby) - User-friendly glob matching

*   [iamkun/dayjs](https://github.com/iamkun/dayjs) - ⏰ Day.js 2kB immutable date-time library alternative to Moment.js with the same modern API

*   [browserstate/history.js](https://github.com/browserstate/history.js) - History.js gracefully supports the HTML5 History/State APIs (pushState, replaceState, onPopState) in all browsers. Including continued support for data, titles, replaceState. Supports jQuery, MooTools and Prototype.  For HTML5 browsers this means that you can modify the URL directly, without needing to use hashes anymore. For HTML4 browsers it will revert back to using the old onhashchange functionality.

*   [trekhleb/javascript-algorithms](https://github.com/trekhleb/javascript-algorithms) - 📝 Algorithms and data structures implemented in JavaScript with explanations and links to further readings

*   [ustbhuangyi/vue-analysis](https://github.com/ustbhuangyi/vue-analysis) - :thumbsup: Vue.js 源码分析

*   [adam-golab/react-developer-roadmap](https://github.com/adam-golab/react-developer-roadmap) - Roadmap to becoming a React developer

*   [mrdoob/stats.js](https://github.com/mrdoob/stats.js) - JavaScript Performance Monitor

*   [mdn/dom-examples](https://github.com/mdn/dom-examples) - Code examples that accompany various MDN DOM and Web API documentation pages

*   [scaleflex/js-cloudimage-360-view](https://github.com/scaleflex/js-cloudimage-360-view) - Engage your customers with a stunning 360 view of your products. Any questions or issues, please report to https://github.com/scaleflex/js-cloudimage-360-view/issues

*   [localForage/localForage](https://github.com/localForage/localForage) - 💾 Offline storage, improved. Wraps IndexedDB, WebSQL, or localStorage using a simple but powerful API.

*   [azl397985856/leetcode](https://github.com/azl397985856/leetcode) - 推荐免费ChatGPT网站：www.lintcode.com/chat-gpt?utm\_source=tf-github-lucifer  LeetCode Solutions: A Record of My Problem Solving Journey.( leetcode题解，记录自己的leetcode解题之路。)

*   [sonysuqin/WasmVideoPlayer](https://github.com/sonysuqin/WasmVideoPlayer) - Play file/stream with wasm & webgl & web audio api, using ffmpeg for multi codec support, especially for h265，support http, websocket, http-flv stream.

*   [duanyao/codecbox.js](https://github.com/duanyao/codecbox.js) - video and audio codecs for javascript based on ffmpeg and asm.js

*   [algorithm-visualizer/algorithm-visualizer](https://github.com/algorithm-visualizer/algorithm-visualizer) - :fireworks:Interactive Online Platform that Visualizes Algorithms from Code

*   [alvarotrigo/fullPage.js](https://github.com/alvarotrigo/fullPage.js) - fullPage plugin by Alvaro Trigo. Create full screen pages fast and simple

*   [brix/crypto-js](https://github.com/brix/crypto-js) - JavaScript library of crypto standards.

*   [denysdovhan/wtfjs](https://github.com/denysdovhan/wtfjs) - 🤪 A list of funny and tricky JavaScript examples

*   [ascoders/weekly](https://github.com/ascoders/weekly) - 前端精读周刊。帮你理解最前沿、实用的技术。

*   [muaz-khan/WebRTC-Experiment](https://github.com/muaz-khan/WebRTC-Experiment) - WebRTC, WebRTC and WebRTC. Everything here is all about WebRTC!!

*   [webrtc/samples](https://github.com/webrtc/samples) - WebRTC Web demos and samples

*   [jones2000/HQChart](https://github.com/jones2000/HQChart) - HQChart - H5, 微信小程序 沪深/港股/数字货币/期货/美股 K线图(kline),走势图,缩放,拖拽,十字光标,画图工具,截图,筹码图. 分析家语法,通达信语法,(麦语法),第3方数据替换接口

*   [videojs/videojs-contrib-dash](https://github.com/videojs/videojs-contrib-dash) - Video.js plugin for supporting the MPEG-DASH playback through a video.js player

*   [alyssaxuu/screenity](https://github.com/alyssaxuu/screenity) - The most powerful screen recorder & annotation tool for Chrome 🎥

*   [Asabeneh/30-Days-Of-React](https://github.com/Asabeneh/30-Days-Of-React) - 30 Days of  React challenge is a step by step guide to learn React in 30 days.  These videos may help too: https://www.youtube.com/channel/UC7PNRuno1rzYPb1xLa4yktw

*   [wuchangming/spy-debugger](https://github.com/wuchangming/spy-debugger) - 微信调试，各种WebView样式调试、手机浏览器的页面真机调试。便捷的远程调试手机页面、抓包工具，支持：HTTP/HTTPS，无需USB连接设备。

*   [30-seconds/30-seconds-of-code](https://github.com/30-seconds/30-seconds-of-code) - Short code snippets for all your development needs

*   [adrai/flowchart.js](https://github.com/adrai/flowchart.js) - Draws simple SVG flow chart diagrams from textual representation of the diagram

*   [fex-team/ueditor](https://github.com/fex-team/ueditor) - rich text 富文本编辑器

*   [jimmywarting/StreamSaver.js](https://github.com/jimmywarting/StreamSaver.js) - StreamSaver writes stream to the filesystem directly asynchronous

*   [eligrey/FileSaver.js](https://github.com/eligrey/FileSaver.js) - An HTML5 saveAs() FileSaver implementation

*   [rigor789/vue-scrollto](https://github.com/rigor789/vue-scrollto) - Adds a directive that listens for click events and scrolls to elements.

*   [js-cookie/js-cookie](https://github.com/js-cookie/js-cookie) - A simple, lightweight JavaScript API for handling browser cookies

*   [surmon-china/vue-awesome-swiper](https://github.com/surmon-china/vue-awesome-swiper) - 🏆 Swiper component for @vuejs

*   [alexwolfe/Buttons](https://github.com/alexwolfe/Buttons) - A CSS button library built using Sass and Compass

*   [notadd/neditor](https://github.com/notadd/neditor) - 基于 ueditor的更现代化的富文本编辑器，支持HTTPS

*   [hilongjw/vue-lazyload](https://github.com/hilongjw/vue-lazyload) - A Vue.js plugin for lazyload your Image or Component in your application.

*   [nolimits4web/swiper](https://github.com/nolimits4web/swiper) - Most modern mobile touch slider with hardware accelerated transitions

*   [DataV-Team/Charts](https://github.com/DataV-Team/Charts) - 轻量级图表，提供常用图表如折线图、柱状图、饼状图等，支持动画效果

*   [Asabeneh/30-Days-Of-JavaScript](https://github.com/Asabeneh/30-Days-Of-JavaScript) - 30 days of JavaScript programming challenge is a step-by-step guide to learn JavaScript programming language in 30 days. This challenge may take more than 100 days,  please just follow your own pace. These videos may help too: https://www.youtube.com/channel/UC7PNRuno1rzYPb1xLa4yktw

*   [renrenio/renren-fast-vue](https://github.com/renrenio/renren-fast-vue) - renren-fast-vue基于vue、element-ui构建开发，实现renren-fast后台管理前端功能，提供一套更优的前端解决方案。

*   [syntaxhighlighter/syntaxhighlighter](https://github.com/syntaxhighlighter/syntaxhighlighter) - SyntaxHighlighter is a fully functional self-contained code syntax highlighter developed in JavaScript.

*   [goldfire/howler.js](https://github.com/goldfire/howler.js) - Javascript audio library for the modern web.

*   [postcss/autoprefixer](https://github.com/postcss/autoprefixer) -  Parse CSS and add vendor prefixes to rules by Can I Use

*   [JetBrains/svg-sprite-loader](https://github.com/JetBrains/svg-sprite-loader) - Webpack loader for creating SVG sprites.

*   [azl397985856/fe-interview](https://github.com/azl397985856/fe-interview) - 宇宙最强的前端面试指南 (https://lucifer.ren/fe-interview)

*   [dai-siki/vue-image-crop-upload](https://github.com/dai-siki/vue-image-crop-upload) - A beautiful vue component for image cropping and uploading. （vue图片剪裁上传组件）

*   [superhos/vue-baberrage](https://github.com/superhos/vue-baberrage) - A simple Barrage plugin Base on Vue.js.  | 基于Vue.js弹幕插件.

*   [sandoche/Darkmode.js](https://github.com/sandoche/Darkmode.js) - 🌓 Add a dark-mode / night-mode to your website in a few seconds

*   [mozilla/pdf.js](https://github.com/mozilla/pdf.js) - PDF Reader in JavaScript

*   [jantimon/html-webpack-plugin](https://github.com/jantimon/html-webpack-plugin) - Simplifies creation of HTML files to serve your webpack bundles

*   [SortableJS/Vue.Draggable](https://github.com/SortableJS/Vue.Draggable) - Vue drag-and-drop component based on Sortable.js

*   [Kagami/ffmpeg.js](https://github.com/Kagami/ffmpeg.js) - Port of FFmpeg with Emscripten

*   [nodejs/node](https://github.com/nodejs/node) - Node.js JavaScript runtime :sparkles::turtle::rocket::sparkles:

*   [vuejs/vue-cli](https://github.com/vuejs/vue-cli) - 🛠️ webpack-based tooling for Vue.js Development

*   [rollup/rollup](https://github.com/rollup/rollup) - Next-generation ES module bundler

*   [Binaryify/NeteaseCloudMusicApi](https://github.com/Binaryify/NeteaseCloudMusicApi) - 网易云音乐 Node.js API service

*   [maomao1996/react-music](https://github.com/maomao1996/react-music) - 基于React的在线音乐播放器（移动端高仿安卓网易云音乐）（重构是不可能的，这辈子都不会用 hooks 重构）

*   [AlloyTeam/curvejs](https://github.com/AlloyTeam/curvejs) - Made curve a dancer in HTML5 canvas - 魔幻线条

*   [airbnb/javascript](https://github.com/airbnb/javascript) - JavaScript Style Guide

*   [youzan/weapp-plugin-demo](https://github.com/youzan/weapp-plugin-demo) - 有赞微商城所有小程序插件的演示demo

*   [PanJiaChen/vue-admin-template](https://github.com/PanJiaChen/vue-admin-template) - a vue2.0 minimal admin template

*   [PanJiaChen/electron-vue-admin](https://github.com/PanJiaChen/electron-vue-admin) -  vue electron admin template web: http://panjiachen.github.io/vue-admin-template

*   [vuejs-templates/webpack](https://github.com/vuejs-templates/webpack) - A full-featured Webpack + vue-loader setup with hot reload, linting, testing & css extraction.

*   [xaboy/form-create](https://github.com/xaboy/form-create) - :fire::fire::fire: 强大的动态表单生成器|form-create is a form generation component that can generate dynamic rendering, data collection, verification and submission functions through JSON.

*   [sunshine940326/canvas](https://github.com/sunshine940326/canvas) -

*   [yzsunlei/special-vue-series-code-analyzing](https://github.com/yzsunlei/special-vue-series-code-analyzing) - 「Vue生态库源码系列」,Vue、Vue-router、Vuex、Vue-cli、Vue-loader、Vue-devtools等

*   [logoove/weui](https://github.com/logoove/weui) - weui+是在weui和zepto基础上开发的增强UI组件,目前分为表单,基础,组件,js插件四大类,共计百余项功能,是最全的weui样式

*   [MyNameisQiShiQi/radarCanvas](https://github.com/MyNameisQiShiQi/radarCanvas) - 微信小程序  雷达图组件 component

*   [sunniejs/vue-canvas-poster](https://github.com/sunniejs/vue-canvas-poster) - vue生成海报图，一个通过 css 属性画 canvas 图片的轻量级的 vue 组件 (Vue poster,a lightweight vue component that draws canvas images via css properties.)

*   [ColorlibHQ/AdminLTE](https://github.com/ColorlibHQ/AdminLTE) - AdminLTE - Free admin dashboard template based on Bootstrap 4

*   [ruanyf/es6tutorial](https://github.com/ruanyf/es6tutorial) - 《ECMAScript 6入门》是一本开源的 JavaScript 语言教程，全面介绍 ECMAScript 6 新增的语法特性。

*   [vuejs/v2.vuejs.org](https://github.com/vuejs/v2.vuejs.org) - 📄 Documentation for Vue 2

*   [sunniejs/sol-weapp](https://github.com/sunniejs/sol-weapp) - :clap:红包雨，大转盘，小程序营销组件，小程序商城常用组件  https://sunniejs.github.io/sol-weapp/

*   [berwin/Blog](https://github.com/berwin/Blog) - 记录成长的过程

*   [ecomfe/echarts-for-weixin](https://github.com/ecomfe/echarts-for-weixin) - Apache ECharts 的微信小程序版本

*   [game-helper/weixin](https://github.com/game-helper/weixin) - 微信小游戏辅助合集（加减大师、包你懂我、大家来找茬腾讯版、头脑王者、好友画我、悦动音符、我最在行、星途WeGoing、猜画小歌、知乎答题王、腾讯中国象棋、跳一跳、题多多黄金版）

*   [youzan/vant-weapp](https://github.com/youzan/vant-weapp) - 轻量、可靠的小程序 UI 组件库

*   [vuejs/vue-cli-plugin-vue-next](https://github.com/vuejs/vue-cli-plugin-vue-next) - A Vue CLI plugin for trying out vue-next (experimental)

*   [timqian/chinese-independent-blogs](https://github.com/timqian/chinese-independent-blogs) - 中文独立博客列表

*   [vuejs/vue-router](https://github.com/vuejs/vue-router) - 🚦 The official router for Vue 2

*   [qwqoffice/odometer-for-wechatapp](https://github.com/qwqoffice/odometer-for-wechatapp) - 微信小程序odometer数字滚动动画组件

*   [qwqoffice/html2wxml](https://github.com/qwqoffice/html2wxml) - 用于微信小程序的HTML和Markdown格式的富文本渲染组件，支持代码高亮

## TypeScript

*   [elastic/kibana](https://github.com/elastic/kibana) - Your window into the Elastic Stack

*   [Dart-Code/Dart-Code](https://github.com/Dart-Code/Dart-Code) - Dart and Flutter support for VS Code

*   [jkchao/typescript-book-chinese](https://github.com/jkchao/typescript-book-chinese) - TypeScript Deep Dive 中文版

*   [alibaba/kiwi](https://github.com/alibaba/kiwi) - 🐤 Kiwi-国际化翻译全流程解决方案

*   [vueComponent/pro-components](https://github.com/vueComponent/pro-components) - easy use `Ant Design Vue` layout

*   [alibaba/hooks](https://github.com/alibaba/hooks) - A high-quality & reliable React Hooks library.

*   [arco-design/arco-design-vue](https://github.com/arco-design/arco-design-vue) - A Vue.js 3 UI Library based on Arco Design

*   [arco-design/arco-cli](https://github.com/arco-design/arco-cli) - CLI tool for Arco Design

*   [lvwzhen/law-cn-ai](https://github.com/lvwzhen/law-cn-ai) - ⚖️ AI 法律助手

*   [nuxt/nuxt](https://github.com/nuxt/nuxt) - Nuxt is an intuitive and extendable way to create type-safe, performant and production-grade full-stack web apps and websites with Vue 3.

*   [HalseySpicy/Hooks-Admin](https://github.com/HalseySpicy/Hooks-Admin) - 🚀🚀🚀 Hooks Admin，基于 React18、React-Router V6、React-Hooks、Redux、TypeScript、Vite2、Ant-Design 开源的一套后台管理框架。

*   [vbenjs/vben3](https://github.com/vbenjs/vben3) -

*   [vbenjs/vite-plugin-svg-icons](https://github.com/vbenjs/vite-plugin-svg-icons) - Vite Plugin for fast creating SVG sprites.

*   [scroll-out/scroll-out](https://github.com/scroll-out/scroll-out) - ScrollOut detects changes in scroll for reveal, parallax, and CSS Variable effects!

*   [ant-design/ant-design-charts](https://github.com/ant-design/ant-design-charts) - A React Chart Library

*   [ant-design/ant-design](https://github.com/ant-design/ant-design) - An enterprise-class UI design language and React UI library

*   [rockbenben/ChatGPT-Shortcut](https://github.com/rockbenben/ChatGPT-Shortcut) - Maximize your efficiency and productivity. 让生产力加倍的 ChatGPT 快捷指令，按照领域和功能分区，可对提示词进行标签筛选、关键词搜索和一键复制。

*   [webVueBlog/umi-poster](https://github.com/webVueBlog/umi-poster) - 海报，封面生成器

*   [umijs/qiankun](https://github.com/umijs/qiankun) - 📦 🚀 Blazing fast, simple and complete solution for micro frontends.

*   [electron-vite/electron-vite-react](https://github.com/electron-vite/electron-vite-react) - :electron: Electron + Vite + React + Sass boilerplate.

*   [ice-lab/icestark](https://github.com/ice-lab/icestark) - :tiger: Micro Frontends solution for large application（面向大型应用的微前端解决方案），站点国内镜像：https://icestark.gitee.io

*   [alibaba/x-render](https://github.com/alibaba/x-render) - 🚴‍♀️ 阿里 - 很易用的中后台「表单 / 表格 / 图表」解决方案

*   [midwayjs/midway](https://github.com/midwayjs/midway) - 🍔 A Node.js Serverless Framework for front-end/full-stack developers. Build the application for next decade. Works on AWS, Alibaba Cloud, Tencent Cloud and traditional VM/Container. Super easy integrate with React and Vue. 🌈

*   [vuejs/pinia](https://github.com/vuejs/pinia) - 🍍 Intuitive, type safe, light and flexible Store for Vue using the composition api with DevTools support

*   [vueuse/vueuse](https://github.com/vueuse/vueuse) - Collection of essential Vue Composition Utilities for Vue 2 and 3

*   [longyanjiang/Nine-chat-backend](https://github.com/longyanjiang/Nine-chat-backend) - 采用socketio打造的多人实时通讯多房间在线音乐聊天室

*   [webVueBlog/bing-wallpaper](https://github.com/webVueBlog/bing-wallpaper) - 使用 deno、Github Actions 自动抓取 Bing 每日超清壁纸（4K）

*   [webVueBlog/todolist-react](https://github.com/webVueBlog/todolist-react) - TypeScript版本-使用 React 和 Redux 构建的 TodoMVC (props\&Event\&Context\&Mobx\&Redux)

*   [webVueBlog/vue-ts-netease-cloud-music](https://github.com/webVueBlog/vue-ts-netease-cloud-music) - 网易云音乐客户端播放器（PC） Online Music Player

*   [liuweiGL/vite-plugin-mkcert](https://github.com/liuweiGL/vite-plugin-mkcert) - Provide certificates for vite's https dev service.

*   [btd/rollup-plugin-visualizer](https://github.com/btd/rollup-plugin-visualizer) - 📈⚖️ Visuallize your bundle

*   [open-cli-tools/concurrently](https://github.com/open-cli-tools/concurrently) - Run commands concurrently. Like `npm run watch-js &amp; npm run watch-less` but better.

*   [sindresorhus/ow](https://github.com/sindresorhus/ow) - Function argument validation for humans

*   [keystonejs/keystone](https://github.com/keystonejs/keystone) - The most powerful headless CMS for Node.js — built with GraphQL and React

*   [weyoss/redis-smq](https://github.com/weyoss/redis-smq) - A simple high-performance Redis message queue for Node.js.

*   [luin/ioredis](https://github.com/luin/ioredis) - 🚀 A robust, performance-focused, and full-featured Redis client for Node.js.

*   [bevry/getmac](https://github.com/bevry/getmac) - Get the mac address of the current machine you are on via Node.js

*   [facebook/docusaurus](https://github.com/facebook/docusaurus) - Easy to maintain open source documentation websites.

*   [bitcoinjs/bitcoinjs-lib](https://github.com/bitcoinjs/bitcoinjs-lib) - A javascript Bitcoin library for node.js and browsers.

*   [AttoJS/vue-request](https://github.com/AttoJS/vue-request) - ⚡️ Vue composition API for data fetching, supports SWR, polling, error retry, cache request, pagination, etc. ⚡️ 一个能轻松帮你管理请求状态（支持SWR，轮询，错误重试，缓存，分页等）的 Vue 请求库

*   [didi/LogicFlow](https://github.com/didi/LogicFlow) - A flow chart editing framework focusing on business customization. 专注于业务自定义的流程图编辑框架，支持实现脑图、ER图、UML、工作流等各种图编辑场景。

*   [7kms/react-illustration-series](https://github.com/7kms/react-illustration-series) - 图解react源码, 用大量配图的方式, 致力于将react原理表述清楚.

*   [total-typescript/beginners-typescript-tutorial](https://github.com/total-typescript/beginners-typescript-tutorial) - An interactive TypeScript tutorial for beginners

*   [pladaria/reconnecting-websocket](https://github.com/pladaria/reconnecting-websocket) - Reconnecting WebSocket. For Web, React Native, cli (Node.js)

*   [vuejs/language-tools](https://github.com/vuejs/language-tools) - ⚡ High-performance Vue language tooling based-on Volar.js

*   [buqiyuan/vite-vue3-lowcode](https://github.com/buqiyuan/vite-vue3-lowcode) - vue3.x + vite2.x + vant + element-plus H5移动端低代码平台 lowcode 可视化拖拽 可视化编辑器 visual editor 类似易企秀的H5制作、建站工具、可视化搭建工具

*   [youngjuning/vant-react-native.js.org](https://github.com/youngjuning/vant-react-native.js.org) - Lightweight React Native UI Components inspired on Vant

*   [curly210102/word-counter](https://github.com/curly210102/word-counter) -

*   [yenshih/style-resources-loader](https://github.com/yenshih/style-resources-loader) - CSS processor resources loader for webpack

*   [Lemoncode/react-typescript-samples](https://github.com/Lemoncode/react-typescript-samples) - The goal of this project is to provide a set of simple samples, providing and step by step guide to start working with React and Typescript.

*   [vuejs/vue-loader](https://github.com/vuejs/vue-loader) - 📦 Webpack loader for Vue.js components

*   [s-panferov/awesome-typescript-loader](https://github.com/s-panferov/awesome-typescript-loader) - Awesome TypeScript loader for webpack

*   [TypeStrong/ts-loader](https://github.com/TypeStrong/ts-loader) - TypeScript loader for webpack

*   [amplication/amplication](https://github.com/amplication/amplication) - Auto-generating TypeScript, GraphQL, REST API, and Node.js, accelerating your full-stack development 🚀

*   [textbus/textbus](https://github.com/textbus/textbus) - Textbus 是一个组件化的、数据驱动的富文本框架，支持在线协同编辑，同时也可以作为一个开箱即用的富文本编辑器，拥有非常好的扩展性和可定制性，是构建复杂富文本的不二之选！

*   [javascript-obfuscator/webpack-obfuscator](https://github.com/javascript-obfuscator/webpack-obfuscator) - javascript-obfuscator plugin for Webpack

*   [HospitalRun/hospitalrun-frontend](https://github.com/HospitalRun/hospitalrun-frontend) - Frontend for HospitalRun

*   [cypress-io/cypress-realworld-app](https://github.com/cypress-io/cypress-realworld-app) - A payment application to demonstrate real-world usage of Cypress testing methods, patterns, and workflows.

*   [react-component/table](https://github.com/react-component/table) - React Table

*   [Nodlik/StPageFlip](https://github.com/Nodlik/StPageFlip) - Simple library for creating realistic page turning effects

*   [labring/laf](https://github.com/labring/laf) - 🤖 laf 是云开发平台，提供云函数、云数据库、云存储等开箱即用的应用资源。让开发者快速释放创意。ChatGPT 自动写函数，秒级上线，世界上只有两种 serverless，30 秒上线的 和 30 秒劝退的！

*   [react-native-elements/react-native-elements](https://github.com/react-native-elements/react-native-elements) - Cross-Platform React Native UI Toolkit

*   [ant-design/ant-design-mobile-rn](https://github.com/ant-design/ant-design-mobile-rn) - Ant Design for React Native

*   [faker-js/faker](https://github.com/faker-js/faker) - Generate massive amounts of fake data in the browser and node.js

*   [akveo/ngx-admin](https://github.com/akveo/ngx-admin) - Customizable admin dashboard template based on Angular 10+

*   [marmelab/react-admin](https://github.com/marmelab/react-admin) - A frontend Framework for building B2B applications running in the browser on top of REST/GraphQL APIs, using ES6, React and Material Design

*   [alibaba/ice](https://github.com/alibaba/ice) - 🚀 ice.js: The Progressive App Framework Based On React（基于 React 的渐进式应用框架）

*   [ant-design/ant-design-pro](https://github.com/ant-design/ant-design-pro) - 👨🏻‍💻👩🏻‍💻 Use Ant Design like a Pro!

*   [ant-design/ant-design-mobile](https://github.com/ant-design/ant-design-mobile) - Essential UI blocks for building mobile web apps.

*   [mui/material-ui](https://github.com/mui/material-ui) - MUI Core: Ready-to-use foundational React components, free forever. It includes Material UI, which implements Google's Material Design.

*   [pnpm/pnpm](https://github.com/pnpm/pnpm) - Fast, disk space efficient package manager

*   [antfu/vitesse](https://github.com/antfu/vitesse) - 🏕 Opinionated Vite + Vue Starter Template

*   [baidu/amis](https://github.com/baidu/amis) - 前端低代码框架，通过 JSON 配置就能生成各种页面。

*   [NervJS/taro](https://github.com/NervJS/taro) - 开放式跨端跨框架解决方案，支持使用 React/Vue/Nerv 等框架来开发微信/京东/百度/支付宝/字节跳动/ QQ 小程序/H5/React Native 等应用。  https://taro.zone/

*   [socketio/socket.io](https://github.com/socketio/socket.io) - Realtime application framework (Node.JS server)

*   [hustcc/timeago.js](https://github.com/hustcc/timeago.js) - :clock8: :hourglass: timeago.js is a tiny(2.0 kb) library used to format date with `*** time ago` statement.

*   [vuese/vuese](https://github.com/vuese/vuese) - 🤗 One-stop solution for vue component documentation. Original org: https://github.com/vuese

*   [styleguidist/react-docgen-typescript](https://github.com/styleguidist/react-docgen-typescript) - A simple parser for react properties defined in typescript instead of propTypes.

*   [ant-design/pro-components](https://github.com/ant-design/pro-components) - 🏆 Use Ant Design like a Pro!

*   [alibaba/GGEditor](https://github.com/alibaba/GGEditor) - A visual graph editor based on G6 and React

*   [antvis/L7](https://github.com/antvis/L7) - 🌎 Large-scale WebGL-powered Geospatial Data Visualization analysis engine

*   [antvis/G2](https://github.com/antvis/G2) - 📊 A concise and progressive visualization grammar.

*   [antvis/G6](https://github.com/antvis/G6) - ♾ A Graph Visualization Framework in JavaScript

*   [umijs/umi](https://github.com/umijs/umi) - A framework in react community ✨

*   [jestjs/jest](https://github.com/jestjs/jest) - Delightful JavaScript Testing.

*   [reduxjs/redux](https://github.com/reduxjs/redux) - Predictable state container for JavaScript apps

*   [Yqnn/svg-path-editor](https://github.com/Yqnn/svg-path-editor) - Online editor to create and manipulate SVG paths

*   [CJex/regulex](https://github.com/CJex/regulex) - :construction: Regular Expression Excited!

*   [adonisjs/core](https://github.com/adonisjs/core) - 🚀 The Node.js Framework highly focused on developer ergonomics, stability and confidence

*   [Cody2333/koa-swagger-decorator](https://github.com/Cody2333/koa-swagger-decorator) - using decorator to automatically generate swagger doc for koa-router

*   [tusen-ai/naive-ui](https://github.com/tusen-ai/naive-ui) - A Vue 3 Component Library. Fairly Complete. Theme Customizable. Uses TypeScript. Fast.

*   [alibaba/formily](https://github.com/alibaba/formily) - 📱🚀 🧩 Cross Device & High Performance Normal Form/Dynamic(JSON Schema) Form/Form Builder -- Support React/React Native/Vue 2/Vue 3

*   [Tencent/tdesign-vue](https://github.com/Tencent/tdesign-vue) - A Vue.js UI components lib for TDesign.

*   [typescript-eslint/typescript-eslint](https://github.com/typescript-eslint/typescript-eslint) - :sparkles: Monorepo for all the tooling which enables ESLint to support TypeScript

*   [ustbhuangyi/better-scroll](https://github.com/ustbhuangyi/better-scroll) - :scroll: inspired by iscroll, and it supports more features and has a better scroll perfermance

*   [umijs/dumi](https://github.com/umijs/dumi) - 📖 Static Site Generator for component library development

*   [date-fns/date-fns](https://github.com/date-fns/date-fns) - ⏳ Modern JavaScript date utility library ⌛️

*   [react-dnd/react-dnd](https://github.com/react-dnd/react-dnd) - Drag and Drop for React

*   [formatjs/formatjs](https://github.com/formatjs/formatjs) - The monorepo home to all of the FormatJS related libraries, most notably react-intl.

*   [remix-run/react-router](https://github.com/remix-run/react-router) - Declarative routing for React

*   [sveltejs/svelte](https://github.com/sveltejs/svelte) - Cybernetically enhanced web apps

*   [module-federation/module-federation-examples](https://github.com/module-federation/module-federation-examples) - Implementation examples of module federation , by the creators of module federation

*   [xcatliu/typescript-tutorial](https://github.com/xcatliu/typescript-tutorial) - TypeScript 入门教程

*   [cuixiaorui/mini-vue](https://github.com/cuixiaorui/mini-vue) - 实现最简 vue3 模型( Help you learn more efficiently vue3 source code )

*   [vitest-dev/vitest](https://github.com/vitest-dev/vitest) - A Vite-native test framework. It's fast!

*   [surmon-china/vue-codemirror](https://github.com/surmon-china/vue-codemirror) - @codemirror code editor component for @vuejs

*   [inorganik/countUp.js](https://github.com/inorganik/countUp.js) - Animates a numerical value by counting to it

*   [dolanmiu/docx](https://github.com/dolanmiu/docx) - Easily generate and modify .docx files with JS/TS with a nice declarative API. Works for Node and on the Browser.

*   [kamranahmedse/driver.js](https://github.com/kamranahmedse/driver.js) - A light-weight, no-dependency, vanilla JavaScript engine to drive the user's focus across the page

*   [pillarjs/path-to-regexp](https://github.com/pillarjs/path-to-regexp) - Turn a path string such as `/user/:name` into a regular expression

*   [SortableJS/react-sortablejs](https://github.com/SortableJS/react-sortablejs) - React bindings for SortableJS

*   [nhn/tui.editor](https://github.com/nhn/tui.editor) - 🍞📝 Markdown WYSIWYG Editor. GFM Standard + Chart & UML Extensible.

*   [MMF-FE/svgicon](https://github.com/MMF-FE/svgicon) - SVG icon components and tool set

*   [zhongsp/TypeScript](https://github.com/zhongsp/TypeScript) - TypeScript 使用手册（中文版）翻译。http://www.typescriptlang.org

*   [logaretm/vee-validate](https://github.com/logaretm/vee-validate) - ✅  Painless Vue forms

*   [any86/any-rule](https://github.com/any86/any-rule) - 🦕  常用正则大全, 支持web / vscode / idea / Alfred Workflow多平台

*   [ant-design/ant-design-icons](https://github.com/ant-design/ant-design-icons) - ⭐ Ant Design SVG Icons

*   [surmon-china/videojs-player](https://github.com/surmon-china/videojs-player) - @videojs player component for @vuejs(3) and React.

*   [voidcosmos/npkill](https://github.com/voidcosmos/npkill) - List any node\_modules 📦 dir in your system and how heavy they are. You can then select which ones you want to erase to free up space 🧹

*   [snabbdom/snabbdom](https://github.com/snabbdom/snabbdom) - A virtual DOM library with focus on simplicity, modularity, powerful features and performance.

*   [kamranahmedse/developer-roadmap](https://github.com/kamranahmedse/developer-roadmap) - Interactive roadmaps, guides and other educational content to help developers grow in their careers.

*   [yangshun/tech-interview-handbook](https://github.com/yangshun/tech-interview-handbook) - 💯 Curated coding interview preparation materials for busy software engineers

*   [algolia/docsearch](https://github.com/algolia/docsearch) - :blue\_book: The easiest way to add search to your documentation.

*   [microsoft/TypeScriptSamples](https://github.com/microsoft/TypeScriptSamples) - Community Driven Samples for TypeScript

*   [leon-ai/leon](https://github.com/leon-ai/leon) - 🧠 Leon is your open-source personal assistant.

*   [JamesIves/github-pages-deploy-action](https://github.com/JamesIves/github-pages-deploy-action) - 🚀 Automatically deploy your project to GitHub Pages using GitHub Actions. This action can be configured to push your production-ready code into any branch you'd like.

*   [excalidraw/excalidraw](https://github.com/excalidraw/excalidraw) - Virtual whiteboard for sketching hand-drawn like diagrams

*   [scastiel/3d-book-image-css-generator](https://github.com/scastiel/3d-book-image-css-generator) - Generate a 3D image from a book cover and export to HTML/CSS to embed on your website.

*   [immutable-js/immutable-js](https://github.com/immutable-js/immutable-js) - Immutable persistent data collections for Javascript which increase efficiency and simplicity.

*   [niklasvh/html2canvas](https://github.com/niklasvh/html2canvas) - Screenshots with JavaScript

*   [championswimmer/vuex-module-decorators](https://github.com/championswimmer/vuex-module-decorators) - TypeScript/ES7 Decorators to create Vuex modules declaratively

*   [rayhomie/react-qq-music](https://github.com/rayhomie/react-qq-music) - 🎵 基于 React 的QQ音乐 mac 客户端播放器（PC） Online Music Player（qqmusic）

*   [zhangyuang/ssr](https://github.com/zhangyuang/ssr) - A most advanced ssr framework support React17/React18/Vue2/Vue3 on Earth that implemented serverless-side render specification.

*   [katspaugh/wavesurfer.js](https://github.com/katspaugh/wavesurfer.js) - Audio waveform player

*   [alexjoverm/typescript-library-starter](https://github.com/alexjoverm/typescript-library-starter) - Starter kit with zero-config for building a library in TypeScript, featuring RollupJS, Jest, Prettier, TSLint, Semantic Release, and more!

*   [vuejs/vitepress](https://github.com/vuejs/vitepress) - Vite & Vue powered static site generator.

*   [vuejs/vue-class-component](https://github.com/vuejs/vue-class-component) - ES / TypeScript decorator for class-style Vue components.

*   [michaelolof/vuex-class-component](https://github.com/michaelolof/vuex-class-component) - A Type Safe Vuex Module or Store Using ES6 Classes and ES7 Decorators written in TypeScript.

*   [ktsn/vuex-class](https://github.com/ktsn/vuex-class) - Binding helpers for Vuex and vue-class-component

*   [vuejs/router](https://github.com/vuejs/router) - 🚦 The official router for Vue.js

*   [kaorun343/vue-property-decorator](https://github.com/kaorun343/vue-property-decorator) - Vue.js and Property Decorator

*   [redhat-developer/vscode-yaml](https://github.com/redhat-developer/vscode-yaml) - YAML support for VS Code with built-in kubernetes syntax support

*   [vuetifyjs/vuetify](https://github.com/vuetifyjs/vuetify) - 🐉 Vue Component Framework

*   [vuejs/devtools](https://github.com/vuejs/devtools) - ⚙️ Browser devtools extension for debugging Vue.js applications.

*   [wangeditor-team/wangEditor](https://github.com/wangeditor-team/wangEditor) - wangEditor —— 开源 Web 富文本编辑器

*   [microsoft/TypeScript](https://github.com/microsoft/TypeScript) - TypeScript is a superset of JavaScript that compiles to clean JavaScript output.

*   [loiane/javascript-datastructures-algorithms](https://github.com/loiane/javascript-datastructures-algorithms) - :books: collection of JavaScript and TypeScript data structures and algorithms for education purposes. Source code bundle of JavaScript algorithms and data structures book

*   [bytedance/bytemd](https://github.com/bytedance/bytemd) - Hackable Markdown Editor and Viewer

*   [vuejs/rollup-plugin-vue](https://github.com/vuejs/rollup-plugin-vue) - Roll .vue files

*   [Vanessa219/vditor](https://github.com/Vanessa219/vditor) - ♏  一款浏览器端的 Markdown 编辑器，支持所见即所得（富文本）、即时渲染（类似 Typora）和分屏预览模式。An In-browser Markdown editor, support WYSIWYG (Rich Text),  Instant Rendering (Typora-like) and Split View modes.

*   [thx/rap2-delos](https://github.com/thx/rap2-delos) - 阿里妈妈前端团队出品的开源接口管理工具RAP第二代

*   [apache/echarts](https://github.com/apache/echarts) - Apache ECharts is a powerful, interactive charting and data visualization library for browser

*   [youzan/vant](https://github.com/youzan/vant) - A lightweight, customizable Vue UI library for mobile web apps.

*   [vuejs/core](https://github.com/vuejs/core) - 🖖 Vue.js is a progressive, incrementally-adoptable JavaScript framework for building UI on the web.

*   [vitejs/vite](https://github.com/vitejs/vite) - Next generation frontend tooling. It's fast!

*   [vuejs/composition-api](https://github.com/vuejs/composition-api) - Composition API plugin for Vue 2

## Shell

*   [nacos-group/nacos-docker](https://github.com/nacos-group/nacos-docker) - This project contains a Docker image meant to facilitate the deployment of Nacos .

*   [webVueBlog/learn-web](https://github.com/webVueBlog/learn-web) - 🚴一份 🚀 涵盖大部分程序员所需要掌握的知识 🚄。

*   [armbian/build](https://github.com/armbian/build) - Armbian Linux Build Framework

*   [tj/n](https://github.com/tj/n) - Node version management

*   [youngyangyang04/leetcode-master](https://github.com/youngyangyang04/leetcode-master) - 《代码随想录》LeetCode 刷题攻略：200道经典题目刷题顺序，共60w字的详细图解，视频难点剖析，50余张思维导图，支持C++，Java，Python，Go，JavaScript等多语言版本，从此算法学习不再迷茫！🔥🔥 来看看，你会发现相见恨晚！🚀

*   [haixiangyan/jest-tutorial](https://github.com/haixiangyan/jest-tutorial) - 🃏《Jest 实践指南》

*   [learn-docs/learn-TypeScript](https://github.com/learn-docs/learn-TypeScript) - 🔥 learn-TypeScript 文档 https://learn-docs.github.io/learn-TypeScript/

*   [nvm-sh/nvm](https://github.com/nvm-sh/nvm) - Node Version Manager - POSIX-compliant bash script to manage multiple active node.js versions

## Go

*   [portainer/portainer](https://github.com/portainer/portainer) - Making Docker and Kubernetes management easy.

*   [alist-org/alist](https://github.com/alist-org/alist) - 🗂️A file list program that supports multiple storages, powered by Gin and Solidjs. / 一个支持多存储的文件列表程序，使用 Gin 和 Solidjs。

*   [qax-os/ElasticHD](https://github.com/qax-os/ElasticHD) - Elasticsearch 可视化DashBoard, 支持Es监控、实时搜索，Index template快捷替换修改，索引列表信息查看， SQL converts to DSL等

*   [ConnectAI-E/Feishu-OpenAI](https://github.com/ConnectAI-E/Feishu-OpenAI) - 🎒 飞书  ×（GPT-4 + DALL·E + Whisper）=  飞一般的工作体验  🚀 语音对话、角色扮演、多话题讨论、图片创作、表格分析、文档导出 🚀

*   [tealeg/xlsx](https://github.com/tealeg/xlsx) - (No longer maintained!) Go (golang) library for reading and writing XLSX files.

*   [avelino/awesome-go](https://github.com/avelino/awesome-go) - A curated list of awesome Go frameworks, libraries and software

*   [coreybutler/nvm-windows](https://github.com/coreybutler/nvm-windows) - A node.js version management utility for Windows. Ironically written in Go.

*   [nanmu42/orly](https://github.com/nanmu42/orly) - :football: Generate your own O'RLY animal book cover to troll your colleagues | 生成你自己的O'RLY动物书封面，让你的同事惊掉下巴

## Python

*   [0voice/interview\_internal\_reference](https://github.com/0voice/interview_internal_reference) - 2023年最新总结，阿里，腾讯，百度，美团，头条等技术面试题目，以及答案，专家出题人分析汇总。

*   [Significant-Gravitas/Auto-GPT](https://github.com/Significant-Gravitas/Auto-GPT) - An experimental open-source attempt to make GPT-4 fully autonomous.

*   [wangshub/Douyin-Bot](https://github.com/wangshub/Douyin-Bot) - 😍 Python 抖音机器人，论如何在抖音上找到漂亮小姐姐？

*   [THUDM/CodeGeeX](https://github.com/THUDM/CodeGeeX) - CodeGeeX: An Open Multilingual Code Generation Model

*   [Quan666/ELFChatBot](https://github.com/Quan666/ELFChatBot) - 闲聊QQ机器人，也就是人工智障

*   [nonebot/nonebot2](https://github.com/nonebot/nonebot2) - 跨平台 Python 异步聊天机器人框架 / Asynchronous multi-platform chatbot framework written in Python

*   [A-kirami/nonebot-plugin-aidraw](https://github.com/A-kirami/nonebot-plugin-aidraw) - nonebot2 AI 绘图

*   [vinta/awesome-python](https://github.com/vinta/awesome-python) - A curated list of awesome Python frameworks, libraries, software and resources

*   [euphrat1ca/fuzzdb-collect](https://github.com/euphrat1ca/fuzzdb-collect) - 网络上安全资源的搜集

*   [getsentry/sentry](https://github.com/getsentry/sentry) - Developer-first error tracking and performance monitoring

*   [jackfrued/Python-100-Days](https://github.com/jackfrued/Python-100-Days) - Python - 100天从新手到大师

*   [joke2k/faker](https://github.com/joke2k/faker) - Faker is a Python package that generates fake data for you.

*   [plctlab/v8-internals](https://github.com/plctlab/v8-internals) - 面向编译器开发人员的V8内部实现文档

*   [babysor/MockingBird](https://github.com/babysor/MockingBird) - 🚀AI拟声: 5秒内克隆您的声音并生成任意语音内容 Clone a voice in 5 seconds to generate arbitrary speech in real-time

*   [donnemartin/system-design-primer](https://github.com/donnemartin/system-design-primer) - Learn how to design large-scale systems. Prep for the system design interview.  Includes Anki flashcards.

## Dockerfile

*   [jaywcjlove/reference](https://github.com/jaywcjlove/reference) - 为开发人员分享快速参考备忘清单(速查表)

*   [goldbergyoni/nodebestpractices](https://github.com/goldbergyoni/nodebestpractices) - :white\_check\_mark:  The Node.js best practices list (May 2023)

## miscellaneous

*   [AobingJava/JavaFamily](https://github.com/AobingJava/JavaFamily) - 【Java面试+Java学习指南】 一份涵盖大部分Java程序员所需要掌握的核心知识。

*   [writethedocs/www](https://github.com/writethedocs/www) - The main website for Write the Docs.

*   [crazycodeboy/awesome-flutter-cn](https://github.com/crazycodeboy/awesome-flutter-cn) - 一个很棒的Flutter学习资源，官方教程，插件，工具，文章，App，视频教程等的资源列表

*   [webVueBlog/webVueBlog](https://github.com/webVueBlog/webVueBlog) - 🌱 面向 🤔 JavaScript爱好人员提供：👋 原创内容、JavaScript、HTML5、Node.js、Vue.js、React等一系列教程和经验分享 👍。

*   [webVueBlog/JavaScript-standard-library](https://github.com/webVueBlog/JavaScript-standard-library) - 前端进阶必看的JavaScript 标准库 JavaScript-standard-library

*   [webVueBlog/webpack-studying](https://github.com/webVueBlog/webpack-studying) - webpack - 为前端圈提供一点贡献

*   [webVueBlog/Tencent-50-Leetcode](https://github.com/webVueBlog/Tencent-50-Leetcode) - 力扣 (LeetCode) 🐧 腾讯精选练习 50 题

*   [webVueBlog/LeetCode-HOT-100](https://github.com/webVueBlog/LeetCode-HOT-100) - 力扣 (LeetCode) 🔥LeetCode HOT 100

*   [wasabeef/awesome-android-ui](https://github.com/wasabeef/awesome-android-ui) - A curated list of awesome Android UI/UX libraries

*   [CarGuo/gsy\_flutter\_book](https://github.com/CarGuo/gsy_flutter_book) - Flutter 完整开发实战详解系列，提供在线预览和pdf下载，本系列将完整讲述：如何快速从 0 开发一个完整的 Flutter APP，配套高完成度 Flutter 开源项目 GSYGithubAppFlutter ，同时会提供一些Flutter的开发细节技巧，之后深入源码和实战为你全面解析 Flutter 。

*   [webVueBlog/awesome-stars-webVueBlog](https://github.com/webVueBlog/awesome-stars-webVueBlog) - 🤩 我的star列表，每天凌晨自动更新

*   [codecrafters-io/build-your-own-x](https://github.com/codecrafters-io/build-your-own-x) - Master programming by recreating your favorite technologies from scratch.

*   [rehooks/awesome-react-hooks](https://github.com/rehooks/awesome-react-hooks) - Awesome React Hooks

*   [opendigg/awesome-github-vue](https://github.com/opendigg/awesome-github-vue) - Vue相关开源项目库汇总

*   [toutiaoio/awesome-architecture](https://github.com/toutiaoio/awesome-architecture) - 架构师技术图谱，助你早日成为架构师

*   [jobbole/awesome-java-cn](https://github.com/jobbole/awesome-java-cn) - Java资源大全中文版，包括开发库、开发工具、网站、博客、微信、微博等，由伯乐在线持续更新。

*   [sindresorhus/awesome-electron](https://github.com/sindresorhus/awesome-electron) - Useful resources for creating apps with Electron

*   [enaqx/awesome-react](https://github.com/enaqx/awesome-react) - A collection of awesome things regarding React ecosystem

*   [prakhar1989/awesome-courses](https://github.com/prakhar1989/awesome-courses) - :books: List of awesome university courses for learning Computer Science!

*   [sindresorhus/awesome](https://github.com/sindresorhus/awesome) - 😎 Awesome lists about all kinds of interesting topics

*   [getify/You-Dont-Know-JS](https://github.com/getify/You-Dont-Know-JS) - A book series on JavaScript. @YDKJS on twitter.

*   [ChickenDreamFactory/fe-chicken](https://github.com/ChickenDreamFactory/fe-chicken) - ✨✨✨ 集锦 前端JavaScript 手写题，编程题，Not just for interviews

*   [zhw2590582/live-video-study-notes](https://github.com/zhw2590582/live-video-study-notes) - :tv: 整理前端视频直播相关技术的笔记，适合想入门前端流媒体技术的人阅读

*   [nuxt/framework](https://github.com/nuxt/framework) - Old repo of Nuxt 3 framework, now on nuxt/nuxt

*   [taowen/awesome-lowcode](https://github.com/taowen/awesome-lowcode) - 国内低代码平台从业者交流

*   [hello-java-maker/JavaInterview](https://github.com/hello-java-maker/JavaInterview) - 【Java面试+Java后端技术学习指南】：一份通向理想互联网公司的面试指南，包括 Java，技术面试必备基础知识、Leetcode、计算机操作系统、计算机网络、系统设计、分布式、数据库（MySQL、Redis）、Java 项目实战等

*   [ChickenDreamFactory/fe-question](https://github.com/ChickenDreamFactory/fe-question) - fe-question，前端问答

*   [ChickenDreamFactory/JavaScript-data-structures-and-algorithms](https://github.com/ChickenDreamFactory/JavaScript-data-structures-and-algorithms) - 玩转数据结构与算法

*   [ChickenDreamFactory/node-chicken](https://github.com/ChickenDreamFactory/node-chicken) - Node.js 源码剖析

*   [0voice/from\_coder\_to\_expert](https://github.com/0voice/from_coder_to_expert) - 2021年最新总结，从程序员到CTO，从专业走向卓越，分享大牛企业内部pdf与PPT

*   [aliyunfe/weekly](https://github.com/aliyunfe/weekly) - 《阿里云前端技术周刊》

*   [jamiebuilds/babel-handbook](https://github.com/jamiebuilds/babel-handbook) - :blue\_book: A guided handbook on how to use Babel and how to create plugins for Babel.

*   [lydiahallie/javascript-questions](https://github.com/lydiahallie/javascript-questions) - A long list of (advanced) JavaScript questions, and their explanations :sparkles:

*   [ConardLi/awesome-coding-js](https://github.com/ConardLi/awesome-coding-js) - 用JavaScript实现的算法和数据结构，附详细解释和刷题指南

*   [mathjax/MathJax](https://github.com/mathjax/MathJax) - Beautiful and accessible math in all browsers

*   [justjavac/awesome-wechat-weapp](https://github.com/justjavac/awesome-wechat-weapp) - 微信小程序开发资源汇总 :100:

*   [SharingSource/LogicStack-LeetCode](https://github.com/SharingSource/LogicStack-LeetCode) - 公众号「宫水三叶的刷题日记」刷穿 LeetCode 系列文章源码

*   [0voice/audio\_video\_streaming](https://github.com/0voice/audio_video_streaming) - 音视频流媒体权威资料整理，500+份文章，论文，视频，实践项目，协议，业界大神名单。

*   [Alvin9999/new-pac](https://github.com/Alvin9999/new-pac) - 翻墙-科学上网、免费翻墙、免费科学上网、VPN、一键翻墙浏览器，vps一键搭建翻墙服务器脚本/教程，免费shadowsocks/ss/ssr/v2ray/goflyway账号/节点，免费自由上网、fanqiang、翻墙梯子，电脑、手机、iOS、安卓、windows、Mac、Linux、路由器翻墙、科学上网

*   [addyosmani/es6-equivalents-in-es5](https://github.com/addyosmani/es6-equivalents-in-es5) - WIP - ES6 Equivalents In ES5

*   [nestjs/awesome-nestjs](https://github.com/nestjs/awesome-nestjs) - A curated list of awesome things related to NestJS 😎

*   [akullpp/awesome-java](https://github.com/akullpp/awesome-java) - A curated list of awesome frameworks, libraries and software for the Java programming language.

*   [sorrycc/awesome-javascript](https://github.com/sorrycc/awesome-javascript) - 🐢 A collection of awesome browser-side  JavaScript libraries, resources and shiny things.

*   [amdjs/amdjs-api](https://github.com/amdjs/amdjs-api) - Houses the Asynchronous Module Definition API

*   [Tencent/tdesign](https://github.com/Tencent/tdesign) - Enterprise Design System

*   [CyC2018/CS-Notes](https://github.com/CyC2018/CS-Notes) - :books: 技术面试必备基础知识、Leetcode、计算机操作系统、计算机网络、系统设计

*   [hzlzh/Best-App](https://github.com/hzlzh/Best-App) - 收集&推荐优秀的 Apps/硬件/技巧/周边等

*   [FrontEndGitHub/FrontEndGitHub](https://github.com/FrontEndGitHub/FrontEndGitHub) - :octocat:GitHub最全的前端资源汇总仓库（包括前端学习、开发资源、数据结构与算法、开发工具、求职面试等）

*   [notable/notable](https://github.com/notable/notable) - The Markdown-based note-taking app that doesn't suck.

*   [CavsZhouyou/Front-End-Interview-Notebook](https://github.com/CavsZhouyou/Front-End-Interview-Notebook) - :ant:前端面试复习笔记

*   [mqyqingfeng/Blog](https://github.com/mqyqingfeng/Blog) - 冴羽写博客的地方，预计写四个系列：JavaScript深入系列、JavaScript专题系列、ES6系列、React系列。

*   [yifeikong/reverse-interview-zh](https://github.com/yifeikong/reverse-interview-zh) - 技术面试最后反问面试官的话

*   [aliyun-node/Node.js-Troubleshooting-Guide](https://github.com/aliyun-node/Node.js-Troubleshooting-Guide) - Node.js 应用线上/线下故障、压测问题和性能调优指南手册（一期更新结束）

*   [k88hudson/git-flight-rules](https://github.com/k88hudson/git-flight-rules) - Flight rules for git

*   [jiangfengming/webpack-and-spa-guide](https://github.com/jiangfengming/webpack-and-spa-guide) - Webpack 4 和单页应用入门

*   [vasanthk/how-web-works](https://github.com/vasanthk/how-web-works) - What happens behind the scenes when we type www.google.com in a browser?

*   [bmorelli25/Become-A-Full-Stack-Web-Developer](https://github.com/bmorelli25/Become-A-Full-Stack-Web-Developer) - Free resources for learning Full Stack Web Development

*   [mbeaudru/modern-js-cheatsheet](https://github.com/mbeaudru/modern-js-cheatsheet) - Cheatsheet for the JavaScript knowledge you will frequently encounter in modern projects.

*   [thedaviddias/Front-End-Checklist](https://github.com/thedaviddias/Front-End-Checklist) - 🗂 The perfect Front-End Checklist for modern websites and meticulous developers

*   [sindresorhus/promise-fun](https://github.com/sindresorhus/promise-fun) - Promise packages, patterns, chat, and tutorials

*   [jaywcjlove/mysql-tutorial](https://github.com/jaywcjlove/mysql-tutorial) - MySQL入门教程（MySQL tutorial book）

*   [byoungd/English-level-up-tips](https://github.com/byoungd/English-level-up-tips) - An advanced guide to learn English which might benefit you a lot 🎉 .  可能是让你受益匪浅的英语进阶指南。

*   [resumejob/system-design-algorithms](https://github.com/resumejob/system-design-algorithms) - Advanced data structure and algorithm for system design，系统设计需要了解的算法

*   [resumejob/awesome-resume](https://github.com/resumejob/awesome-resume) - Resume，Resume Templates，程序员简历例句，简历模版，

*   [css-modules/css-modules](https://github.com/css-modules/css-modules) - Documentation about css-modules

*   [sindresorhus/awesome-nodejs](https://github.com/sindresorhus/awesome-nodejs) - :zap: Delightful Node.js packages and resources

*   [vuejs/awesome-vue](https://github.com/vuejs/awesome-vue) - 🎉 A curated list of awesome things related to Vue.js

*   [hemanth/functional-programming-jargon](https://github.com/hemanth/functional-programming-jargon) - Jargon from the functional programming world in simple terms!

*   [jwasham/coding-interview-university](https://github.com/jwasham/coding-interview-university) - A complete computer science study plan to become a software engineer.

*   [webpack-china/awesome-webpack-cn](https://github.com/webpack-china/awesome-webpack-cn) - [印记中文](https://docschina.org/) - webpack 优秀中文文章

*   [EbookFoundation/free-programming-books](https://github.com/EbookFoundation/free-programming-books) - :books: Freely available programming books

*   [afatcoder/LeetcodeTop](https://github.com/afatcoder/LeetcodeTop) - 汇总各大互联网公司容易考察的高频leetcode题🔥         推荐免费ChatGPT网站：https://www.lintcode.com/chat-gpt?utm\_source=tf-github-codetop

*   [vue3/vue3-News](https://github.com/vue3/vue3-News) - 🔥 Find the latest breaking Vue3、Vue CLI 3+ & Vite  News. (2021/2022)

*   [yzsunlei/javascript\_concurrency\_translation](https://github.com/yzsunlei/javascript_concurrency_translation) - 《JavaScript Concurrency》英文版全书翻译 ->《JavaScript并发编程》，主要内容是Promises, Generators, Web Workers实现JavaScript并发编程相关

*   [sunniejs/wx-h5-mall](https://github.com/sunniejs/wx-h5-mall) - 微信商城

*   [xdmjun/wxappUnpacker](https://github.com/xdmjun/wxappUnpacker) -

*   [vue-bulma/vue-admin](https://github.com/vue-bulma/vue-admin) - We are refactoring it, using the latest Vue and Bulma. WIP

*   [imgcook/imgcook](https://github.com/imgcook/imgcook) - Generate pages from any sketch or images.

*   [nuxt-community/awesome-nuxt](https://github.com/nuxt-community/awesome-nuxt) - A curated list of awesome things related to Nuxt.js

## Kotlin

*   [Kr328/ClashForAndroid](https://github.com/Kr328/ClashForAndroid) - A rule-based tunnel for Android.

*   [2dust/v2rayNG](https://github.com/2dust/v2rayNG) - A V2Ray client for Android, support Xray core and v2fly core

## Jupyter Notebook

*   [CompVis/stable-diffusion](https://github.com/CompVis/stable-diffusion) - A latent text-to-image diffusion model

## HTML

*   [yangzongzhuan/RuoYi](https://github.com/yangzongzhuan/RuoYi) - :tada: (RuoYi)官方仓库 基于SpringBoot的权限管理系统 易读易懂、界面简洁美观。 核心技术采用Spring、MyBatis、Shiro没有任何其它重度依赖。直接运行即可用

*   [mdn/learning-area](https://github.com/mdn/learning-area) - Github repo for the MDN Learning Area.

*   [tailwindlabs/tailwindcss-forms](https://github.com/tailwindlabs/tailwindcss-forms) - A plugin that provides a basic reset for form styles that makes form elements easy to override with utilities.

*   [jashkenas/docco](https://github.com/jashkenas/docco) - Literate Programming can be Quick and Dirty.

*   [madrobby/zepto](https://github.com/madrobby/zepto) - Zepto.js is a minimalist JavaScript library for modern browsers, with a jQuery-compatible API

*   [leizongmin/js-xss](https://github.com/leizongmin/js-xss) - Sanitize untrusted HTML (to prevent XSS) with a configuration specified by a Whitelist

*   [jasl/ueditor\_rails](https://github.com/jasl/ueditor_rails) - \[Abandoned] UEditor integration with Rails

*   [alpinejs/alpine](https://github.com/alpinejs/alpine) - A rugged, minimal framework for composing JavaScript behavior in your markup.

*   [tailwindlabs/tailwindcss](https://github.com/tailwindlabs/tailwindcss) - A utility-first CSS framework for rapid UI development.

*   [pagedjs/pagedjs](https://github.com/pagedjs/pagedjs) - Display paginated content in the browser and generate print books using web technology

*   [aui/pinyin-engine](https://github.com/aui/pinyin-engine) - JavaScript 拼音匹配引擎

*   [sindresorhus/screenfull](https://github.com/sindresorhus/screenfull) - Simple wrapper for cross-browser usage of the JavaScript Fullscreen API

*   [ElemeFE/node-interview](https://github.com/ElemeFE/node-interview) - How to pass the Node.js interview of ElemeFE.

*   [whatwg/html](https://github.com/whatwg/html) - HTML Standard

*   [ColorlibHQ/gentelella](https://github.com/ColorlibHQ/gentelella) - Free Bootstrap 4 Admin Dashboard Template

*   [tabler/tabler](https://github.com/tabler/tabler) - Tabler is free and open-source HTML Dashboard UI Kit built on Bootstrap

*   [JeffreySu/WeixinResource](https://github.com/JeffreySu/WeixinResource) - 微信开发资源汇总 | WeChat Development Resources Summary

## Starlark

*   [rabbitmq/rabbitmq-server](https://github.com/rabbitmq/rabbitmq-server) - Open source RabbitMQ: core server and tier 1 (built-in) plugins

## Groovy

*   [gradle/gradle](https://github.com/gradle/gradle) - Adaptable, fast automation for all

## Rust

*   [johnlui/PPHC](https://github.com/johnlui/PPHC) - 📙《高并发的哲学原理》开源图书（CC BY-NC-ND）

*   [vercel/turbo](https://github.com/vercel/turbo) - Incremental bundler and build system optimized for JavaScript and TypeScript, written in Rust – including Turbopack and Turborepo.

*   [rust-lang/rust](https://github.com/rust-lang/rust) - Empowering everyone to build reliable and efficient software.

*   [i5ting/learn-rust-for-fe](https://github.com/i5ting/learn-rust-for-fe) - Rust是未来前端基础设施

*   [denoland/deno](https://github.com/denoland/deno) - A modern runtime for JavaScript and TypeScript.

## Ruby

*   [Homebrew/brew](https://github.com/Homebrew/brew) - 🍺 The missing package manager for macOS (or Linux)

*   [faker-ruby/faker](https://github.com/faker-ruby/faker) - A library for generating fake data such as names, addresses, and phone numbers.

*   [bayandin/awesome-awesomeness](https://github.com/bayandin/awesome-awesomeness) - A curated list of awesome awesomeness

## C

*   [tporadowski/redis](https://github.com/tporadowski/redis) - Native port of Redis for Windows. Redis is an in-memory database that persists on disk. The data model is key-value, but many different kind of values are supported: Strings, Lists, Sets, Sorted Sets, Hashes, Streams, HyperLogLogs. This repository contains unofficial port of Redis to Windows.

*   [bytecodealliance/wasm-micro-runtime](https://github.com/bytecodealliance/wasm-micro-runtime) - WebAssembly Micro Runtime (WAMR)

*   [cossacklabs/themis](https://github.com/cossacklabs/themis) - Easy to use cryptographic framework for data protection: secure messaging with forward secrecy and secure data storage. Has unified APIs across 14 platforms.

*   [yangkun19921001/AVFFmpegLib](https://github.com/yangkun19921001/AVFFmpegLib) - 移植 FFmpeg 最新版本v4.4-dev-416 + libx264 + freetype + fontconfig + fribidi + openh264  +libfdk-aac + gnutls + speex + libwebp + lame +opus + opencore-amr + https）编译的适用于 Android 平台的音视频编辑、视频剪辑的快速处理框架，目前内置了音视频剪辑、编辑、视频拼接、字幕、水印、倒放等功能，也可以根据 ffmpeg 命令模式来进行处理。

*   [yangkun19921001/AVEditor](https://github.com/yangkun19921001/AVEditor) - 这是一款短视频编辑 SDK，仿 DouYin 音视频处理。功能包含有美颜、滤镜、贴纸、特效、录制、分段录制、速率录制、变声、配乐、rtmp 直播推流、图片转视频、剪辑,mp4/flv 格式封装等功能。动态库用的我另一个项目编译好的 https://github.com/yangkun19921001/AVFFmpegLib

*   [yangkun19921001/AVSample](https://github.com/yangkun19921001/AVSample) - 0 基础音视频进阶路线 (MediaCodec、FFmpeg、OpenCV、OpenGL、短视频 SDK、音视频播放器、webrtc)

*   [leandromoreira/ffmpeg-libav-tutorial](https://github.com/leandromoreira/ffmpeg-libav-tutorial) - FFmpeg libav tutorial - learn how media works from basic to transmuxing, transcoding and more. Translations: 🇺🇸 🇨🇳 🇰🇷 🇪🇸 🇻🇳 🇧🇷

## C++

*   [RedisInsight/RedisDesktopManager](https://github.com/RedisInsight/RedisDesktopManager) -

*   [flutter-webrtc/flutter-webrtc](https://github.com/flutter-webrtc/flutter-webrtc) - WebRTC plugin for Flutter Mobile/Desktop/Web

*   [v8/v8](https://github.com/v8/v8) - The official mirror of the V8 Git repository

*   [electron/electron](https://github.com/electron/electron) - :electron: Build cross-platform desktop apps with JavaScript, HTML, and CSS

## CSS

*   [webVueBlog/static-html](https://github.com/webVueBlog/static-html) - 主要研究日常开发中一些功能点的实现， 旨在帮大家捋顺前端底层知识

*   [csstools/sanitize.css](https://github.com/csstools/sanitize.css) - A best-practices CSS foundation

*   [l-hammer/You-need-to-know-css](https://github.com/l-hammer/You-need-to-know-css) - 💄CSS tricks for web developers~

*   [tastejs/todomvc-app-css](https://github.com/tastejs/todomvc-app-css) - CSS for TodoMVC apps

*   [learn-docs/1024bibi](https://github.com/learn-docs/1024bibi) - 🔥 1024bibi.com bolg https://1024bibi.com/

*   [animate-css/animate.css](https://github.com/animate-css/animate.css) - 🍿 A cross-browser library of CSS animations. As easy to use as an easy thing.

*   [mladenplavsic/css-ripple-effect](https://github.com/mladenplavsic/css-ripple-effect) - Pure CSS (no JavaScript) implementation of Android Material design "ripple" animation

*   [SilurianYang/uni-app-tools](https://github.com/SilurianYang/uni-app-tools) - this is some uni-app toolset, more routing extensions

*   [necolas/normalize.css](https://github.com/necolas/normalize.css) - A modern alternative to CSS resets

## PHP

*   [fzaninotto/Faker](https://github.com/fzaninotto/Faker) - Faker is a PHP library that generates fake data for you

*   [easychen/howto-make-more-money](https://github.com/easychen/howto-make-more-money) - 程序员如何优雅的挣零花钱，2.0版，升级为小书了。Most of this not work outside China , so no English translate

*   [kuaifan/dootask](https://github.com/kuaifan/dootask) - DooTask是一款开源在线项目任务管理工具，提供各类文档协作工具、在线思维导图、在线流程图、项目管理、任务分发、即时IM，文件管理等工具；同时消息功能使用非对称加密技术让你的沟通更安全。

*   [JaguarJack/catch-admin](https://github.com/JaguarJack/catch-admin) - CatchAdmin is a background management system based on secondary development of Laravel and Element Plus. CatchAdmin still adopts the traditional front-end and back-end separation strategy, and the Laravel framework is only used as an Api output. Coupling between management system modules is minimized

*   [dedemao/alipay](https://github.com/dedemao/alipay) - 一个PHP文件搞定支付宝支付系列，包括电脑网站支付，手机网站支付，现金红包、消费红包、扫码支付，JSAPI支付、单笔转账到支付宝账户、交易结算（分账、分润）、网页授权获取用户信息等

*   [dedemao/weixinPay](https://github.com/dedemao/weixinPay) - 微信支付单文件版。一个PHP文件搞定微信支付系列。包括原生支付（扫码支付），H5支付，公众号支付，现金红包、企业付款到零钱等。新增V3版。

*   [qwqoffice/woocommerce-to-wechatapp-mini](https://github.com/qwqoffice/woocommerce-to-wechatapp-mini) - WooCommerce微信小程序迷你版

## OCaml

*   [facebook/flow](https://github.com/facebook/flow) - Adds static typing to JavaScript to improve developer productivity and code quality.

## Markdown

*   [labuladong/fucking-algorithm](https://github.com/labuladong/fucking-algorithm) - 刷算法全靠套路，认准 labuladong 就够了！English version supported! Crack LeetCode, not only how, but also why.

## Bikeshed

*   [immersive-web/webxr](https://github.com/immersive-web/webxr) - Repository for the WebXR Device API Specification.

## CoffeeScript

*   [quizlet/pinyin-converter](https://github.com/quizlet/pinyin-converter) - A simple Javascript plugin to convert pinyin with numbers to tone marks

## SCSS

*   [miniMAC/magic](https://github.com/miniMAC/magic) - CSS3 Animations with special effects

*   [phuocng/csslayout](https://github.com/phuocng/csslayout) - A collection of popular layouts and patterns made with CSS. Now it has 100+ patterns and continues growing!

*   [creativetimofficial/material-dashboard](https://github.com/creativetimofficial/material-dashboard) - Material Dashboard - Open Source Bootstrap 5 Material Design Admin

## Stylus

*   [jerryc127/hexo-theme-butterfly](https://github.com/jerryc127/hexo-theme-butterfly) -  🦋 A Hexo Theme: Butterfly

## Less

*   [TalkingData/iview-weapp](https://github.com/TalkingData/iview-weapp) - 一套高质量的微信小程序 UI 组件库

## Thanks

*   generated with [webVueBlog/awesome-stars-webVueBlog](https://github.com/webVueBlog/awesome-stars-webVueBlog)
