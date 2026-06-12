---
title: "Internet access"
date: 2008-06-29
forum: General Help
---

### Post by Bill1961 on 2008-06-29
hello all,

I'm a newcomer to the Ubuntu World, and more than happy to leave the world of Microsoft behind. However I have a problem in accessing the internet with Ubuntu and have to keep resorting to Vista (sorry for using bad language :lolflag:) 

I use Virgin Broadband and they supply the modem  : 
a Globe Surfer II

Does anyone have either a Driver or a link to one, or can anyone give me hints on how to get around this problem.

Cheers Bill

---

### Post by iaculallad on 2008-06-29
If you booted with Ubuntu and your Globe Surfer II connected, Using the terminal, what does the command below displays?

```
ifconfig
```

---

### Post by theshadowwithanmp5n on 2008-06-29
you may be able to get the drivers and use ndiswrapper to install them
that's what i did using xp.

---

### Post by Bill1961 on 2008-07-06
sorry about the delay in getting back to you I work shift and well don't always have spare time.
the ifconfig results were as appeared on screen (including Caps)

eth0

link encap: Ethernet HWaddr 00:1a:4d;c3:ac
Inet6 addr:fe88::21a:4dff:fedd:c3ac/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1

RX packets:0 errors:0 dropped:0 frame:0
TX packets:0 errors:0 dropped:0 carrier:0
collisions:0 txquelen:1000
RX bytes:0 (0.0B) TX bytes:0 (0.0B)
Interupt:220 Base address :0xc000

lo
Link encap:Local Loopback
inet addr:127.0.0.1 mask 255.0.0.0
inet6 addr: ::1/128 Scope Host
UP LOOPBACK RUNNING MTU:16436 Metric :1
RX packets:1766 errors:0 dropped:0 overruns:0 frame:0
TX packets:1766 errors:0 dropped:0 overruns:0 carrier:0
Collisions:0txqueuelen:0
RX bytes:88580 (86.5KB) TX bytes:88588 (86.5KB)

hope this helps

---

