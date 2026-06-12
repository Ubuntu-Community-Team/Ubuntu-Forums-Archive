---
title: "[SOLVED] Kubuntu live CD: &amp;quot;Microcode &amp;quot;bcm43xx_microcode5.fw&amp;quot; not available or load fa"
date: 2008-01-17
forum: General Help
---

### Post by TeeAhr1 on 2008-01-17
Hey all, about to install Kubuntu on a new HP laptop, and the live CD bails with:

bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

I understand from some searching I've done that this is an issue with the wireless card firmware, but why should that punt me back to the prompt?  Just when KDM is about to start, it boots me back to tty1.  Any workarounds for this?  Thx, all...

-pd-

---

### Post by TeeAhr1 on 2008-01-18
SOLVED it myself (with a lot of help from this [thread]("http://ubuntuforums.org/showthread.php?t=575750&highlight=Pavilion+dv9628nr") here).  Basically, it was two seperate issues.  The wireless driver, or lack thereof, was giving me the error stated in the title.  The firmware is installed by default, but not the driver, for some reason, so it keeps looking for a nonexistent file.  But what was kicking me back to the prompt was the nv driver fracking up the works.  I went into /etc/X11/xorg.conf and changed the driver to vesa, got into KDE, and downloaded the nvidia driver from the repositories.  All was well.  For much more information of the configuration of these laptops, see the thread I linked.

---

