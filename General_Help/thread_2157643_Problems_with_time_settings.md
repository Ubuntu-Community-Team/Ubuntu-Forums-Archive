---
title: "Problems with time settings"
date: 2013-06-26
forum: General Help
---

### Post by tigerjack89 on 2013-06-26
Hey all!
I have a strange problem with the time settings on Ubuntu 13.04.
Now they are 11.30 a.m. here in Italy. Well, when I set this time in the BIOS and then access to Ubuntu, it returns 01.30 p.m; also, Windows returns 11.30 a.m.
Then, if I change the hour on Ubuntu, both manually or from the Internet, now time is right: 11.30 a.m.; however, both BIOS and Windows sign 09.30 a.m.
So, what's going on here?

I apologize for my bad bad english :(
Thanks in advance :)

---

### Post by nerdtron on 2013-06-26
Seems to me like a timezone problem. Have you set your timezone correctly?

---

### Post by tigerjack89 on 2013-06-26
> **nerdtron said:**
> Seems to me like a timezone problem. Have you set your timezone correctly?
Sure, unless they moved rome out of Italy :D

---

### Post by nerdtron on 2013-06-26
Try setting your timezone (at least in Ubuntu only) to UTC.

---

### Post by Impavidus on 2013-06-26
Linux stores the time on the bios clock by default in UTC during shutdown and at boot assumes it is set at UTC. Windows uses local time. This explains your problem.

Open the file /etc/default/rcS
```
gksudo gedit /etc/default/rcS
```
change UTC=yes into UTC=no and save the file.
When installing on a dual boot Ubuntu should apply this fix automatically, but maybe you installed Ubuntu first or installed it with the windows disk disconnected.

---

### Post by tigerjack89 on 2013-06-26
Solved!! Thank you guys for your help :)

---

