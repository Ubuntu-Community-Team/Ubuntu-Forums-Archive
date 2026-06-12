---
title: "Slow bittorrent (eventhough NAT works)"
date: 2008-03-14
forum: General Help
---

### Post by cb951303 on 2008-03-14
Hello,

I have an unusual problem. I recently changed my mother board. It has a Realtek 8110SC/8169SC gigabit ethernet card which is quite problematic in Linux. I managed to make it work it but I believe it somehow blocks my port forwarding which necessary for bittorrent. I tested modem settings in windows and [this]("http://www.utorrent.com/testport.php?port=11334") link gives success. But for same machine with same static ip, dns servers etc. it gives error ...

Here is my ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:1A:4D:F7:AB:AB  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4dff:fef7:abab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:76383 errors:0 dropped:0 overruns:0 frame:0
          TX packets:79504 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:48187656 (45.9 MB)  TX bytes:30793017 (29.3 MB)
          Interrupt:21 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

my /etc/resolv.conf
```

nameserver 208.67.222.222
nameserver 208.67.220.220
domain localdomain

```

Any ideas? Thanks very much

---

