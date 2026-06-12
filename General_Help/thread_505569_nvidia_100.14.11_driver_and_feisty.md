---
title: "nvidia 100.14.11 driver and feisty"
date: 2007-07-20
forum: General Help
---

### Post by jefffq on 2007-07-20
I am having trouble with the nvidia 100.14.11 driver in Ubuntu 7.04 Feisty. I have an 8600GT.

When I try to start X I get this error:
> Error: API mismatch: this NVIDIA driver component has version 100.14.11, but the NVIDIA kernel module's version does not match. Please make sure that the kernel module and all NVIDIA driver components have the same version.
(EE) NVIDIA(0): Failed to intialize the NVIDIA kernel module! Please ensure that there is a supported NVIDIA GPU in this system, and that the NVIDIA device files have been created properly.
(EE) Screen(s) found, but none have a usable configuration.

I followed this guide:
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

I have this kernel:
2.6.20-16-generic

I did install the source, although the directions on the tutorial did not work exactly as specified. The command "sudo apt-get install linux-source-`uname -r`" did not find a package. I used synaptic and installed one, the difference in the string was lacking the "-16-generic". This affected the following to commands (from the guide) as well.

When I installed the driver it told me no precompiled kernel interface was found. This is the relevant output from the log file:
> -> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.

This is the only other error I could find:
> ERROR: Kernel configuration is invalid.
include/linux/autoconf.h or include/config/auto.conf are missing.
Run 'make oldconfig && make prepare' on kernel src to fix it.

The entire log file can be found [here]("http://jefff.ca/host/nvidia-installer.txt").

Any help would be much appreciated!

---

### Post by Takmadeus on 2007-07-20
follow this tutorial:

[http://www.ubuntuparatodos.org/?q=node/169](http://www.ubuntuparatodos.org/?q=node/169)

happened to me as well, this fixed it, it is in spanish though

---

### Post by oscarsfriend on 2007-07-20
jefffq,

The error message about an API mismatch is the same problem I had.  I posted details of how to solve the problem here: [http://ubuntuforums.org/showthread.php?p=3009058#post3009058](http://ubuntuforums.org/showthread.php?p=3009058#post3009058)  Long story short: you probably have several different nvidia drivers running at the same time, so disable the others manually.

---

### Post by Digitallysick on 2007-07-30
nice thanks for this, i always have this issue

---

