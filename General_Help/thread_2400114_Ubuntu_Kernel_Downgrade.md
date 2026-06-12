---
title: "Ubuntu Kernel Downgrade"
date: 2018-09-02
forum: General Help
---

### Post by jbamford92 on 2018-09-02
Hi folks,

Im wondering if someone could help me out here. Is it possible to downgrade Kernel Version from 4.15 to 4.4.0? Reason is due to Firmware for Sat Tuner cards. Im stuck on 14.04 with Kernel 4.4.0 anything newer than 4.4.0 seems to fail when compiling and building Firmware for the Kernel.

Thanks.

Jack.

---

### Post by Impavidus on 2018-09-03
I don't see why you would be stuck on 14.04. Ubuntu 14.04 supports kernels 3.13 and 4.4, Ubuntu 16.04 supports kernels 4.4 and 4.15, Ubuntu 18.04 supports kernel 4.15 and will support later kernels in the future. You should be able to use 16.04 without the HWE stack. Make sure you have the linux-generic package and not the linux-generic-hwe package, and the matching header packages. A fresh install from the original 16.04 live disk or the 16.04.1 live disk should do it, but you can also arrange this on an already installed system.

---

