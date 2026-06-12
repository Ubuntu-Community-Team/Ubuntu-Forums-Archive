---
title: "After restart of 10.04, will not boot to desktop"
date: 2013-04-27
forum: General Help
---

### Post by lsutiger on 2013-04-27
I have had this installation working for about a year so far. I did a shutdown then restart and now I am seeing the splash screen then a blank screen with no activity on the hard drive. There were no updates that needed reboot before rebooting. Also, I was not having any issues before the reboot. 
I am able to boot into recovery mode from GRUB, so I am thinking it may be a video driver issue. I have an AMD Radeon HD 6520 and have the driver from the ubuntu repository activated. 
I have done a few searches on google, but am a little confused on what to try next. Any help would be well appreciated.

---

### Post by lsutiger on 2013-04-27
I went back a few kernels until I was able to get to the desktop, which was in low graphics mode (not recovery). I removed the fglrx driver, rebooted and was able to boot into the latest kernel. I reinstalled the driver, rebooted, but still in low graphics mode. When I go to the Hardware drivers it states that no proprietary drivers are in use.
At this point I do not know what to do. I have an extra hard drive and have the windows recovery discs. I guess I could try that in order to see if the driver loads in windows. I would rather not do that.
Any suggestions?

---

### Post by lsutiger on 2013-04-27
update: I went to the AMD/ATI website and downloaded the proprietary driver. We're back in business, but my screen seems a bit darker than usual and the fonts are smaller than what I remember..Whew! I was freaking out there for a while!

PS - Is the "SOLVED" tag for the threads gone? I am logged in but there is now SOLVED option.

---

