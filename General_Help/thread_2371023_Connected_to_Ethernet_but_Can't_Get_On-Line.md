---
title: "Connected to Ethernet but Can't Get On-Line"
date: 2017-09-09
forum: General Help
---

### Post by jaydub868 on 2017-09-09
I have a new install of UbuntuMate 17.04.  The system recognizes my Ethernet connection and says I'm connected, but I can't go on line.  When I attempt to go to a website in Firefox, it returns "Server Not Found".  Same thing with Thunderbird.  I cannot get OS updates or download programs.  Here is a print out of my ip link and ifconfig.  Any ideas for a solution?

xxx@xxx-desktop:~$ sudo ip link
[sudo] password for xxx: 
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: enp0s31f6: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP mode DEFAULT group default qlen 1000
    link/ether 70:85:c2:31:6b:d5 brd ff:ff:ff:ff:ff:ff
3: wlp9s0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/ether 92:f6:13:bf:19:2f brd ff:ff:ff:ff:ff:ff
xxx@xxx-desktop:~$ 


xxx@xxx-desktop:~$ sudo ifconfig
[sudo] password for xxx: 
enp0s31f6: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.2  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::d5b8:6ff:e219:c808  prefixlen 64  scopeid 0x20<link>
        ether 70:85:c2:31:6b:d5  txqueuelen 1000  (Ethernet)
        RX packets 2469  bytes 612042 (612.0 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1562  bytes 168338 (168.3 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  memory 0xdf700000-df720000  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 370  bytes 27438 (27.4 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 370  bytes 27438 (27.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

xxx@-desktop:~$

---

### Post by ajgreeny on 2017-09-10
First try ```
ping 216.58.213.142
``` in terminal the immediately ```
ping google.com
```
Do both work or only the first?

Both command are a ping to google.com but if the second fails you have a problem with your DNS server or settings and may be able to solve this by changing the network settings to use DNS servers 8.8.8.8

Go to the network icon in panel and "Edit Connections" from where you should be able to add 8.8.8.8 as primary DNS and 8.8.4.4 as secondary DNS.
Restart network and see if it helps.

---

