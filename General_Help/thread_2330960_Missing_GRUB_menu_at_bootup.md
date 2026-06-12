---
title: "Missing GRUB menu at bootup?"
date: 2016-07-16
forum: General Help
---

### Post by anthonywc on 2016-07-16
For work I got a Oryx Pro /w 14.04 which I have quite happy with.  I was messing around with the lightdm setting and ran into this issue ([https://ubuntuforums.org/showthread.php?t=1968492](https://ubuntuforums.org/showthread.php?t=1968492)) and unfortunately it looks like the grub menu wasn't properly installed and I am struck with grub prompt.

Not sure how/why they would install it /w a missing GRUB menu because it really impact my ability to fix broken configuration by not giving me the ability to get a proper shell.

---

### Post by oldfred on 2016-07-16
Boot Ubuntu installer in live mode and add Boot-Repair:

May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by grahammechanical on 2016-07-16
If Ubuntu is the only OS then we will not see a Grub boot menu. It is hidden. If we press Shift as the motherboard works through its Power On Startup Tests (POST) then the Grub boot menu should appear.

The Grub rescue prompt is an indication that Grub cannot find either its menu configuration file or a Linux kernel to load.

> 
[LIST]
[*]If no other operating system is detected GRUB 2 will boot straight  into the default operating system and no menu will be displayed. 
[/LIST]


[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Regards.

---

### Post by anthonywc on 2016-07-19
Actually I should've mentioned I already tried Boot Ubuntu installer and Boot-Repair; neither work.  Ditto for shift because grub menu config file is not there (I think one of the grub repair tool showed it).  Going to open a support ticket & see; otherwise I will install Ubuntu (properly) myself.

---

