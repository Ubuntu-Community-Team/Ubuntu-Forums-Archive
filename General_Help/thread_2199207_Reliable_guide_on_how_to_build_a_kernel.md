---
title: "Reliable guide on how to build a kernel"
date: 2014-01-12
forum: General Help
---

### Post by Purnish_Dave on 2014-01-12
Hi,

I just spent several hours trying to build a custom kernel and then when I tried to boot into it through grub I just got a purple screen. Couldn't boot into it.

Has anyone managed to find a guide to custom build a kernel which just works?

I guess the build was fine because no errors were reported.

---

### Post by tomearp on 2014-01-12
For "simple" configuration changes, the Community Help Wiki [has a page]("https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel") that can guide you through the process.

There is also [a page]("https://help.ubuntu.com/community/Kernel/Compile") which has more detail but links to the other page on the grounds that it requires updating.

---

### Post by devine.steve on 2014-01-12
It's a rite of passage. I don't know which is worse building a kernel or X windows. Either way take your time and make sure you have a working kernel to fall back on in your grub menu. Look for instructions on building a minimal kernel.

---

### Post by tgalati4 on 2014-01-12
Purple screen is usually a modeset problem.  So set nomodeset as a kernel switch in grub.  In fact check your working grub entries and see what switches are being used.

---

### Post by Purnish_Dave on 2014-01-12
I actually managed to build a kernel using the following page:

[http://www.tecmint.com/kernel-compilation-in-debian-linux/](http://www.tecmint.com/kernel-compilation-in-debian-linux/)

I wanted to build a custom module and insmod it. Which I was able to do after building the kernel. The argument that I was supplying in the make -C part of the command was wrong .. it had to point to /lib/modules/kernel-name/build and I was pointing it to any random place where the kernel source was downloaded. Thankfully, I got it to run and the kernel works as well.

Thanks a lot, guys. Cheers. On to the next problem ..

---

### Post by Bucky Ball on 2014-01-12
Thanks for sharing. Please mark thread as solved to help others by following the instructions in my signature. Thanks.

---

