---
title: "Kernel compilation, how-to?"
date: 2004-11-11
forum: General Help
---

### Post by Slovak on 2004-11-11
How do I recompile this kernel? I want to change a few things around, and check what is compiled already into the kernel. Right now I am on the 686 arch, but still have the 386 kernel available.

---

### Post by az on 2004-11-11
Either install a 686 kernel (use synaptic) or download the kernel-2.6 source (also, use synaptic)

It is easier to use kernel-package.  This compiles your kernel and makes a debian package of it.  Very safe and easy to use.

install build-essential kpackage and the kernel-source.

cd /usr/src
tar xvjf kernel-source-2.6*
cd kernel-source*
make menuconfig
or anyother config tool.  You can load the current kernel's config.  It is in /boot/config-2.6-whatever...
make-kpkg --revision=1 --append-to-version-686 kernel_image kernel_headers

Wait.

Install the generated kernel-image debs.  You do not need to make the kernel-headers packages, but if you will be installing this kernel elsewhere, it is fun to be able to add more modules without the whole kernel source.

---

### Post by kamstrup on 2004-11-11
I usually just download a fresh kernel from [www.kernel.org](www.kernel.org) . The new 2.6 series is a breeze to compile and install. I have tried 2.6.9 with Ubuntu. It works fine. If you need details or help with this, just post back.

Cheers.

---

### Post by kamstrup on 2004-11-11
By the way... Is it really impossible to have ati 3d acceleration? Nvidia cards works fine. I have (almost) no experience with ati-cards... Just curious about your signature Slovak.

---

### Post by HungSquirrel on 2004-11-11
It's possible depending on the card...and the driver's mood.  I had it working for awhile, then it quit.

My problem is the DRI module.  If I tell it not to load, X starts fine.  Otherwise, I get a blank screen and I can't even Ctrl+Alt+Backspace to kill it.

---

### Post by kamstrup on 2004-11-11
You shouldn't load DRI with nvidia either. Atleast you shouldn't last time I tried :)

---

### Post by HungSquirrel on 2004-11-11
For Nvidia cards DRI is not needed but it is for ATI cards.  I don't get hardware acceleration without it.

---

### Post by HiddenWolf on 2004-11-11
I am running the fglrx drivers now. Although on an old card (R9200)

have no clue wether I have hardware accel going, but fglrxgears gets some extra frames as compared to the 'ati' driver in the xfree86 package.

---

