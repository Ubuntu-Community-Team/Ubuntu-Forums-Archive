---
title: "Question on new Edgy updates"
date: 2007-02-08
forum: General Help
---

### Post by darweth on 2007-02-08
Some new updates just popped up in the notifier.

linux-headers-generic, linux-image-generic, linux-restricted-modules-common

descriptions are like: Generic Linux kernel headers from version 2.6.1710 to 2.617.11, etc.


What will the ramifications of installing this be?  Is it just security updates?  Will I need to reinstall proprietary nvidia drivers?

I only ask because I remember when I follow a HOWTO for Beryl, it said that steps to install drivers and blah blah would need to be repeated in case of a kernal change.  Does that have nothing to do with this update?

Thanks!

---

### Post by darweth on 2007-02-08
I was told in IRC that that actually IS the kernal.  

The funny thing is linux-restricted-modules-common is the only one I was able to install.  The other two were greyed out and the update notification no longer pops up after a restart.

I tried to reinstall the nvidia drivers for the hell of it after upgrading restricted-modules-common, but it seems like there is no need.  Beryl and all work fine for the moment.

---

### Post by dr_d on 2007-02-08
If they were grayed out in the update notifier then they're probably getting 'held back' by synaptic/apt-get/aptitude.

There are quite a few of us getting this problem... No actual functionality loss as far as I know. I guess it's up to you if you care about this enough to try to get it fixed.

Anyway here's a link to the main thread:
[http://ubuntuforums.org/showthread.php?p=2123214#post2123214](http://ubuntuforums.org/showthread.php?p=2123214#post2123214)

---

### Post by chumpjaw on 2007-02-08
I also see the three updates grayed out for the 2.6.17-11 kernel...even after a reboot!

I'm pretty new to Linux (especially Ubuntu), but have not ever seen this!  Any help/hints are greatly appreciated!!!

Later,
chumpJAW

---

### Post by banditti on 2007-02-08
My .02, I have the same issue with the ATI drivers.

---

### Post by tjk on 2007-02-09
In the Adept Updater you can right click and force an install (haven't actually tried) -- but before I install, I too would like to hear what the reason is for these files not upgrading automatically.

---

