---
title: "Nvidia Driver 390.77 not compiling in kernel 4.18-rc6 xubuntu 18.04"
date: 2018-07-23
forum: General Help
---

### Post by jason-kaiser on 2018-07-23
I dont really know who should look at this but a change in the kernel code for 4.18 is causing the nvidia drivers to fail to compile. Im sure Nvidia thinks its a kernel team problem and the kernel team blames Nvidia.

FATAL: modpost: GPL-incompatible module nvidia.ko uses GPL-only symbol '__put_devmap_managed_page'
scripts/Makefile.modpost:92: recipe for target '__modpost' failed
make[2]: *** [__modpost] Error 1
Makefile:1503: recipe for target 'modules' failed
make[1]: *** [modules] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.18.0-041800rc6-generic'
Makefile:79: recipe for target 'modules' failed
make: *** [modules] Error 2

There was a patch to remove the gpl symbol in kernel/memremap.c but it was deleted
[https://patchwork.kernel.org/patch/10473337/](https://patchwork.kernel.org/patch/10473337/)

Any help would be well, helpful.

---

### Post by cariboo on 2018-07-23
Thread moved, as 18.04 has been released.

---

### Post by Doug S on 2018-07-23
> **cariboo said:**
> Thread moved, as 18.04 has been released.yes, but the kernel is 4.18 rc series (development). We always have the current RC kernel stuff in the development area.

OP: If something changed in the kernel, then you may have to wait for nvidia to catch up. And no, it is not a mainstream kernel issue. Is this just as of kernel 4.18-rc6, or is it an issue even for 4.18-rc1?

---

### Post by jason-kaiser on 2018-07-24
This has been the same since 4.18-rc1

---

### Post by jason-kaiser on 2018-08-06
This is now fixed as of 4.18-rc7

---

