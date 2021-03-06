# <img src="https://github.com/guoxiaoxing/android-open-source-project-analysis/raw/master/art/logo.png" alt="Android open source project analysis" width="80" height="80" align="bottom"/> Android open source project analysis

## 功能介绍

[![License](https://img.shields.io/github/license/guoxiaoxing/android-open-source-project-analysis.svg)](https://jitpack.io/#guoxiaoxing/android-open-source-project-analysis) 
[![Stars](https://img.shields.io/github/stars/guoxiaoxing/android-open-source-project-analysis.svg)](https://jitpack.io/#guoxiaoxing/android-open-source-project-analysis) 
[![Stars](https://img.shields.io/github/forks/guoxiaoxing/android-open-source-project-analysis.svg)](https://jitpack.io/#guoxiaoxing/android-open-source-project-analysis) 
[![Forks](https://img.shields.io/github/issues/guoxiaoxing/android-open-source-project-analysis.svg)](https://jitpack.io/#guoxiaoxing/android-open-source-project-analysis) 

- [点击进入GitBook阅读](https://guoxiaoxing.gitbooks.io/android-open-source-project-analysis/content/)

第一次阅览本系列文章，请参见[导读](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/导读.md)，更多文章请参见[文章目录](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/README.md)。

- [Git repositories on android](https://android.googlesource.com/)
- [Android Open Source Project](https://source.android.com/)

**代码版本**

- 细分版本：N6F26U	
- 分支：android-7.1.1_r28	
- 版本：Nougat	
- 支持设备：Nexus 6

**分析思路**

Android是一个庞大的系统，Android Framework只是对系统的一个封装，里面还牵扯到JNI、C++、Java虚拟机、Linux系统内核、指令集等。面对如此庞大的系统，我们得有一定的
章法去阅读源码，否则就会只见树木不见森林，陷入卷帙浩繁的细节与琐碎之中。

- 不要就记录那些API调用链，Android Framework中有很多复杂的API调用链，你去关注这些东西，一点用都没有。你需要学会的是跟踪调用链和梳理流程的技巧，思考一
下作者是怎么找到关键入口的，核心的实现在什么地方。
- 要有宏观思维，要善于思考，面对一个模块，你要去思考这个模块解决了什么问题，为什么这么解决，如果让我来写，我会怎么设计，不要陷入无穷无尽的细节之中。
- 要善于去粗存精，Android Framework也是人写的，有精华也有糟粕，并不是每行代码你都需要问个为什么，很多时候没有那么多为什么，只是当时那种情况下就那样设计了。但是
对于关键函数我们要去深究它的实现细节。

**写作风格**

和大家一样，笔者也是在前人的书籍和博客的基础上开始学习Android的底层实现的，站在前人的肩膀上会看的更远。但是这些书籍和博客有个问题在于，文章中罗列了大量的代码，这样
很容易把初学者带入到琐碎的细节之中，所以本系列文章在行文中更多的会以图文并茂和提纲总结的方式来分析问题，关键的地方才会去解析源码，力求让大家从宏观上理解Android的底层实现。
另外，基本上一个主题对应一篇文章，所以文章会比较长，但是文章会有详细的标题划分和提纲总结，可以有的放矢，阅读自己需要的内容。

好了，让我们开始我们的寻宝之旅吧~😆

**Android系统架构图**

官方架构图

<img src="https://github.com/guoxiaoxing/android-open-source-project-analysis/raw/master/art/aosp_structure.png"/>

从上到下依次分为六层：

- 应用框架层
- 进程通信层
- 系统服务层
- Android运行时
- 硬件抽象层
- Linux内核层

在正式阅读本系列文章之前，请先阅读导读相关内容，这会帮助你更加快捷的理解文章内容。

- [导读](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/导读.md)

除了导读之外，为了能更好理解Android源码的设计，读者还需要掌握一定的设计模式与编程思想。

- [Android系统编程思想篇：设计模式](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/Android系统编程思想篇/Android系统编程思想篇：设计模式.md)
- [Android系统编程思想篇：软件设计原则](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/Android系统编程思想篇/Android系统编程思想篇：软件设计原则.md)

## Android应用开发实践篇

**Android界面开发**

- [01Android界面开发：View自定义实践概览](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/Android应用开发实践篇/Android界面开发/01Android界面开发：View自定义实践概览.md)
- [02Android界面开发：View自定义实践布局篇](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/Android应用开发实践篇/Android界面开发/02Android界面开发：View自定义实践布局篇.md)
- [03Android界面开发：View自定义实践绘制篇](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/Android应用开发实践篇/Android界面开发/03Android界面开发：View自定义实践绘制篇.md)
- [04Android界面开发：View自定义实践交互篇](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/Android应用开发实践篇/Android界面开发/04Android界面开发：View自定义实践交互篇.md)

**Androidy应用优化**

- [01Android应用优化：兼容适配实践指南](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/Android应用开发实践篇/Android应用优化/01Android应用优化：兼容适配实践指南.md)
- [02Android应用优化：性能优化实践指南](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/Android应用开发实践篇/Android应用优化/02Android应用优化：性能优化实践指南.md)

**其他**

- [01Android网络编程：网络编程实践](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/Android应用开发实践篇/其他/01Android网络编程：网络编程实践.md)
- [02Android混合编程：WebView实践](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/Android应用开发实践篇/其他/02Android混合编程：WebView实践.md)

## Android系统应用框架篇

**Android显示框架**

- [01Android显示框架：Android显示框架概述](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/Android系统应用框架篇/Android显示框架/01Android显示框架：Android显示框架概述.md)
- [02Android显示框架：Android应用视图的载体View](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/Android系统应用框架篇/Android显示框架/02Android显示框架：Android应用视图载体View.md)
- [03Android显示框架：Android应用视图的管理者Window](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/Android系统应用框架篇/Android显示框架/03Android显示框架：Android应用视图管理者Window.md)
- [04Android显示框架：Android应用窗口管理者WindowManager](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/Android系统应用框架篇/Android显示框架/04Android显示框架：Android应用窗口管理者WindowManager.md)
- [05Android显示框架：Android布局解析者LayoutInflater](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/Android系统应用框架篇/Android显示框架/05Android显示框架：Android布局解析者LayoutInflater.md)
- [06Android显示框架：Android列表控件RecyclerView](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/Android系统应用框架篇/Android显示框架/06Android显示框架：Android列表控件RecyclerView.md)

**Android组件框架**

- [01Android组件框架：Android组件框架概述](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/Android系统应用框架篇/Android组件框架/01Android组件框架：组件框架概述.md)
- [02Android组件框架：Android组件管理者ActivityManager](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/Android系统应用框架篇/Android组件框架/02Android组件框架：Android组件管理者ActivityManager.md)
- [03Android组件框架：Android视图容器Activity](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/Android系统应用框架篇/Android组件框架/03Android组件框架：Android视图容器Activity.md)
- [04Android组件框架：Android视图片段Fragment](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/Android系统应用框架篇/Android组件框架/04Android组件框架：Android视图片段Fragment.md)
- [05Android组件框架：Android后台服务Service](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/Android系统应用框架篇/Android组件框架/05Android组件框架：Android后台服务Service.md)
- [06Android组件框架：Android内容提供者ContentProvider](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/Android系统应用框架篇/Android组件框架/06Android组件框架：Android后台服务ContentProvider.md)
- [07Android组件框架：Android广播接收者BroadcastReceiver](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/Android系统应用框架篇/Android组件框架/07Android组件框架：Android后台服务ContentProvider.md)

**Android包管理框架**

- [01Android包管理框架：APK的打包流程](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/Android系统应用框架篇/Android包管理框架/01Android包管理框架：APK的打包流程.md)
- [02Android包管理框架：APK的安装流程](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/Android系统应用框架篇/Android包管理框架/02Android包管理框架：APK的安装流程.md)
- [03Android包管理框架：APK的加载流程](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/Android系统应用框架篇/Android包管理框架/03Android包管理框架：APK的加载流程.md)

## Android系统底层框架篇

**Android进程框架**

- [01Android进程框架：进程的创建、启动与调度流程](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/Android系统底层框架篇/Android进程框架/01Android进程框架：进程的创建、启动与调度流程.md)
- [02Android进程框架：线程与线程池](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/Android系统底层框架篇/Android进程框架/02Android进程框架：线程与线程池.md)
- [03Android进程框架：线程通信的桥梁Handler](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/Android系统底层框架篇/Android进程框架/03Android进程框架：线程通信的桥梁Handler.md)
- [04Android进程框架：进程通信的桥梁Binder](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/Android系统底层框架篇/Android进程框架/04Android进程框架：进程通信的桥梁Binder.md)
- [05Android进程框架：进程通信的桥梁Socket](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/Android系统底层框架篇/Android进程框架/05Android进程框架：进程通信的桥梁Socket.md)

**Android内存框架**

- Android系统底层框架篇：Ashmem匿名共享内存系统
- Android系统基础篇：硬件抽象层
- Android系统基础篇：智能指针
- Android系统基础篇：ART/Dalvik 虚拟机

**Android虚拟机框架**

- [01Android虚拟机框架：类加载机制](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/Android系统底层框架篇/Android虚拟机框架/01Android虚拟机框架：类加载机制.md)
- 02Android虚拟机框架：资源加载机制

有兴趣参与此项目的小伙伴可以扫码入群，本群主要讨论Android Framework、主流开源框架以及Android工程化相关技术，本群不是一个读者群，希望大家每个人都能成为项目的参与者。另外，为了营造一个
良好的技术氛围，群里尽量不要灌水闲聊~

<img src="https://github.com/guoxiaoxing/android-open-source-project-analysis/raw/master/art/wechat.JPG" width="300"/>
