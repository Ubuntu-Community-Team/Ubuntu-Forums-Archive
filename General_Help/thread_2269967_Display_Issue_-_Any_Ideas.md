---
title: "Display Issue - Any Ideas"
date: 2015-03-19
forum: General Help
---

### Post by trivialpackets on 2015-03-19
I have a single laptop, that whenever I run any verison of Ubuntu on it newer than 14.04, has screen distortion issues.  I am not sure of the issue.  I also see the same issues, although even more pronounced when running Windows, but they are the same issues.  I have attached a screenshot of it, that admittedly is taken in Windows, however it's the best image I have showing the issue which also plagues ubuntu.  What would cause this?  Any thoughts?

[ATTACH=CONFIG]260729[/ATTACH]

---

### Post by dino99 on 2015-03-19
windows & ubuntu have the same issue ? very strange.
at first glance it seems to be either a font issue/borked profile/graphic driver trouble
but as they are both affected the only reason i can think about is the hardware: ram ? overheat ? custom tuning (voltage,speed) ?

---

### Post by trivialpackets on 2015-03-19
That's the thing that is so elusive about this.  It has to be hardware, I've just not run into it before.  Ubuntu has the issue only if it's newer than 14.04.  Also, just about any other current distribution has the issue occur.  I'm okay with leaving it at 14.04 for quite some time, as I just wiped the thing out and stuck just Ubuntu 14.04 on it and will keep backups of my data, but I was curious if anyone had ever seen the issue before.

---

### Post by dino99 on 2015-03-19
have you some abnormal temperatures (psensor) or noisy fans (or not working at all); do you get some usefull errors/warnings logged ?
what says the graphic settings ? hardware temps ?

and last question: is that laptop used at home or in 'extreme' environment ? (you know, electronic better like dry air and not extreme temp)
maybe open the box to remove dust

---

### Post by buzzingrobot on 2015-03-19
Since it's happening on Ubuntu and Windows, it must be something in common. 

They have the hardware in common, of course.  They also have the same video card in common, and the same BIOS.

What video card is in use? If you laptop has both onboard Intel video and a discrete Nvidia/AMD card, and if the BIOS allows one to be disabled and the other enabled, does the problem remain after you make the switch?

If you using an Nvidia or AMD card and a proprietary driver on Ubuntu  (as you will on Windows), try removing it (use Additional Drivers if that's how you installed it) and select the open source driver. If the problem goes away on rebooting Ubuntu, but remains in Windows,  then that points at a problem common to both the proprietary driver in Ubuntu and its cousin in Windows.  (You can also boot a 14.04 install image and run it in live mode to make this check, since it will use an open source driver.)

Is a BIOS update available for your machine?  Check the manufacturer's support site.

If it's connected with overheating, you might not see the distortion immediately after booting on a cold machine.

---

