---
title: "Lubuntu suspend not working"
date: 2023-11-22
forum: General Help
---

### Post by portalan on 2023-11-22
Continuing from elsewhere: In the first post, please describe the CPU and graphics GPU, the release version you are running and which kernel version. 

Inspiron 545

Kernel        : Linux 5.19.0-46-generic (x86_64)
Version        : #47-Ubuntu SMP PREEMPT_DYNAMIC Fri Jun 16 13:30:11 UTC 2023
C Library        : GNU C Library / (Ubuntu GLIBC 2.36-0ubuntu4) 2.36
Distribution        : Ubuntu 22.10

display                 
       description: VGA compatible controller
       product: 82G33/G31 Express Integrated Graphics Controller
       vendor: Intel Corporation

After Suspend, XScreenSaver 2021, v6.02 comes up asking for password. The display is flickering with other lines etc. Password entered OK but display then freezes.

---

### Post by guiverc on 2023-11-22
Lubuntu 22.10 is *End of Life* and unsupported, as is all of Ubuntu 22.10.

- [https://discourse.lubuntu.me/t/lubuntu-22-10-kinetic-kudu-reaches-end-of-life-on-july-20-2023/4310](https://discourse.lubuntu.me/t/lubuntu-22-10-kinetic-kudu-reaches-end-of-life-on-july-20-2023/4310) 
- [https://fridge.ubuntu.com/2023/07/27/ubuntu-22-10-kinetic-kudu-end-of-life-reached-on-july-20-2023/](https://fridge.ubuntu.com/2023/07/27/ubuntu-22-10-kinetic-kudu-end-of-life-reached-on-july-20-2023/)

Given the 5.19 kernel has been EOL for some time, I hope you stay offline.

---

### Post by portalan on 2023-11-23
I have now upgraded to 23.10. It now works after suspend. I see that this version includes the grub line about cstate=4. There seemed to be some machine learning as I initially needed to use Control_Alt_F2 to get a working screen back. As described by MAFoElffen in [https://ubuntuforums.org/showthread.php?t=1743535](https://ubuntuforums.org/showthread.php?t=1743535)
Thanks

---

