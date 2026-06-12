---
title: "Controlling Fan Speed, Vsync etc. using non-proprietary driver"
date: 2013-06-19
forum: General Help
---

### Post by Alex Carroll on 2013-06-19
I have a HD5870 and am using the open source (non-proprietary) driver with it. Xsensors tells me its idling at 70c and Counter-Strike refuses to run above 60fps, so I've been looking to fix either of those. Google is getting confused because the non-proprietary driver doesnt have a nice codename like fglrx does.

Is anyone aware of a way to do either of these things? Or even a good short name to call the non-proprietary driver.

Thanks.

---

### Post by QIII on 2013-06-19
Hello!

The non-proprietary driver, used by default when you install Ubuntu, is called the Radeon driver.

There are some things you can do to adjust the performance of your card, but controlling the fan speed in any way other than the hardware control already built in is ***not *** something I would recommend.

Is your card a reference model?  Have you installed the proprietary fglrx driver?  Have you installed the little bit of hardware acceleration available (see the wiki in my signature)?  Have you used the Catalyst Control Center to adjust performance.

ATI Overdrive is available for Linux, but it is a command-line-only affair.  But if you have a reference model you can adjust the clock speeds, etc.

---

