---
title: "Internet Sharing with my Xbox 360"
date: 2008-07-02
forum: General Help
---

### Post by OutOfReach on 2008-07-02
One thing that I liked about Windows was that you can Enable connection bridging/sharing with a couple of clicks. Unfortunately, its not the same for Ubuntu.
What Im basically trying to do is Share/Bridge my internet connection from my laptop to my Xbox 360.
My ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:14:22:94:c9:3b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:572 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:54050 (52.7 KB)  TX bytes:12757 (12.4 KB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:13:ce:d6:de:22  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:ceff:fed6:de22/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:501 errors:0 dropped:0 overruns:0 frame:0
          TX packets:277 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:386152 (377.1 KB)  TX bytes:64754 (63.2 KB)
          Interrupt:17 Base address:0xc000 Memory:dfbfd000-dfbfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1694 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1694 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:84852 (82.8 KB)  TX bytes:84852 (82.8 KB)
```
According to nm-applet, my WiFi is eth1
Anyone care to help? :)

---

### Post by untermensch on 2008-07-02
Are you trying to connect it threw lan or wlan?

---

### Post by OutOfReach on 2008-07-02
LAN if im correct, with cables.
From my computers Ethernet port to the Xbox's.
Like using my laptop as a 'wireless receiver' for my xbox 360

---

### Post by untermensch on 2008-07-02
I think I'm to ignorant for this post =[  sorry.

---

