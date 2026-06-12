---
title: "After installing the latest xorg update, both Beryl &amp; Google Earth crash the xserver"
date: 2007-01-11
forum: General Help
---

### Post by tmastran on 2007-01-11
I just installed the latest Edgy updates (xorg-?) and both Beryl (svn) and Google Earth (v4) crash the xserver.

Anyone else having this problem?

---

### Post by Radiera on 2007-01-11
Same problem here. Switched back to Debian Sid :D.

---

### Post by tmastran on 2007-01-11
I re-installed the latest beta nvidia driver and everybody is happy again.

---

### Post by jem7v on 2007-01-12
If you use proprietary video drivers (i.e., official NVidia or ATI ones), any time you have a kernel update you should probably reinstall your video drivers... especially the nvidia ones.  I don't actually know why; I just know that you're supposed to.

---

### Post by jimbo99 on 2007-01-12
> **tmastran said:**
> I re-installed the latest beta nvidia driver and everybody is happy again.

That is the answer for those problems.  The only negative part is having that update dished out to everyone without warning that the nvidia driver reinstall is necessary.   They should not have pushed that update to the client.

---

### Post by Zer0Nin3r on 2007-01-15
> **jimbo99 said:**
> That is the answer for those problems.  The only negative part is having that update dished out to everyone without warning that the nvidia driver reinstall is necessary.   They should not have pushed that update to the client.

I agree.  I spent the better part of the day yesterday tinkering around to get Linux up and running.  I installed all the updates (50+) including the xserver, xorg, etc and it crashed the whole system.  I tried to to install the nvidia drivers again after that fiasco, but the install wouldn't even work, and that would end up halting.  I ended up reinstalling everything (](*,) ) and performed all the updates minus the above said.    Even without the xserver, xorg and such Google Earth is crashing the xserver.

I'll try reinstalling the nvidia drivers (crosses fingers in hopes the whole system won't go corrupt) and we'll see how that goes.  Wish me luck.

**UPDATE**
After clicking and cycling through the equalizer in amaroK, my xserver was reset.  That was the last straw.  I rebooted, reinstalled the nVidia drivers and Google Earth & amaroK is working like a charm now.

---

