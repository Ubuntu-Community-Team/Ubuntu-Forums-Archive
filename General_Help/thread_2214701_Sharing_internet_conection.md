---
title: "Sharing internet conection"
date: 2014-04-02
forum: General Help
---

### Post by brendan4 on 2014-04-02
I am using my laptop with ubuntu to share internet with my desktop vis ethernet cable. The problem is is that it works for about a minute and stops working. the windows network diagnostics says the defualt gateway is not avaliable.




Thanks

---

### Post by Iowan on 2014-04-02
Perhaps a bit more information...
Are you using static IP addresses?
What is the gateway address that becomes unavailable (is it the Ubuntu box)?

---

### Post by brendan4 on 2014-04-02
No. and im not sure how to tell  I would greatly appreciate any help.


Thanks

---

### Post by Iowan on 2014-04-02
Is the laptop set up as a server or does it have Network Manager?
From a terminal, you can use **ifconfig -a** to retrieve information about your network settings.

---

### Post by brendan4 on 2014-04-02
The laptop has a network manager.  This is what I get from the comand:
```
eth0      Link encap:Ethernet  HWaddr 00:26:6c:e5:2e:f7  
          inet addr:10.42.0.1  Bcast:10.42.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:6cff:fee5:2ef7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:166 errors:0 dropped:0 overruns:0 frame:0
          TX packets:135 errors:0 dropped:0 overruns:0 carrier:5
          collisions:0 txqueuelen:1000 
          RX bytes:15689 (15.6 KB)  TX bytes:25925 (25.9 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:494 errors:0 dropped:0 overruns:0 frame:0
          TX packets:494 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:52776 (52.7 KB)  TX bytes:52776 (52.7 KB)

wlan0     Link encap:Ethernet  HWaddr e0:ca:94:83:65:7b  
          inet addr:192.168.1.117  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e2ca:94ff:fe83:657b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8914 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6875 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9014377 (9.0 MB)  TX bytes:1206054 (1.2 MB)

ubuntu@ubuntu:~$
```

---

### Post by brendan4 on 2014-04-02
Still need help.....

---

