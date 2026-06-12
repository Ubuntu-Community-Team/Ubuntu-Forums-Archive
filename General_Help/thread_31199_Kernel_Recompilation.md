---
title: "Kernel Recompilation"
date: 2005-05-02
forum: General Help
---

### Post by ckwong on 2005-05-02
Hi,

I have recently installed ubuntu 5.04 and I must say that it is a great OS!

My installation was done using the default i386 kernel arch, so I decided to build a new one for i686 to add support for Large memory and SMT.

I followed instructions for the Kernel Compilation HOWTO on one of the Ubuntu sites. Using the initial config file copied from /boot, I used make menuconfig to make only 3 changes: changing the architecture to Pentium 4, added support for 4GB of memory, and SMT support. Kernel recompilation was no problem and then I did a reboot.

On reboot, bootup using the new kernel, the system was noticeably slower than the using the old kernel.. Running top and cat /proc/cpuinfo showed correctly 2GB of memory and 2 CPUs (as a result of the Intel Hyperthreading)... Its just that the whole system runs very slowly now...

Does anyone here know why this might be the case? I was very sure that I only changed the system arch, large memory and smt support, so one of these options is the cause of the slow system issue?

I'd appreciate any help/suggestions offered.

Thanks,
Christian

---

### Post by shakin on 2005-05-02
I suggest using apt-get or Synaptic to install the i686 SMP kernel. There is no need to compile it yourself.

---

### Post by ckwong on 2005-05-02
I've actually tried using apt-get to install the linux 686 SMP kernel, but it didn't boot up properly either... It came up with the message "Can't find ext3fs on /dev/sda4"... 

I think its because I'm using reiserfs on the root drive (/dev/sda4) and somehow the default 686 SMP kernel doesn't load the reiserfs drivers?

---

