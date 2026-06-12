---
title: "Please set 'visible_hostname'"
date: 2007-07-09
forum: General Help
---

### Post by yinglcs2 on 2007-07-09
Hi,

I have compiled squid 2.6 stable 13 on ubuntu.
But when I run it ' ./squid -N -d 1 -D' , i get the following error:

```
# ./squid -N -d 1 -D
FATAL: Could not determine fully qualified hostname.  Please set 'visible_hostname'

Squid Cache (Version 2.6.STABLE13): Terminated abnormally.
CPU Usage: 0.008 seconds = 0.008 user + 0.000 sys
Maximum Resident Size: 0 KB
Page faults with physical i/o: 0
Aborted (core dumped)
```


Can you please tell me how to  set 'visible_hostname'?

thank you.

---

### Post by pbaumgar on 2007-07-09
Check your squid.conf file.

---

