---
title: "Network Card problem (i think)"
date: 2007-01-31
forum: General Help
---

### Post by synthsrkl on 2007-01-31
I have been a ubuntu user for a few months now, and purchased a new computer which arrived today. It's a dell dimmension E520.

i installed edgy only to find that my internet will not work.

i have a feeling it's becuase the network card isn't recognized although i cannot be sure and don't really know how to find out if it is, or what the problem actually is, or how to fix it!

it's a LAN connection i'm trying to establish in order to get internet

any help?

---

### Post by MrNormS on 2007-01-31
Definitely suggest figuring out what network card is in the machine.  Somewhere in the Administration menu there should be something that should show you, like a device manager type thing.  I'm not on an Ubuntu machine right now, so I can't check.  If you're dual-booting just switch over to Windows for a sec and check the device manager.  The manufacturer's website might help you too.  Post the output of running this on the commandline, too:
```
ifconfig
```

---

### Post by synthsrkl on 2007-01-31
result of the ifconfig was:

-----------------------------------------------------------------------------------

eth0      Link encap:Ethernet  HWaddr 00:16:76:CD:61:73  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0xecc0 Memory:dffe0000-e0000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1284 (1.2 KiB)  TX bytes:1284 (1.2 KiB)

-----------------------------------------------------------------------------------

couldn't find any clues as to what network card i have in the device manager

i'll have a search on the manufacturer's website (intel i think)

and i don't have a dual boot btw

---

