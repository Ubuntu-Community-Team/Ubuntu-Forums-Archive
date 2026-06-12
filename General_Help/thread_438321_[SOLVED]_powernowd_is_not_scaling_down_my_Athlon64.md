---
title: "[SOLVED] powernowd is not scaling down my Athlon64 3000+"
date: 2007-05-09
forum: General Help
---

### Post by sgarman on 2007-05-09
Powernowd worked perfectly on this machine under Edgy Eft, causing my CPU to dynamically change between 1 and 2 GHz. Under Fiesty, however, it stays pegged at 2 GHz. 

According to the files in /sys/devices/system/cpu/cpu0/cpufreq, I'm using the powernow-k8 scaling driver, ondemand governor, and my available frequences are 1.0 GHz, 1.8 GHz, and 2.0 GHz. So from that end everything looks as it should.

But my load average is 0.0 and my CPU never slows down. The weather is getting warmer and I like to keep my computer as cool and energy-efficient as possible. 

Any suggestions?

Thanks,

Scott

---

### Post by kerry_s on 2007-05-09
Try the i386 kernel, the generic is screwy sometimes, you can bring down the temp with athcool. Hopefully the i386 will take care of your scaling problem to.

---

### Post by sgarman on 2007-05-24
Thank you, kerry_s - switching to the 386 kernel did in fact fix the problem. My CPU is now scaling correctly. 

Regards,

Scott

---

