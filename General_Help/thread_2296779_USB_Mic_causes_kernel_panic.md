---
title: "USB Mic causes kernel panic"
date: 2015-09-28
forum: General Help
---

### Post by leepe on 2015-09-28
I have a Samson GoMic Direct that I am trying to use with my ubuntu installation. The mic is known good and works on other linux PC's, but fails when I plug it into my ODROID C1+. I need to get it working on this platform. I suspect it is a kernel module or other driver that is different on the ARM than the x86 platform, as the mic works with an x86 installation of the same version of ubuntu (and the same kernel). Does anybody know of a solution to my problem, or of another sound driver I can try?
I've tried OSS but it doesnt compile, as the package is CPU-dependent and doesn't come in an ARM-cpu variant.
Thanks!

---

### Post by tgalati4 on 2015-09-28
Perhaps it is taking too much power from the USB causing a voltage drop and lockup.  Most ARM devices don't like 4.8 VDC.  Look at /var/log/syslog and see if there are any USB/power entries.

Try using a powered USB hub.

---

