---
title: "How can I permanently add a new module?"
date: 2014-12-10
forum: General Help
---

### Post by pgib8 on 2014-12-10
Hi Everyone.

I've been trying to learn more about linux and I'm at the point where I'm learning how to build my own module.

I compiled my own hello-world module and got a .ko file. I know how to load the module with insmod and I can see some text output by using dmesg, so that I know it's working (which it is).

I went ahead and added my .ko file into the kernel tree and made all the necessary modifications to the Makefile and Kconfig. I can run "make menuconfig" and in there I can see my new module. I have set it to 'y' to be compiled into the kernel.
Now when I boot the new kernel image, I can't tell if it's in there or not or if it's running or not.

So here is my disconnect: I can compile the kernel and get it into the boot partition and all but I never mess with the root-file-system. I know that the two must go hand-in-hand. So far I made changes to the Kernel only.

So let's say I compile a new module into the Kernel. Do I need to do anything else? I mean, do I have to make any kind of change on the rootfs?

Many thanks in advance.

---

### Post by Bashing-om on 2014-12-10
pgib8; Hello'

If you have compiled the module into the kernel, then it is available.

This tutorial may shed some light:
[https://help.ubuntu.com/community/Loadable_Modules](https://help.ubuntu.com/community/Loadable_Modules)

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

