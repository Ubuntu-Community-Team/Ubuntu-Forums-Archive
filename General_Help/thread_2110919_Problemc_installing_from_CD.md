---
title: "Problemc installing from CD"
date: 2013-01-31
forum: General Help
---

### Post by rmcellig on 2013-01-31
I'm not sure where I should have posted this but here is the problem I am having.

When I boot my HP laptop with a Live CD, some distros boot properly but the screen looks awful. It doesn't look normal. Some distros have a safe mode option in the Grub menu but this still causes the screen to look funny. So, it goes without saying that I am unable to install the distro. One of the distros I am trying to install is Watt OS 6. Puppy Linux is fine after booting.

What should I do? Sounds like a driver issue?

---

### Post by grahammechanical on 2013-01-31
I am only familiar with one distribution - Ubuntu. The Ubuntu live session uses the nouveau open source video driver. A proprietary video driver is installed either during the installation to the hard disk (by ticking Install Third Party Software) or after (by using Additional Drivers).

I cannot speak for other distributions but I guess that they also use the open source driver during live sessions.

You can try installing a proprietary driver whilst in the live session but once the session is closed the settings would be lost.

You should still be able to install the distribution.

Regards.

---

### Post by Mark Phelps on 2013-01-31
Do you know the make and model video chipset on the HP?  If not, next time you boot a Linux distro, open a terminal and enter "lspci" and look for the line containing "VGA".  That will provide you the information.

---

