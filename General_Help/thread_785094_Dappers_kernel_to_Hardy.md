---
title: "Dappers kernel to Hardy??"
date: 2008-05-07
forum: General Help
---

### Post by anaconda on 2008-05-07
Would it be possible to install an old kernel from Dappers (Ubuntu 6.06) repositories to Hardy Heron? 

I need a feature that has been removed from the kernel, but it was in Dappers kernels..

---

### Post by angry_johnnie on 2008-05-07
It's possible for different kernels to coexist, so I'm guessing you could download the packages you need  [here]("http://packages.ubuntu.com/dapper/base/").  Or, you could just add dapper repositories to your sources.list and then install it through synaptic.

A little googling for dapper repos yields [this]("http://ubuntuforums.org/showthread.php?t=185758").

---

### Post by anaconda on 2008-05-07
Thanks,

Tried it.. And got the machine to boot with Dappers kernel, And the feature I wanted worked...

BUT

The system become too unstable. Hanging every 10 mins or so, so I switched back to Hardys own kernel.

It seems that I will have to reinstall Dapper to this machine.. Damn.

---

### Post by jespdj on 2008-05-07
If you explain what that certain feature is in the Dapper kernel, then someone might be able to help you to get it working on the Hardy kernel.

Is it something that's completely removed from the Linux kernel, or something that still exists but isn't compiled into the Ubuntu kernel? If it's the latter, then you could try compiling your own custom Hardy kernel with the feature enabled.

---

### Post by anaconda on 2008-05-07
It is an undocumented feature of sambamount which we use. And it was removed from kernels (not just ubuntu kernel) after dapper.

If I mount the share with Hardys kernel and edit any file and save the changes, the contents of that file will be completely erased..


Mounting it with cifs would propably solve the problem, but unfortunately that old server doesn't support cifs..

I might be able to compile a custom kernel, but I have never tiried that yet..

---

