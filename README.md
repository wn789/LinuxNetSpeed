# Linux-NetSpeed
```
不卸载内核
wget -N --no-check-certificate "https://raw.githubusercontent.com/ylx2016/Linux-NetSpeed/2020.2.3/tcpx.sh" && chmod +x tcpx.sh && ./tcpx.sh
卸载内核 
wget -N --no-check-certificate "https://raw.githubusercontent.com/ylx2016/Linux-NetSpeed/2020.2.3/tcp.sh" && chmod +x tcp.sh && ./tcp.sh

支持版本
for bbr/bbrplus
centos6,7,8
debian8.9.10
ubuntu16,18,19
锐速保持原来一致

双持bbr+锐速
bbr 添加
echo "net.core.default_qdisc=fq" >> /etc/sysctl.conf 
echo "net.ipv4.tcp_congestion_control=bbr" >> /etc/sysctl.conf 
sysctl -p

编辑锐速文件
nano /appex/etc/config

检测代码有BUG，如果锐速正常 运行查看
bash /appex/bin/lotServer.sh status | grep "LotServer"

检查bbr ?
lsmod | grep bbr

查看当前支持TCP算法
cat /proc/sys/net/ipv4/tcp_allowed_congestion_control
查看当前运行的算法
cat /proc/sys/net/ipv4/tcp_congestion_control

命令： uname -a
作用： 查看系统内核版本号及系统名称

命令： cat /proc/version
作用： 查看目录"/proc"下version的信息，也可以得到当前系统的内核版本号及系统名称

bbsplus算法原作者
https://blog.csdn.net/dog250/article/details/80629551
bbrplus首用名 ？
https://github.com/cx9208/bbrplus
