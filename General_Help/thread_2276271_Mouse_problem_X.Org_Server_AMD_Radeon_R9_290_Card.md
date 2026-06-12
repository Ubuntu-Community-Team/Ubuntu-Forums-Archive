---
title: "Mouse problem X.Org Server AMD Radeon R9 290 Card"
date: 2015-05-01
forum: General Help
---

### Post by aimless2 on 2015-05-01
Hello, I recently had a problem in GIMP where it would crash doing certain operation.  I switched from using the proprietary AMD Radeon driver to the open source X.Org Server and Gimp works great along with everything else it seems EXCEPT now my mouse looks weird.  Whether it's the mouse or the little hand it's distorted.  Looks like it's been squished down and theres some weird print hanging off it.

I'm using AMD Radeon R9 290 card on a Crosshair V formula Z board.  16 GB Ram.  AMD 8120 processor.

I tried re-installing X.Org and it didn't work.  Is there a way to override how the mouse is presented so it looks normal?  Or maybe something else I can do to fix the problem?

EDIT: Ubuntu 14.04 64 bit

---

### Post by kagashe on 2015-05-01
Which kernel you are using? (type uname -a in the terminal)
If you have lower version of the kernel try booting with it and see whether you get normal mouse pointer.

---

### Post by aimless2 on 2015-05-01
Linux ubuntulion 3.13.0-51-generic #84-Ubuntu SMP Wed Apr 15 12:08:34 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by aimless2 on 2015-05-02
bump

---

### Post by kagashe on 2015-05-02
Sorry for the delay.

I think R9 290 Card although launched before Ubuntu 14.04 may not be properly supported on it for open source Radeon driver. There are two solutions

a) upgrade to newer Ubuntu version

or

b) Go for [Kernel/LTSEnablement]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") on Ubuntu 14.04 through following command:
```
sudo apt-get install --install-recommends linux-generic-lts-utopic xserver-xorg-lts-utopic libgl1-mesa-glx-lts-utopic libegl1-mesa-drivers-lts-utopic
```

This will install Kernel 3.16 and better Radeon and Mesa drivers.

Kamalakar

---

### Post by aimless2 on 2015-05-02
Went with option B.  It worked!  Thanks!

---

### Post by kagashe on 2015-05-02
> **aimless2 said:**
> Went with option B.  It worked!  Thanks!
Welcome please mark the thread SOLVED.

Kamalakar

---

