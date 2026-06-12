---
title: "[SOLVED] Error MSG between GRUB and login screen"
date: 2007-10-18
forum: General Help
---

### Post by AbredPeytr on 2007-10-18
Hi all,

after installing 7.10 (fresh install), I keep seeing the following error messages (very briefly) after the GRUB screen disappears and before the login in screen appears. I haven't noticed any problems. Does anyone know what it means and how I can correct the problem?


Oct 18 19:35:17 kenneth-laptop kernel: [    7.280758] PCI: Cannot allocate resource region 7 of bridge 0000:00:05.0
Oct 18 19:35:17 kenneth-laptop kernel: [    7.280804] PCI: Cannot allocate resource region 8 of bridge 0000:00:05.0

Thanks for you help!

---

### Post by xircius on 2007-10-18
I also get errors regarding region 7,8, and 9 of the PCI bridge... anyone find a workaround or is this a kernel issue that we'll have to wait out?

---

### Post by portach king on 2007-10-19
I'm also getting this error. Boot-up is taking an extrememly long time too with no graphcal indication that its even doing so. Just a blank screen

---

### Post by AbredPeytr on 2007-11-17
Bump

---

### Post by FuturePilot on 2007-11-17
They're really harmless warnings. I wouldn't be too worried about them. My one laptop gives me a similar error. Works great though.
[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/159241]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/159241")

---

### Post by AbredPeytr on 2007-11-17
> **FuturePilot said:**
> They're really harmless warnings. I wouldn't be too worried about them. My one laptop gives me a similar error. Works great though.
[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/159241]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/159241")

Thanks Future Pilot. I haven't noticed any problems using my laptop despite these errors, so I haven't been too concerned. I just wanted to know if it was something to be concerned about.  I'll mark this as solved.

Thanks for your help!

---

