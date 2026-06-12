---
title: "Can't ping localhost"
date: 2013-11-16
forum: General Help
---

### Post by matej.vince on 2013-11-16
Hi, 
i can't ping localhost. Ping end with 100% packet loss.


I checked ifconfig and there is no inet addr for loopback:

lo        Link encap:Local Loopback  
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18340 (18.3 KB)  TX bytes:18340 (18.3 KB)


Shouldn't be there also inet addr:127.0.0.1 ?

Any help would be greatly appreciated.

Thanks.

emi

---

