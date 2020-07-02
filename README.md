# 《深入理解Java虚拟机（第3版）》

> **广告**：
>
> 预告下我的下一本书：[https://icyfenix.cn](https://icyfenix.cn)

　　本工程为《深入理解Java虚拟机（第3版）》书中的样例代码，以方便读者自行测试。部分代码需要在特定的虚拟机版本、参数下运行，在代码前均已“VM Args”的注释进行标注。

　　书中的勘误也会在本文中持续更新，读者可通过issues提交新的勘误，如对新版有任何建议，也欢迎以issues或任何其他您方便的形式提出。

### 勘误列表：

- **Page 77**：发生垃圾【搜集】时，将Eden和Survivor中仍然存活的对象一次性过拷贝到另外一块Survivor空间上
<br>更正：发生垃圾【收集】时，将Eden和Survivor中仍然存活的对象一次性过拷贝到另外一块Survivor空间上

- **Page 128**：JDK 9之前虚拟机运行在Server模式下的默认值，打开此开关后，使用【Parallel Scavenge + Serial Old（PS MarkSweep）的】收集器组合进行内存回收
<br>更正：3 JDK 9之前虚拟机运行在Server模式下的默认值，打开此开关后，使用【Parallel】收集器组合进行内存回收

- **Page 259**：3 monitorenter // 以【栈定】元素（即f）作为锁，开始同步
<br>更正：3 monitorenter // 以【栈顶】元素（即f）作为锁，开始同步

- **Page 265**：上述代码运行之后，只会输出“SuperClass init!”
<br>更正：上述代码运行之后，【除value的值外，】只会输出“SuperClass init!”

#### 以下勘误内容已在第4次重印版（2020-6-10日）修正
------
- **Page 25**：即不能动态加载其他【编译器】不可知的代码和类库
<br>更正：即不能动态加载其他【编译期】不可知的代码和类库

- **Page 30**：JDK 7则【还完全】处于研发状态的半成品。
<br>更正：JDK 7则【完全是】处于研发状态的半成品。

- **Page 38**：由于JDK12已EOL，RedHat的GitHub上目前只维护8、11两个LTS和13这个正在半年支持期内的JDK版本，JDK12的Repo已经关闭（但从Git的History中挖掘出来是很容易的），为了便于读者获取 CMakeLists.txt，我上传了一份到本仓库中。此文件版权归原作者所有。（编辑在更新勘误时可跳过此条）

- **Page 48**：Java是一门面向对象的编程语言，Java程序运行过程中【无时无刻都】有对象被创建出来
<br>更正：Java是一门面向对象的编程语言，Java程序运行过程中【每时每刻都】有对象被创建出来

- **Page 58-60**：代码清单2-4、2-5的输出，在代码中定义的方法名是“stackLeak()”，在输出日志中看到的堆栈的方法名是“leak()”。这个是代码粘贴后整理编辑过方法名，不影响意思表达。（方法名在日志、代码中出现次数较多，编辑处理这条勘误时请单独联系我提供更正详情）

- **Page 80**：HotSpot虚拟机里面关注吞吐量的Parallel 【Scavenge】收集器是基于标记-整理算法的。
<br>更正：HotSpot虚拟机里面关注吞吐量的Parallel 【Old】收集器是基于标记-整理算法的。

- **Page 97**：并发回收时垃圾收集线程【只占用不超过25%】的处理器运算资源，并且会随着处理器核心数量的增加而下降。
<br>更正：并发回收时垃圾收集线程【占用不少于25%】的处理器运算资源，并且会随着处理器核心数量的增加而下降。

- **Page 105**：图3-14中第3行，G1收集器的Compact阶段应该为【浅色】，这个我交上去的原图是正确的，但编辑重新画图时候涂层了深色。请编辑更新新版的时候注意一下。

- **Page 106**：在回收时通过这张表格就可以得出哪些Region之间产生了【跨代引用】。
<br>更正：在回收时通过这张表格就可以得出哪些Region之间产生了【跨Region的引用】。

- **Page 107**：图3-15中，两个X的位置打错了，应该在5行3列、3行1列处打X

- **Page 106**：降低了处理跨代指针时的记忆集维护消耗，也降低了伪共享问题（【见3.4.4节】）的发生概率。
<br>更正：降低了处理跨代指针时的记忆集维护消耗，也降低了伪共享问题（【见3.4.5节】）的发生概率。

- **Page 134**：如果在Survivor空间中【相同年龄】所有对象大小的总和大于Survivor空间的一半
<br>更正：如果在Survivor空间中【低或等于某个年龄的】所有对象大小的总和大于Survivor空间的一半

- **Page 134**：满足【同年】对象达到Survivor空间的一半规则
<br>更正：满足【低于或等于某年龄的】对象达到Survivor空间的一半规则

- **Page 162-163**：代码中类名“SynAddRunalbe”中英文“Runalbe”为拼写错误，应为“SynAddRunnable”，代码中一共有4处，图片中有1处。

- **Page 239**：Exceptions属性的作用是列举出方法中可能抛出的受查异常（Checked 【Excepitons】）
<br>更正：Exceptions属性的作用是列举出方法中可能抛出的受查异常（Checked 【Exceptions】）

- **Page 265**：创建动作由字节码指令【newarray】触发
<br>更正：创建动作由字节码指令【anewarray】触发

- **Page 272**：【JDK 7及之前】，HotSpot使用永久代来实现方法区时，实现是完全符合这种逻辑概念的；【而在JDK 8及之后】，类变量则会随着Class对象一起存放在Java堆中
<br>更正：【JDK 7之前】，HotSpot使用永久代来实现方法区时，实现是完全符合这种逻辑概念的；【而在JDK 7及之后】，类变量则会随着Class对象一起存放在Java堆中

- **Page 274**：被访问类C是public的，不与访问类D处于同一个模块，但是被访问类C的模块允许【被访问类D】的模块进行访问。
<br>更正：被访问类C是public的，不与访问类D处于同一个模块，但是被访问类C的模块允许【访问类D】的模块进行访问。

- **Page 312**：运行结果的第3行：This 【gay】 has $2
<br>更正：This 【guy】 has $2

- **Page 314**：脚注三最后一行：具体可【常见】第11章关于方法内联的内容。
<br>更正：具体可【参见】第11章关于方法内联的内容。

- **Page 461**：图12-6，New->Running，Running->Terminated这两个是单向箭头，交给编辑的原稿上也还是单向的，应该是排版修图时搞错变成双向了，请编辑同学修正过来。

- **Page 462**：【以前处理一个请求可以允许花费很长时间在单体应用中】，具有这种线程切换成本也是无伤大雅的
<br>语句不通，更正为：【在以前的单体应用中，处理一个请求可以允许花费很长时间】，具有这种线程切换成本也是无伤大雅的

- **Page 462**：现实的需求在迫使Java去研究新的解决方案，【同】大家又怀念起以前绿色线程的种种好处
<br>更正为：现实的需求在迫使Java去研究新的解决方案，【此时】大家又怀念起以前绿色线程的种种好处

#### 以下勘误内容已在第3次重印版（2020-2-20日）修正
------
- **Page 27**：到了JDK 10，HotSpot又重构了Java虚拟机的垃圾收集器接口 （Java Virtual Machine 【Compiler】 Interface）
  <br>更正：到了JDK 10，HotSpot又重构了Java虚拟机的垃圾收集器接口 （Java Virtual Machine 【Garbage】 Interface）
  
- **Page 37**：譬如【Eclipst】 CDT或者NetBeans来进行的话
  <br>更正：譬如【Eclipse】 CDT或者NetBeans来进行的话
  
- **Page 110**：对象的读取、写入、对象的比较、【为对象哈希值计算】、用对象加锁等等
  <br>更正：对象的读取、写入、对象的比较、【为对象计算哈希值】、用对象加锁等等
  
- **Page 113**：图3-19中，【Larage】为笔误，应为【Large】

- **Page 238**：13: iload_1 后的注释应该是字节码第14行的，即
  >   13:  iload_1   // 保存x到returnValue中，此时x=2  
  >   14:  istore  4  

  改为：
  >   13:  iload_1    
  >   14:  istore  4  // 保存x到returnValue中，此时x=2
  
- **Page 254**：算术指令用于对【两个操作数栈上的值】进行某种特定运算
 <br>对语序修改以避免歧义：算术指令用于对【操作数栈上的两个值】进行某种特定运算
 
- **Page 259**：13 astore_3 后注释【Taget】为笔误，应为【Target】

- **Page 265/266**：在266页正文中出现两次注释一，其中第一个注释是265页才对，应该是排版问题，请编辑再版时注意。

- **Page 278**：代码清单7-5，第一行注释：给变量【复制】可以正常编译通过
 <br>更正：
 给变量【赋值】可以正常编译通过
 
 - **Page 278**：代码清单7-5，第二行注释：这句编译器会提示“非法【向前】引用”
 <br>更正：
 这句编译器会提示“非法【前向】引用”
 
- **Page 290**：用在IntelliJ 【IDE】、Eclipse这些IDE上做HotSwap……
 <br>更正：
 用在IntelliJ 【IDEA】、Eclipse这些IDE上做HotSwap……
 
- **Page 312**：代码实例中出现三处【gay】，譬如Father gay = new Son(); 均应为【guy】，这个不影响代码运行，只是不太雅观。

- **Page 317**：产生这种差别产生的根本原因是Java语言在编译期间【却】已将println(String)方法完整的符号引用。
 <br>更正：产生这种差别产生的根本原因是Java语言在编译期间【就】已将println(String)方法完整的符号引用。

- **Page 322**：由于注解中John Rose博客文章中的代码托管网站Kenai.com已经关闭，为了便于读者获取INDY工具，我上传了一份到本仓库中(源码，在src/indify目录)。此文件版权归原作者John Rose所有。（编辑在更新勘误时可跳过此条）

- **Page 348**：通常解决【类】问题有以下几种途径
 <br>更正：通常解决【此类】问题有以下几种途径

- **Page 372**：譬如将【代码清单10-2】稍微修改一下，变成下面代码清单10-7这个样子
 <br>更正：譬如将【代码清单10-4】稍微修改一下，变成下面代码清单10-7这个样子

- **Page 396**：【图11-2】和【图11-3】都仅仅是描述了客户端模式虚拟机的即时编译方式
 <br>更正：【图11-3】和【图11-4】都仅仅是描述了客户端模式虚拟机的即时编译方式
 
  
#### 以下勘误内容已在第2次重印版（2019-12-27日）修正
------
- **前言部分**：读者反馈信箱：understandjvm@gmail.com 
  <br>更正：由于这个信箱由于一直只收未发，刚印刷后收到Google的通知此账号已自动作废。而且根据Google规定，作废后无法注册同名邮箱。下次重印将修改为本工程地址:https://github.com/fenixsoft/jvm_book。

- **Page 9**：支持HTTP 2客户【单】API等91个JEP
  <br>更正：支持HTTP 2客户【端】API等91个JEP

- **Page 64**：在【代码清单2-8】里笔者借助了CGLib……
  <br>更正：在【代码清单2-9】里笔者借助了CGLib……

- **Page 368**: 【ArrayList&lt;int&gt;】与ArrayList&lt;String&gt;其实是同一个类型
  <br>更正：【ArrayList&lt;Integer&gt;】与ArrayList&lt;String&gt;其实是同一个类型
