---
title: "Intranet Problems (Works on Windows)"
date: 2007-08-10
forum: General Help
---

### Post by jcronkhite on 2007-08-10
I've been searching high and low and cannot seem to find a solution to this.  Maybe my keywords are poor.  In any case, here's the situation.

My computer is running Ubuntu 7.04 here at work.  I am on the same subnet as the Intranet webserver.  Firefox is unable to find my Intranet by the server name, fully qualified domain name, or IP address.  At the same time, however, I have VMware Workstation running Windows XP on the same box, and Firefox in the VM is able to find the Intranet based on all of these locations.

If any of you are having similar issues please share your experiences here until we get to the bottom of this.  I'm relatively new to linux, so it's possible I have over looked what some might consider obvious.  Thanks!

---

### Post by ddrichardson on 2007-08-10
How is the network configured? DHCP or static IP? Is there a gateway?

---

### Post by jcronkhite on 2007-08-10
All clients are DHCP with no explicit gateway settings.

---

### Post by ddrichardson on 2007-08-10
Sorry I misread this - is firefox running within XP on virtual box inside Linux? Turning off TCP segmentation offload might help:

```
ethtool -K eth0 tso off
```

---

### Post by jcronkhite on 2007-08-10
In the scenario that works, Firefox is running and able to load our Intranet inside of VMware Workstation 6 (I stopped using VirtualBox because it became unstable; see [http://forums.virtualbox.org/viewtopic.php?t=703&highlight=](http://forums.virtualbox.org/viewtopic.php?t=703&highlight=) ).  That is to say VMware is running inside of Ubuntu with Windows XP and everything works beautifully.

In the scenario that does not work, I'm simply opening Firefox on Ubuntu, outside of VMware of course, and I am unable to reach my Intranet.  I am still able to reach all websites on the Internet, including this one.

Below is the output of ifconfig (I've edited out addresses, etc.):
```

br0       Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:xxx.xxx.94.57  Bcast:xxx.xxx.94.255  Mask:255.255.255.0
          inet6 addr: ffxx::xxx:xxff:ffxx:fxxx/xx Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:168693 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59054 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:57417858 (54.7 MiB)  TX bytes:8077836 (7.7 MiB)

eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:xxx.xxx.94.57  Bcast:xxx.xxx.94.255  Mask:255.255.255.0
          inet6 addr: ffxx::xxx:xxff:ffxx:fxxx/xx Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:208849 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59514 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:65325473 (62.2 MiB)  TX bytes:8425032 (8.0 MiB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:316 errors:0 dropped:0 overruns:0 frame:0
          TX packets:316 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:34048 (33.2 KiB)  TX bytes:34048 (33.2 KiB)

tap1      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet6 addr: ffxx::xxx:xxff:ffxx:fxxx/xx Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:114462 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet1    Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:xxx.xxx.51.1  Bcast:xxx.xxx.51.255  Mask:255.255.255.0
          inet6 addr: ffxx::xxx:xxff:ffxx:fxxx/xx Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:279 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:xxx.xxx.110.1  Bcast:xxx.xxx.110.255  Mask:255.255.255.0
          inet6 addr: ffxx::xxx:xxff:ffxx:fxxx/xx Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:279 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```

---

### Post by jcronkhite on 2007-08-16
This issue was a direct result of a tunnel and bridge configuration left over by VirtualBox.  I deleted the tunnel and the bridge to resolve this issue.

Delete the tunnel:
```

sudo tunctl -d tap1

```

Take down the bridge:
```

sudo ifconfig br0 down

```

Delete the bridge:
```

sudo brctl delbr br0

```

---

### Post by gozala on 2008-05-05
Hi,

I have the same problem but can't undersatnd your solution can you help me???

me ifconfig looks like this

> 
gozala@jarti:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:8b:d1:ee:73  
          inet addr:10.123.16.129  Bcast:10.123.16.255  Mask:255.255.255.0
          inet6 addr: fe80::218:8bff:fed1:ee73/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17781 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14742 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21406646 (20.4 MB)  TX bytes:2028217 (1.9 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2024 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2024 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:101200 (98.8 KB)  TX bytes:101200 (98.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:23:21:a0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-77-23-21-A0-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)




Thanks anyway

---

