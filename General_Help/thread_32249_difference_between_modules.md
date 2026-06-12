---
title: "difference between modules"
date: 2005-05-06
forum: General Help
---

### Post by cutOff on 2005-05-06
I was wondering which is the difference between these two modules

```
cutoff@this:~$ modinfo nvidia
filename:       /lib/modules/2.6.10-5-k7/kernel/drivers/video/nvidia.ko
license:        NVIDIA
alias:          char-major-195-*
vermagic:       2.6.10-5-k7 preempt K7 gcc-3.3
depends:        agpgart
alias:          pci:v000010DEd*sv*sd*bc03sc00i00*

cutoff@this:~$ modinfo nvidia-agp
filename:       /lib/modules/2.6.10-5-k7/kernel/drivers/char/agp/nvidia-agp.ko
license:        GPL and additional rights
author:         NVIDIA Corporation
vermagic:       2.6.10-5-k7 preempt K7 gcc-3.3
depends:        agpgart
alias:          pci:v000010DEd000001A4sv*sd*bc06sc00i00*
alias:          pci:v000010DEd000001E0sv*sd*bc06sc00i00*
srcversion:     22D229F194645825840C38C
```
Actually my Ubuntu box is using the first module

```
cutoff@this:~$ lsmod | grep nvidia
nvidia               3923644  12
agpgart                33704  3 nvidia,sis_agp
```
Which module do you think that I should use? and how do I do it?

Thanx

---

### Post by cutOff on 2005-05-07
nobody??  ](*,)

---

### Post by cutOff on 2005-06-13
_bump_

---

### Post by skoal on 2005-06-13
The first module is the one supplied from the Nvidia binary driver - called "nvidia.ko".  The second module you have listed is the one created from the kernel compile, which is for your specific chipset - "nvidia-agp.ko".  I believe the second one relates to the Nforce chipsets offered by Nvidia corp.

\\//_

---

