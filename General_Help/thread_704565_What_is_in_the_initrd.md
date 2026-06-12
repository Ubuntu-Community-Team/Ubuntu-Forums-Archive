---
title: "What is in the initrd?"
date: 2008-02-22
forum: General Help
---

### Post by ChrisMP1 on 2008-02-22
The initrd on my system takes up about fifteen seconds of boot time. On my laptop, which I need available within short notice immediately, that makes the boot much too slow. If I recompile the kernel to include important things built in instead of as modules, can I drop the initrd? Is there any important Ubuntu-y stuff in there that I could put in an rc-file, or something? I tried pruning up the rcS.d and rc2.d directories, but I couldn't disable much.

---

### Post by bodhi.zazen on 2008-02-22
For info on initrd see here:

[http://www.opennet.ru/docs/HOWTO/Kernel-HOWTO-11.html](http://www.opennet.ru/docs/HOWTO/Kernel-HOWTO-11.html)

Do not know if you "need" an initrd, depends on your hardware and ability to compile a custom kernel I would imagine.

---

### Post by banewman on 2008-02-22
I found this article helpful for speeding the boot time -
[http://www.extremetech.com/article2/0,1697,2114124,00.asp](http://www.extremetech.com/article2/0,1697,2114124,00.asp)
:)

---

### Post by mrsteveman1 on 2008-02-22
The major thing the initrd gets used for is to mount root before the kernel could otherwise load the modules for your sata controller and for the ext3 filesystem, since those things are typically modules which reside on root....catch 22 etc.

Another thing the initrd gets used for is crypto mounting of the root device like on the ubuntu alternate CD. Even if you compile in support for SATA controllers and ext3, the system needs to run cryptsetup to ask for the password and map/mount root. The only way to do that is to run scripts before root is mounted, which initrd helps with nicely.

As far as i know the ubuntu initrd is a gzipped cpio archive, so you can gunzip it and extract it with cpio -i if you want to see whats in it.

---

### Post by az on 2008-02-22
If you customize a kernel to not use an initrd, you will be doomed to recompile the kernel every single time there is an update.

I don't think you are going to shave off 15 seconds from your boot time by getting rid of an intrd anyway.

---

