---
title: "[SOLVED] Can the Gutsy kernel be customized?"
date: 2007-11-09
forum: General Help
---

### Post by Yarbo on 2007-11-09
Hi, I am wondering if it is possible for me to simply recompile the existing kernel included with Ubuntu 7.10, as it seems to be the only one that supports the current restricted driver manager. I tried to compile the latest stable kernel, but was unable to get the video drivers installed the last time.  In fact, I was unable to get the video drivers to work with the generic kernel after I tried to install it manually. Which lead to having to format my drive and start over.

I was wondering if its possible to get the performance benefits of a customized kernel, but without having to upgrade to the latest kernel. I just want to customize the 2.6.22-14 kernel for my hardware.

I've posted this question numerous times, but no ones seems to be answering me.  I've searched online, but wasn't able to really find anything.  I found SOME instructions and tried them, but it didn't work well. I am already pretty familiar with the procedure for compiling the kernel, as i've done it like 10 times or so now trying to get this to work properly, so I am not asking for a step-by-step guide.   Just wondering if it is possible, and if someone can at least point me in the right direction.  

If no one is answering me because this is in the wrong section of the forums, then at least please tell me so that I can start looking where I should.

---

### Post by yabbadabbadont on 2007-11-09
You should just be able to install the kernel sources (using apt-get, aptitude, or synaptic) and then build your kernel manually as you no doubt have done in the past.  Once you have your own kernel built, and have booted with it, you'll probably want to remove the linux-image-* and linux-restricted-modules-* packages.  By the way, you'll have to manually add your new kernel to /boot/grub/menu.lst in order to be able to boot it.

---

### Post by Yarbo on 2007-11-10
I hate to sound like n00b, but what would the kernel source packages be called?

kernel-source-<version number>, or something?

So:

```
sudo apt-get install kernel-source-2.6.22
```

I also want to patch the kernel to 2.6.22-14...  I essentially want to use the same kernel version that is distributed with gutsy, but with my own tweaks.

---

### Post by yabbadabbadont on 2007-11-10
I'm not sure about the package name, linux-source something or other.  Just use Synaptic and search both the name and description fields.  Or you could run ```
aptitude search linux
```  You should be able to pick out the correct package from the results.

---

### Post by Yarbo on 2007-11-11
Awesome, found em :).

Thanks!

---

