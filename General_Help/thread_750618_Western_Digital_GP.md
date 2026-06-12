---
title: "Western Digital GP"
date: 2008-04-09
forum: General Help
---

### Post by jabagawee on 2008-04-09
Remember the ol' issue with the laptop hard drives being thrashed by Ubuntu? Something about load/unload cycles that were supposed to be a power-saving feature but ended up killing the disk prematurely. I'm thinking about getting a Western Digital GP drive to put into a 24/7 file server. One of the "green" features of the drive is something quite similar to the feature already found in laptops: it'll park the hard drive head when unneeded. I'm wondering: will this result in the same fiasco? People with WD GP hard drives please check your load/unload cycles and tell me if it's abnormally high.

---

### Post by gerni on 2008-04-20
i had really big problems with this GP Drive -- the Load-Cycle-Count raised >100 Cycles/Hour! I tried different kernels and distros but i could not solve this problem. I changed the "clicking" Drive to a Samsung SP-F1 which does not show this annoying behavior. I called the support-hotline of Western Digital (because they did not answer my email) but they only told me that they don't offer support for Linux and they do not know about this Problem :mad: 
I'm very angry about WD and i recommend you not to buy this drive drive.

---

### Post by jabagawee on 2008-04-20
Thanks, I'm now switching to a Samsung Spinpoint. Try using hdparm to change the apm value of the WD drive to 255. That should help a bit.

---

### Post by gerni on 2008-04-21
sadly this GP-drive does not support setting the APM-"level" manually --> hdparm -B does not work

---

### Post by jabagawee on 2008-04-21
Oh... Well then, there's definitely no GP in my future then.

---

