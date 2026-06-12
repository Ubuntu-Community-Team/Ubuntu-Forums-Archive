---
title: "Artifacts in radeon driver on kernel 3.15 and upwards"
date: 2014-12-19
forum: General Help
---

### Post by Lockheed on 2014-12-19
This is what I get if I run any kernel  newer than 3.14: [https://www.youtube.com/watch?v=nx2-Fvihzxg](https://www.youtube.com/watch?v=nx2-Fvihzxg)
Those artifacts appear as soon as new kernel is selected in GRUB, and remain after logging into X session.

I get my kernels from from [ubuntu mainline]("http://kernel.ubuntu.com/~kernel-ppa/mainline/").
The last kernel working without artifacts is v3.15-rc2-trusty. All later kernels have artifacts. All later kernels also are either "-utopic" or "-vivid" instead of "-trusty", but I do not know if it is related.

I updated mesa and xorg to those form ppa:oibaf/graphics-drivers ppa, but it did not change a thing. This regression is solely kernel-related.
Is there some workaround for it?

GPU: Mobility Radeon HD 3200 (RS780M)
System: Ubuntu Mate 14.04.1
Kernels tested: 3.13-3.18.1

---

