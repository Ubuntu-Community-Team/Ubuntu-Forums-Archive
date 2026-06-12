---
title: "Wubi downloads amd-64 when I dont have amd anything."
date: 2007-10-18
forum: General Help
---

### Post by .Michael on 2007-10-18
How can I get it to install the 386 version?

why is it downloading the amd x64 version if I have an intel chip?

---

### Post by tuxcantfly on 2007-10-18
> **.Michael said:**
> How can I get it to install the 386 version?

why is it downloading the amd x64 version if I have an intel chip?

You're running an intel core2 aren't you? That's a 64-bit processor; x86-64 processors, both Intel and AMD, are designated as "amd64" by Ubuntu.There's no option in Wubi to let you force it to use the 32-bit install, but if you just want to do a no-CD install of i386 Ubuntu, you can use [UNetbootin](http://lubi.sourceforge.net/unetbootin.html) and select the standard, 32-bit Ubuntu version to install (or you can also use the standard cd-install procedure)

---

### Post by ago on 2007-10-19
Correct, wubi 7.10 will automatically pick 64-bit version if you have a compatible machine (intel or amd). Today there is not much reason to go with 32-bits if you have a 64-bits processor. Only a few apps are not compatible (notably flash). But there are ways around that sometimes.

---

### Post by mikedep333 on 2007-11-03
Unfortunately the package w64codecs is much worse than w32codecs (they are what mplayer uses to support many formats like WMV3. (or is it WMV9?)

That is the main reason why I would like 32-bit Ubuntu on my 64-bit machine.

---

### Post by ago on 2007-11-04
start wubi with the option --32bit

---

