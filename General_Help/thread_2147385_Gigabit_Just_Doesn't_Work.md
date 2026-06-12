---
title: "Gigabit Just Doesn't Work"
date: 2013-05-21
forum: General Help
---

### Post by CrusaderAD on 2013-05-21
Ok, this is getting aggrivating, so I apologize if I sound like I'm venting. I have tried multiple gigabit network cards, the latest ST1000BT32 Startech, and two different gigabit routers. The machine refuse to connect and pull an IP address. I've tried different ethernet cords, different routers, different ethernet cards. I've even tried a Startech 10/100 ST100S... it just lights up and never makes a connection... just says connecting and dies. Then retries. I have also tried it on different Ubuntu installs... nothing works. Any ideas would be very appreciated!

---

### Post by CrusaderAD on 2013-05-21
This is the output of:

```
cat /etc/network/interfaces
```

> # interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


---

### Post by CrusaderAD on 2013-05-21
Results of ifconfig:

> eth0      Link encap:Ethernet  HWaddr bc:5f:f4:57:8e:13  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth2      Link encap:Ethernet  HWaddr 00:0a:cd:22:88:27  
          inet6 addr: fe80::20a:cdff:fe22:8827/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:5528 (5.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:90 errors:0 dropped:0 overruns:0 frame:0
          TX packets:90 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8661 (8.6 KB)  TX bytes:8661 (8.6 KB)


---

### Post by CrusaderAD on 2013-05-21
Anyone?

---

