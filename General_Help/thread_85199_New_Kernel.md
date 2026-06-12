---
title: "New Kernel"
date: 2005-11-02
forum: General Help
---

### Post by Drifter on 2005-11-02
On linux.org there is listed a new kernel 2.6.14, is this the new vanilla kernel there is also a patch mentioned.  Will this new kernel help with freeze ups while online.  Help Please

---

### Post by RAOF on 2005-11-02
The 2.6.14 kernel is the new vanilla kernel.  Packed full of vitamins, and the goodness of bugfixes, new drivers, and the like.  The patch will contain the differences between the new kernel **source** and the 2.6.13 (probably) kernel source.

It's possible that your freezes while online are a result of a buggy network driver which is fixed in the new kernel, but without knowing more about the problem I can't give more than that.

Building and installing a new kernel is a non-trivial enterprise.  It's not really difficult, but it's a bit of a grind getting everything just right.  If you want to try, the [wiki page]("https://wiki.ubuntu.com/KernelHowto?highlight=%28kernel%29") has a good run-down of what you need to do.  After that, you'll need to build/reinstall all of the non-free drivers you may have been using (the nvidia drivers, ndiswrapper, etc).

---

### Post by Drifter on 2005-11-02
[QUOTE=RAOF]The 2.6.14 kernel is the new vanilla kernel.  Packed full of vitamins, and the goodness of bugfixes, new drivers, and the like.  The patch will contain the differences between the new kernel **source** and the 2.6.13 (probably) kernel source.

It's possible that your freezes while online are a result of a buggy network driver which is fixed in the new kernel, but without knowing more about the problem I can't give more than that.

Building and installing a new kernel is a non-trivial enterprise.  It's not really difficult, but it's a bit of a grind getting everything just right.  If you want to try, the [wiki page]("https://wiki.ubuntu.com/KernelHowto?highlight=%28kernel%29") has a good run-down of what you need to do.  After that, you'll need to build/reinstall all of the non-free drivers you may have been using (the nvidia drivers, ndiswrapper, etc).[/QUOTE]
Will an update be forth comming that will have the kernel in it or will I need to do what you said.  I am very new to linux.

---

### Post by RAOF on 2005-11-02
No.  Ubuntu releases are essentially frozen once they're released.  Nothing new gets put into the official repositories, unless it's a (simple) bugfix or security patch.  There will not be an official, supported ubuntu release of this kernel in Breezy.  It will go in to the next version, Dapper.

There will likely be an unsupported backports repository opening containing stuff that will be in Dapper but that is not in Breezy, so once that's open you may find a kernel package in there, but I wouldn't count on it.  If you want the new kernel, you'll have to roll-your-own.

There's a good bet the new kernel wouldn't help your freezes anyway.  Have you tried to find out what causes them?  You might want to start a new thread to do that.  Fixing them will probably be easier than building the new kernel.

---

### Post by Drifter on 2005-11-02
[QUOTE=RAOF]No.  Ubuntu releases are essentially frozen once they're released.  Nothing new gets put into the official repositories, unless it's a (simple) bugfix or security patch.  There will not be an official, supported ubuntu release of this kernel in Breezy.  It will go in to the next version, Dapper.

There will likely be an unsupported backports repository opening containing stuff that will be in Dapper but that is not in Breezy, so once that's open you may find a kernel package in there, but I wouldn't count on it.  If you want the new kernel, you'll have to roll-your-own.

There's a good bet the new kernel wouldn't help your freezes anyway.  Have you tried to find out what causes them?  You might want to start a new thread to do that.  Fixing them will probably be easier than building the new kernel.[/QUOTE]
O.K. thanks for the info, I will see if I can find out what the cause of freeze is.

---

### Post by Kyral on 2005-11-02
Psh, rolling a kernel isn't that hard once you do it a couple times. Menuconfig actually has a very good help system :D

---

