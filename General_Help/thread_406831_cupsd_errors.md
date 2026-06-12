---
title: "cupsd errors"
date: 2007-04-11
forum: General Help
---

### Post by chrishack14 on 2007-04-11
Hi all,

As of a few days ago, I can no longer add printers using System Settings in Kubuntu.  Whenever I click on Printers > Add > Add Printer/Class, the process hangs, cupsd starts consuming a lot of system resources, and I have to manually kill kcmshell to get it to go away.  My /var/log/cups/error_log contains the following:

```
 [11/Apr/2007:09:45:29 -0500] Creating missing directory "/var/run/cups/certs"
E [11/Apr/2007:09:45:29 -0500] Unable to bind socket for address 127.0.0.1:631 - Cannot assign requested address.
E [11/Apr/2007:09:45:45 -0500] Unable to bind socket for address 127.0.0.1:631 - Cannot assign requested address.
E [11/Apr/2007:09:47:39 -0500] Creating missing directory "/var/run/cups/certs"
E [11/Apr/2007:09:53:39 -0500] Unable to bind socket for address 127.0.0.1:631 - Cannot assign requested address.
E [11/Apr/2007:09:55:02 -0500] Unable to bind socket for address 127.0.0.1:631 - Cannot assign requested address.
```

I looked around on launchpad and saw some people who once had a similar problem when upgrading to Dapper and someone suggested removing and purging the configuration files for cupsys, which I did, and then reinstalled, but that didn't help.  I'm running Edgy (64 bit version) if that's of any significance.  Any ideas?

---

### Post by heimo on 2007-04-11
If you run ifconfig and route as shown below, do you get something similar?
```
ifconfig lo
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26900 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26900 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11594295 (11.0 MiB)  TX bytes:11594295 (11.0 MiB)

route -n | grep lo
127.0.0.1       0.0.0.0         255.255.255.255 UH    0      0        0 lo
```

---

### Post by chrishack14 on 2007-04-11
Bingo!  The problem was apparently that I had introduced a syntax error in my /etc/network/interfaces file when I was trying to configure a wireless card, and that was keeping the loopback interface from being activated.  Thanks so much for your help, heimo.

---

