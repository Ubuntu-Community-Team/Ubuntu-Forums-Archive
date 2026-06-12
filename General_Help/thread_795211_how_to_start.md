---
title: "how to start?"
date: 2008-05-15
forum: General Help
---

### Post by iplayfast on 2008-05-15
I've got the ubuntu 8 32 bit version iso burned and have installed ubuntu in windows. 

The start menu wasn't updated, and there is no obvious way of starting it.

using the command prompt and running wubildr results in a program crash.

My machine is an 64 bit amd, running 32 bit vista home premium, with an attempt at 32 bit ubuntu install within windows (thinking that would be more likely to work then the 64 bit install)

I've also got 64 bit ubuntu installed into another partition.

---

### Post by ago on 2008-05-15
You can use EasyBCD to update the boot menu
A new version of Wubi will be available soon with the required fix.

---

### Post by iplayfast on 2008-05-15
ok... easybcd is found where? and when I run/install it what should I tell it to run?

Can I run Ubuntu from the command line in vista?  What would be the command to run it?

Also, would it be better or possible to install the 64bit ubuntu under the 32bit windows?

---

### Post by ago on 2008-05-15
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

Yes the version of Ubuntu has nothing to do with the version of Wubi, so you can have wubi 64 bits on windows 32 bits or vice versa. Of course you need a 64 bit CPU for Ubuntu 64 bits.

---

### Post by iplayfast on 2008-05-15
I think I might have a misconception. Is this running ubuntu under windows mean that it installs into a windows partition but is booted separately from windows, or is it emulated under windows so I have both Linux and windows running at the same time?

I had assumed the latter, but am now thinking I'm an idiot.

---

### Post by ago on 2008-05-15
It's the first one. Wubi produces an installation that is almost identical to a "real" one. I.E. it requires a dual boot.

If you want to access Ubuntu apps under Windows andLinux is the best option.

---

### Post by iplayfast on 2008-05-15
Thanks, [andLinux]("http://www.andlinux.org") looks to be what I want.

---

