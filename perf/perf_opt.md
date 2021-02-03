
#### 评判标准
多快好省

#### 性能的测试的一般原则
1. 有针对性的场景

#### 典型性能数据
|项目|说明||
|:-|:-|:-|
||0||

#### 网络延时
|项目|时延|说明|
|:-|-:|-:|
|上下文切换|1us||
|集群内部RTT|0.1ms||
|RAID卡写入缓存|10-100 us||
|1M数据的内存拷贝|300 us||
|1M文件写(HDD)|20ms||

#### 内存基准测试
|工具||说明|
|:-|-:|-:|
|dd|||
|stream||需要自己编译 http://github.com/jef|


#### 内存观测工具
|工具|||
|:-|-:|-:|
||||

#### 磁盘基准测试
|工具|||
|:-|-:|-:|
|fio|||

#### 磁盘观测工具
|工具|||
|:-|-:|-:|
|iostat|||

#### 磁盘优化和排查
||||
|:-|-:|-:|
|主要排查RAID缓存是否打开以及读写比例是否配置正确|||

#### 网络基准测试
|工具|||
|:-|-:|-:|
|ping|||
|qperf|侧重时延，可以用来测试TCP/UDP协议栈延时，这个是ping做不到的||
|iperf|侧重带宽||

#### 网络观测工具
|工具|||
|:-|-:|-:|
|sar| sar -n DEV 1||
|tcpdump/wireshark||更细致的网络调优|

#### 网络优化和排查
|手段|||
|:-|-:|-:|
|网卡中断绑核心|||
|增大TCP缓冲区|net.ipv4.tcp_wmem||
|网卡ring buffer|||

#### 案例 kworder:H 导致网卡丢包问题

kworker的优先级80，高于网卡软中断ksoftirq线程的60。
