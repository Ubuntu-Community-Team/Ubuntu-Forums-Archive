---
title: "What has been compiled in my kernel?"
date: 2007-11-23
forum: General Help
---

### Post by trazart on 2007-11-23
How can I know what has been compiled in my kernel? I'm also interested in what has been compiled as module.

I'm using the 2.6.22-14-generic kernel that is installed with Gutsy.

Thanks in advance

---

### Post by Whiffle on 2007-11-23
If you've got the kernel sources installed, you can open up a terminal, go to 

/usr/src/linux


and run

sudo make menuconfig

And browse through there to see whats modules (marked with an M), and whats been compiled in (marked with a *).  Don't change anything though unless you intend to learn to compile your own kernel.  Even if you do accidently change something though, the configuration is backed up in /boot

---

### Post by scorp123 on 2007-11-23
> **trazart said:**
>  How can I know what has been compiled in my kernel? Take a look at this file:  **/boot/config-2.6.22-14-generic**

> **trazart said:**
>   I'm also interested in what has been compiled as module. See above file. If in the file it says e.g. ```
BLAHBLAHSOMETHING=m
``` ... then that should be a module and there should be a *.ko file for this somewhere underneath  **/lib/modules/2.6.22-14-generic**

If it says ```
BLAHSOMETHINGELSE=y
``` then that's not a module but compiled directly into the kernel. If it says "=n" or if the line is commented out then the option in question is not active.

---

### Post by trazart on 2007-11-23
Thank you ;)

I have downloaded the source and I will copy the config file to the source directory to see it with menuconfig.

---

