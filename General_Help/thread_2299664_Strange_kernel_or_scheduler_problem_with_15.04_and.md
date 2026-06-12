---
title: "Strange kernel or scheduler problem with 15.04 and 15.10"
date: 2015-10-20
forum: General Help
---

### Post by onuralparslan on 2015-10-20
I see a strange kernel or scheduler problem with Kubuntu 15.04 and 15.10. I did not see such a problem with initial release of Kubuntu 15.04, but it started after I applied the latest updates to 15.04. I also tried updating to development version of 15.10 (kernel 4.2), but the problem was not fixed.

I have Intel 3960X cpu with 6 cores (Hyperthreading is disabled). The problem is that when I run many CPU intensive applications (using full CPU), I cannot fully use all the cores of CPU. I tried a very simple application which only multiplies some integers infinitly to emulate only high cpu usage with out any disk bottleneck. Sometimes the scheduler assign all the CPU intensive apps to a single core! Sometimes "top" shows that all CPU intensive apps are using only 0% CPU even though one of the cores is 100% utilized and the apps are definitely working. Sometimes, the scheduler distributes the apps to other cores, but the apps cannot use the full CPU and the CPU usage of a single app oscillates between 0% to 100%. The problem becomes visible when there are 4 or more CPU intensive apps. When there are 6 apps, the mouse movement becomes sluggish and the system becomes very unresponsive even though the "top" shows that the CPUs are not fully used. I tried adding intel_pstate=disable in GRUB and setting scheduler to SCHED_ISO, but no effect. How can I solve this problem?

---

### Post by onuralparslan on 2015-10-20
I tried different kernel versions previously installed. The current kernel 4.2.0-16 and the previous kernel 3.19.0-30 have this problem. Kernel version 3.11.0-19 worked without any problems. I wonder what changed between 3.19 and 3.11.

---

