---
title: "Custom kernerl compiling/implementing issues"
date: 2008-02-14
forum: General Help
---

### Post by cozadaman on 2008-02-14
Basics - I made some kernel changes. I used the kernel 2.4.22-14-generic (default Ubuntu 7.10 kernel). I only touched my processor type and a few options under processor e.g. Frequency timer, MCE, kernel crash dumps, kexec. Under power management, I disabled CPU frequency scailing, software suspend and PC Card support.

Problems - My sound now does not work, when i booted for the first time the restricted drivers box popped up but when i clicked it, it said im not using the correct kernel. These are the only things ive discovered so far.

Could any of the options above affected my sound, and if so could they affect anything else? And is there something im supposed to do so Ubuntu recognises im using a differnet kernel?

Many Thanks. [-o<

---

### Post by Gen2ly on 2008-02-14
Drivers are often compiled, its so called, against the kernel.  Meaning they are like plugins to it.  The best options IMO at this point is to either revert to the older kernel, or compile the drivers... manually.  Compiling sounds a bit obscure but usually it isn't very difficult.  If you know the version of the driver, take a look for it here in the forums and see if someone else has compiled it already.

---

### Post by cozadaman on 2008-02-17
(Forgive my "nubishness") - How do you mean compile the drivers. I do have a set of audio drivers (if that is what we're talking about haha) that i got off of my mobo CD. ive installed thoughs, but to no avail.

Development - The kernel that i thought was default is "2.4.22-14-generic", the kernel i modified and compiled is "2.4.66.9". If i got my hands on 2.4.22-14 and modified and compiled that, would this solve many problems?

---

