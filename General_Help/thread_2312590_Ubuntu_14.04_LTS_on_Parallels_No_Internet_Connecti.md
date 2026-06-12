---
title: "Ubuntu 14.04 LTS on Parallels No Internet Connection"
date: 2016-02-05
forum: General Help
---

### Post by nick242 on 2016-02-05
Hello everyone, I'm currently running Ubuntu 14.04 on my macbook pro using Parallels. The problem that I'm having is that I can't seem to connect to the internet anymore. The weird thing is that I'm currently also running windows 7 on parallels and the internet connection work fine on that OS. I've been researching the problem and came across a thread that explains the problem might be that Ubuntu is currently using "eth1" instead "eth0." I'm fairly new to ubuntu so I have no idea how to change back to "eth0" if anyone can show me a step process as to how this is done, it'd be greatly appreciated.

Below is the output of *ifconfig* in the terminal...

parallels@ubuntu:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:1c:42:23:24:52  
          inet addr:169.254.4.52  Bcast:169.254.255.255  Mask:255.255.0.0
          inet6 addr: fe80::21c:42ff:fe23:2452/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8045 errors:0 dropped:31 overruns:0 frame:0
          TX packets:284 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:388645 (388.6 KB)  TX bytes:45348 (45.3 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:481 errors:0 dropped:0 overruns:0 frame:0
          TX packets:481 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:33149 (33.1 KB)  TX bytes:33149 (33.1 KB)


parallels@ubuntu:~$

---

