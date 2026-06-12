---
title: "Unable to change to 686 kernel"
date: 2007-01-20
forum: General Help
---

### Post by trevva on 2007-01-20
Hi,

I have Xubuntu 6.10 installed on a fairly old Compaq Armada laptop (Pentium II 266MHz). It runs fairly well, but I'm trying to squeeze as much performance out of it as I possibly can, and would like to switch from the 2.6.17-10-generic kernel that I am currently using to the more suited 686 kernel.  I have been trying to do this using the descriptions found in the tips / tricks forum, ie  install the  linux-686 and linux-686-image packages using either Synaptic or apt-get. These packages seem to download and install fine, but it doesn't make any difference to the kernel that I am using. It seems to me that there may be an extra step required to enable the new kernels, but I haven't been able to find anything anywhere.... Does anyone have any suggestions?

Cheers,

Mark

---

### Post by mcduck on 2007-01-20
There is no more separate 686 kernel in 6.10, instead the generic kernel checks your CPU at boot time and then uses right optimizations automatically.

---

