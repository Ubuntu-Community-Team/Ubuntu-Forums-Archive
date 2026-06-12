---
title: "Kernel Panic Help!"
date: 2007-09-05
forum: General Help
---

### Post by LiNuXxToOthEMaX on 2007-09-05
Hi I was intsalling some new drivers for my video card untill i got a kernel panic, i rebooted and it seems fine i was just wondring what causes a kernel panic here is the output:
```
scheduling while atomic: gam_server/0xffffffff/7058
scheduling while atomic: gam_server/0xffffffff/7058
scheduling while atomic: gam_server/0xffffffff/7058
 [...that message repeated a couple dozen times...]
scheduling while atomic: gam_server/0xffffffff/7058
scheduling while atomic: gam_server/0xffffffff/7058
scheduling while atomic: gam_server/0xffffffff/7058
Kernel panic - not syncing: Aiee, killing interrupt handler
```

---

### Post by Crafty Kisses on 2007-09-05
> **LiNuXxToOthEMaX said:**
> Hi I was intsalling some new drivers for my video card untill i got a kernel panic, i rebooted and it seems fine i was just wondring what causes a kernel panic here is the output:
```
scheduling while atomic: gam_server/0xffffffff/7058
scheduling while atomic: gam_server/0xffffffff/7058
scheduling while atomic: gam_server/0xffffffff/7058
 [...that message repeated a couple dozen times...]
scheduling while atomic: gam_server/0xffffffff/7058
scheduling while atomic: gam_server/0xffffffff/7058
scheduling while atomic: gam_server/0xffffffff/7058
Kernel panic - not syncing: Aiee, killing interrupt handler
```

If you're using a Mac or something to that nature then defective or incompatible RAM are the most frequent causes of kernel panics. Despite being a highly-reliable product, RAM can fail. Modern operating systems, like Mac OS X, are sensitive to RAM. Purchase additional RAM from either Apple or third parties who guarantee their RAM is compatible with Mac OS X, offer a liberal exchange policy, and provide a lifetime warranty should the RAM become defective or a later version of Mac OS X introduce incompatibilities.

---

