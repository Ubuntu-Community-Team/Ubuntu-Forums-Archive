---
title: "Feisty kenel compilation"
date: 2007-07-02
forum: General Help
---

### Post by Bogaurd on 2007-07-02
I have a feisty-server system which I am using as a router on a network. Due to the setup of the network, I require the use of the IFB module in the linux kernel, for traffic shaping. Unfortunately this module does not come with ubuntu feisty.

I attempted to compile a new kernel yesterday, following the kernel compilation guide. I installed linux-source from apt, used menuconfig to enable the module I needed, and then compiled the kernel.

This machine is running on old hardware, but I still suspect there is something wrong with the amount of time & disk space it took - the compile took around 10 hours, and aborted when the machine had filled its entire hard disk - the linux source directory in which I was compiling had blown out to almost 4gb. The cpu is a Pentium 2 at 333mhz, from memory...

I've compiled kernels in the past on old hardware, and never had such problems. Could anybody suggest what the problem might be?

---

### Post by DagMan on 2007-07-03
The feisty kernel source directory does indeed really really huge to compile and takes a real long time.  I've run out of room when I compiled on a partition around that size and had to compile it elsewhere.
There isn't anything with the size or length of time, on that processor, I don't think and I think you probably were pretty close to being done before it ran out of space.

If your'e looking at a small amount of disk space then keep in mind that for me in the generic kernel /lib/module directory I have 572 megs for the custom compiled kernel that was made with just a couple of changes from the config file in the generic one, which is only 68 megs.  I don't know why that is, perhaps the hardware detection on boot during the install plays a big role or something.  After you youve built and installed your kernel image and headers though, the huge amount of space being claimed back is from deleting the now bloated source directory.  Be sure that anything you know you need to compile agianst that source is done before you delete it.

---

