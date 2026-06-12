---
title: "NVIDIA Driver Installation Leads to Program Failure"
date: 2016-09-04
forum: General Help
---

### Post by theahmad on 2016-09-04
[COLOR=#242729][FONT=Arial]I have built and installed an untouched Linux 4.5.2 kernel. Then I downloaded NVIDIA device driver for my graphics card. The driver version is 367.35 and my graphics card model is GeForce GTX 960M. I have also downloaded and built MPlayer-1.2.1 and run 10 H.264 videos with frame-sizes of 1920*816. When I use the default scheduler (cfs), nothing wrong happens. But When I change the scheduler to CBS (SCHED_DEADLINE), the system stops (No kernel panic). The scheduler switch is done using sched_setattr system call at the beginning of MPlayer source code.
NOTE THAT, the same code works perfectly when I use the default Ubuntu 16.04 system with the NVIDIA driver downloaded from Ubuntu repository.
It seems that there is a problem with the driver installation. How can I confirm that the installation is OK?


[/FONT][/COLOR]

---

