# webServer
Linux高并发服务器项目

一、技术框架

  1、线程池 + 非阻塞socket + epoll + 事件处理的并发模型；
  2、有限状态机解析HTTP请求
  3、定时更新 + 超时删除
  
二、主要内容

  1. 使用 socket 实现服务器和浏览器客户端的通信
  2. 用 epoll 事件检测技术实现 IO 多路复用，提高运行效率
  3. 采用模拟 Proactor的事件处理模式，利用线程池实现多线程机制，实现高并发通信，减少频繁创建和销毁线程带来的开销（信号和互斥锁）
  4. 主进程负责事件的读写，子线程负责业务逻辑——用有限状态机解析HTTP（GET）请求报文；生成相应的响应报文
  5. 利用链表数据结构实现定时机制（超时检测处理）

三、压力测试

  经过webbench压力测试，在虚拟机配置性能有限的情况下，仍然可以达到4800的并发量。
