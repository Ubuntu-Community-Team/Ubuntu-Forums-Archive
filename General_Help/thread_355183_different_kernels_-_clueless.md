---
title: "different kernels - clueless"
date: 2007-02-06
forum: General Help
---

### Post by vdhagen on 2007-02-06
Hi folks,
sorry to bother you with another question. My aim is to enlarge a raid5-array by one disk.

I was running ubuntu kernel 6.17. In this group it was suggested that I use kernel 6.19. So I compiled a new kernel according to [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu) and got it to run.

Unfortunately with the new kernel
mdadm &#8211;grow /dev/md0 &#8211;raid-disks=4 ...
reports "resource busy"

What I don't understand: why does
"mount /dev/md0 /mnt/nas"
work well with the old kernel (still installed) but with the new kernel (otherwise identical system) reports
mount: you must specify the filesystem type??

I would be grateful for helpful hints.

Oskar

---

### Post by Arup on 2007-02-06
Oscar,

Did you compile in the RAID module in your new Kernel?

---

### Post by vdhagen on 2007-02-07
Arup,
apologies if I didn't understand your question correctly:
the system (and the different kernels) are on an SCSI disk. The RAID array consists only of IDE-drives.

Oskar

---

### Post by Arup on 2007-02-07
I just wanted to know if you have selected RAID feature when you compiled your new Kernel? I am sure you did, just wanted to confirm.

---

### Post by vdhagen on 2007-02-07
To be honest, I just executed the instructions (without understanding every step). As far as I understand I took the configuration of my working kernel as basis for my new kernel (make menuconfig).
Oskar

---

### Post by vdhagen on 2007-02-19
> **Arup said:**
> Did you compile in the RAID module in your new Kernel?

That was a good hint. Thanks. Since the raid array ran under the old kernel, I thought the settings of the old kernel were sufficient - but they weren't. Trying the kernel compilation again I found that among the raid components was one that was not selected in the old kernel: one that specifically supported adding a disk to a raid5 array.

Oskar

P.S. I still don't know why I couldn't mount the array under the new kernel - but there are more important things for me to understand.

---

