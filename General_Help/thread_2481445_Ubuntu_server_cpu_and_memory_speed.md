---
title: "Ubuntu server cpu and memory speed?"
date: 2022-11-30
forum: General Help
---

### Post by josephchrzempiec on 2022-11-30
Hello, I’m running two Ubuntu servers small ones. I was wondering if it is possible if I’m not on my server that I can slow down or speed up the cpu and memory speed?

joseph

---

### Post by TheFu on 2022-11-30
> **josephchrzempiec said:**
> Hello, I’m running two Ubuntu servers small ones. I was wondering if it is possible if I’m not on my server that I can slow down or speed up the cpu and memory speed?

joseph

Yes, you can stop it completely.  "sudo shutdown -h"
You may be able to place it in standby mode, but that is dependent on hardware support for that.  I've only used standby on laptops and fortunately, it works well with my hardware. I specifically don't allow servers to standby or even HDDs to spin down.  IMHO, HDDs starting and stopping is bad for the lifespan of the HDD.  With an SSD-only system, since there's no moving parts, it is a very different problem.

Modern CPUs automatically slow and shutdown cores as needed.  
```
$ inxi -C
CPU:       6 core AMD Ryzen 5 2600 Six-Core (-MT-MCP-) cache: 3072 KB
           clock speeds: max: 3400 MHz 1: 1355 MHz 2: 1322 MHz 3: 1449 MHz
           4: 1377 MHz 5: 1377 MHz 6: 1377 MHz 7: 1278 MHz 8: 1329 MHz 9: 2612 MHz
           10: 1377 MHz 11: 1377 MHz 12: 1377 MHz
```
Note how all the cores are slower than the max for this CPU?  The base clock speed for all the Cores is 3.4GHz.  Because the workload isn't pushing it right now, they are running much slower.  All the cores are used, but that's because the system is also running 10 virtual machines.  

Let me give it some work .... and we can check the core speeds:
```
$ inxi -C
CPU:       6 core AMD Ryzen 5 2600 Six-Core (-MT-MCP-) cache: 3072 KB
           clock speeds: max: 3400 MHz 1: 3399 MHz 2: 3399 MHz 3: 2787 MHz
           4: 2794 MHz 5: 3399 MHz 6: 2719 MHz 7: 3399 MHz 8: 3399 MHz 9: 2814 MHz
           10: 2821 MHz 11: 3399 MHz 12: 2719 MHz

$ uptime 
 12:49:55 up 11 days,  4:21,  7 users,  load average: **14.01**, 6.78, 3.19

```
Ah ... it is certainly working now. All automatic.

RAM refresh rates are about keeping the bits in the desired state. [https://www.makeuseof.com/tag/quick-dirty-guide-ram-need-know/](https://www.makeuseof.com/tag/quick-dirty-guide-ram-need-know/)

---

