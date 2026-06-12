---
title: "After kernel upgrade, X won't start on SLI motherboard"
date: 2007-02-11
forum: General Help
---

### Post by NutMonkey on 2007-02-11
After the latest kernel upgrade, X won't start for me.  I have an SLI motherboard with two cards, but only one monitor.  I want to use the SLI when I boot into windows, but on the linux side I just want it to ignore the second card.  I previously had a "Device" section in xorg.conf for the card on PCI:3:0:0 and nothing for the other card, and that worked fine.  After the latest kernel upgrade and reboot, when I try to start X it says "No Device section found for BusId PCI:6:0:0" or something like that.  So I tried to add a Device section for both cards, with a different identifier for the second card, but I still get that error.  If I change the one section to PCI:6:0:0 I get an error about missing a device section for PCI:3:0:0.  So what is the proper way to tell X that yes I have two cards, but just use the one and ignore the other?

---

### Post by g8m on 2007-02-11
Don't know anything about your hardware. But just in case. If you have custom drivers installed for your videocard, you must reinstall them after a kernel upgrade.

---

### Post by NutMonkey on 2007-02-11
Thanks, but I've tried reinstalling, that does not seem to be the problem based on the errors reported.

---

### Post by cmost on 2007-02-11
...what errors?  Please post output.  Thanks.

---

### Post by NutMonkey on 2007-02-11
The errors listed in the original post, "No Device section found for BusId PCI:6:0:0".  To summarize, I have two video cards but I only want to use one.  Until the recent kernel upgrade I had a Device section in my xorg.conf for the one video card only and it was fine, but now it's complaining because it's finding the second video card and doesn't have a Device section describing it (because I want it to ignore that one).  I tried to add a second Device section but that didn't work.

---

### Post by TheWizzard on 2007-02-11
you can also boot your old kernel. hit escape to enter the grub menu.
if you're planning to go to feisty, i wouldn't put too much effort in this newer kernel.

---

