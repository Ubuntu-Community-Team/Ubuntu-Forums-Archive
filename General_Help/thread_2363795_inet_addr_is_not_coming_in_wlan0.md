---
title: "inet addr is not coming in wlan0"
date: 2017-06-14
forum: General Help
---

### Post by susenjitee on 2017-06-14
I have tried to connect my system with wifi. After connecting no inet addr is showing. Though I have tried both DHCP and static ip to connect. Even when I have tied to ping my router from the system its showing no network is connected.

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:163 errors:0 dropped:0 overruns:0 frame:0
          TX packets:163 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12481 (12.1 KiB)  TX bytes:12481 (12.1 KiB)

wlan0     Link encap:Ethernet  HWaddr 5C:31:3E:28:01:22  
          inet6 addr: fe80::5e31:3eff:fe28:122/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:491 (491.0 B)  TX bytes:1698 (1.6 KiB)

---

