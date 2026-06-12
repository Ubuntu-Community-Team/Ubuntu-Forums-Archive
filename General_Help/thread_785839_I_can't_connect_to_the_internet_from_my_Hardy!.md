---
title: "I can't connect to the internet from my Hardy!"
date: 2008-05-07
forum: General Help
---

### Post by Fixman on 2008-05-07
I can't connect to the internet from my Hardy, and I think its the network card. Can someone help me or give me new drivers for it? Here are some commands I ran:

```

dmesg | grep -i eth
[   28.135880] Driver 'sd' needs updating - please use bus_type methods
[   34.220945] sis190 Gigabit Ethernet driver 1.2 loaded.
[   34.811838] 0000:00:04.0: SiS 191 PCI Gigabit Ethernet adapter at f8896c00 (IRQ: 20), 00:1e:8c:14:0b:7d
[   34.811842] eth0: GMII mode.
[   34.811847] eth0: Enabling Auto-negotiation.
[   36.039581] udev: renamed network interface eth0 to eth1
[   45.799733] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 3458.606189] ADDRCONF(NETDEV_UP): eth1: link is not ready


ifconfig
eth1      Link encap:Ethernet  HWaddr 00:1e:8c:14:0b:7d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11612 (11.3 KB)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1392 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1392 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:69600 (67.9 KB)  TX bytes:69600 (67.9 KB)


lspci -nn | grep -i eth
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter [1039:0191] (rev 02)

```

---

### Post by Fixman on 2008-05-07
bump

---

### Post by itaintover on 2008-05-07
what kind of an internet connection are you using?

---

### Post by Fixman on 2008-05-07
> **itaintover said:**
> what kind of an internet connection are you using?

I use a ethernet cable connection.

---

### Post by Iowan on 2008-05-07
> **Fixman said:**
> eth1      Link encap:Ethernet  HWaddr 00:1e:8c:14:0b:7d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11612 (11.3 KB)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:[COLOR="Red"]0xdead[/COLOR] NAWWWW... Not the reason, but curious that the address is DEAD.

---

### Post by Fixman on 2008-05-07
> **Iowan said:**
> NAWWWW... Not the reason, but curious that the address is DEAD.

Its pretty strange, because the light of the router is green (that means that the cable is connected), and its not a installation problem, because I just changed my computer and, with the old one, it worked (and in the Live Cd does neither work).

---

### Post by Fixman on 2008-05-07
bump

---

