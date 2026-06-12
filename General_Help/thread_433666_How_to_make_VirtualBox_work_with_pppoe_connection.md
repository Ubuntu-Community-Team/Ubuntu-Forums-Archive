---
title: "How to make VirtualBox work with pppoe connection"
date: 2007-05-05
forum: General Help
---

### Post by burebista on 2007-05-05
Hy, I have Ubuntu 7.04, and I have instaled VirtualBox and in it Win XP, now the problem is that everthing works but not the internet connection, my connection is like this:

eth0      Link encap:Ethernet  HWaddr 00:14:22:9F:7B:1D  
          inet addr:172.16.**.**  Bcast:172.16.**.***  Mask:255.255.240.0
          inet6 addr: 2002:a9fe:2b5:5:214:22ff:fe9f:7b1d/64 Scope:Global
          inet6 addr: fec0::5:214:22ff:fe9f:7b1d/64 Scope:Site
          inet6 addr: fe80::214:22ff:fe9f:7b1d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41625 errors:0 dropped:0 overruns:0 frame:0
          TX packets:933 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5639754 (5.3 MiB)  TX bytes:229034 (223.6 KiB)
          Interrupt:19 


ppp0      Link encap:Point-to-Point Protocol  
          inet addr:86.122.**.**  P-t-P:10.0.0.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:762 errors:0 dropped:0 overruns:0 frame:0
          TX packets:815 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:657998 (642.5 KiB)  TX bytes:194561 (190.0 KiB)

Does anybody now how to make it work?
Thanks

---

