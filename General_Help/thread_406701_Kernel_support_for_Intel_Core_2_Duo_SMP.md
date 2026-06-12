---
title: "Kernel support for Intel Core 2 Duo SMP"
date: 2007-04-11
forum: General Help
---

### Post by SniperSlap on 2007-04-11
Greetings to all!
I'm having a difficult time digging up some conclusive documentation or threads regarding SMP for Core 2 Duos.
In running either Edgy or Feisty, I have been unable to get a kernel running that recognizes both my CPUs.

I've got a plethora of the kernel images installed (I'm not kernel illiterate), yet no matter which image I use, /proc/cpuinfo just doesn't seem to reflect two CPUs...

If I just compiled my own kernel, I'm sure it'd work - but that's just not how I want to fly my Linux install (I'd install Gentoo again if I wanted that).  What is the Ubuntized way of getting the most optimized kernel, with restricted modules and SMP for Core 2 Duos???

(I swear, I've installed other kernels before for non-SMP systems and had them work...It's just this SMP that doesn't seem to want to cooperate!)

---

### Post by SniperSlap on 2007-04-11
Well, this is slightly embarassing.  I solved my own problem, yet again.

Seems like the latest kernel updates magically enabled SMP support.

For documentations' sake, I'll put down here what I did:

Hit <esc> while booting, and select the new kernel with grub!

While I was doing this before for the other kernels, there's something about this one that wants to be SMP.  So - long story short...everything works now!  Both cores are humming away happily.

Now...to figure out how to make that the default kernel without just going in and editing menu.lst!

---

### Post by pimpaulogy on 2007-04-11
Well, I am kernel illiterate, so that's why I am posting.

I am trying to setup a server that will be running a Core Duo and I wanted to make sure I used the right kernel to take advantage of it.

I am going to install the server version of Ubuntu.

What is the kernel version that you are using that now takes advantage of everything?

Ultimately, I can find out these answers by asking a colleague of mine, but I would rather find out via this great internet and not just asking him.

My experience with Linux is less than 1 year and I would say I am one step past complete newbie so thank you for your help and education on this.

---

### Post by FrostyFlames on 2007-04-11
Any kind of SMP builds are ran under then "generic" kernel type. On older versions of ubuntu I believe you would have to use the 686-smp kernels.

---

### Post by SniperSlap on 2007-04-11
> **pimpaulogy said:**
> Well, I am kernel illiterate, so that's why I am posting.

I am trying to setup a server that will be running a Core Duo and I wanted to make sure I used the right kernel to take advantage of it.

I am going to install the server version of Ubuntu.

What is the kernel version that you are using that now takes advantage of everything?

Ultimately, I can find out these answers by asking a colleague of mine, but I would rather find out via this great internet and not just asking him.

My experience with Linux is less than 1 year and I would say I am one step past complete newbie so thank you for your help and education on this.

Bear in mind the version of the server distribution you install will have a bearing on what kernel you need to install.
As best as I have determined, if you are using Edgy or a beta of Feisty, you will want to install the generic kernel.  It will have everything baked in for just about anything you want.
(I don't favor this approach as it results in a rather bloated kernel and gigantic set of modules, but it works, and is no worse than the one Windows takes.)

If you're using Dapper (6.06LTS) or earlier, your kernels are broken up a bit.

Either way, just because you install the kernels using Synaptic, doesn't mean you're using them right away.  You'll have to make sure that you're also booting the kernel.  Also note that each installed kernel must have one set of proprietary modules installed with it.  Make sure you get those in all at the same time to prevent excessive rebootage.

Right now is a bit of a tough time for people doing new installations as Feisty is being released soon.  I'd recommend that you work on ironing out a solid server structure & plan, and then reinstalling after feisty comes out (part of knowing Linux is knowing the platform you run on!).  A fresh install is always preferable to an upgrade.
I just got a new laptop, and I'm running the beta of feisty on it to see how everything will run.  Once feisty is released, I'll just do a fresh reinstall and get everything done nice & clean.

---

### Post by pimpaulogy on 2007-04-11
Thank you for the education.  I very much appreciate it.  I will keep all suggestions in mind while I go forward.

---

