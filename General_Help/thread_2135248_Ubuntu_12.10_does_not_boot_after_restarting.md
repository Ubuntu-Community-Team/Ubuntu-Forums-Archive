---
title: "Ubuntu 12.10 does not boot after restarting"
date: 2013-04-13
forum: General Help
---

### Post by OnlyZak on 2013-04-13
So after i restarted my computer with ubuntu 12.10 it doesn't boot,it just shows a line on the left side and after that an [OK] in the right.

I'm also a noob so please tell me an easy way to fix this.

---

### Post by OnlyZak on 2013-04-13
Someone please tell me, i can't do anything on my pc

---

### Post by grahammechanical on 2013-04-13
It would be helpful if you gave us some information about your hardware and whether you had another operating system installed. Otherwise, we might give you instructions that are not applicable.

Do you get a boot menu? Is it the Grub boot menu? Do you see an option to boot Ubuntu in Recovery Mode> You may have to look in Advance Options for Ubuntu.

If you boot in Recovery Mode at the first screen select Resume. That will sometimes gewt us to a working desktop. You might also try Recover Mode>Failsafex.

If you can get to a desktop the go to System Settings>Software Sources>Additional Drivers tab and select the open source video driver called Nouveau (Using X.Org X-server - Nouveau display driver from xserver-xorg-video-nouveau. Or you could experiment with some of the other proprietary video drivers listed.

Is this a very new installation of Ubuntu? A simple answer might be to re-install Ubuntu and this time do not tick the box to install third party software. In this way you will get the Nouveau driver from the start. You can install those third party codices after installation by opening the Ubuntu Software Centre and searching from Ubuntu Restricted Extras.

I do testing installs of Ubuntu while it is under development and as a policy I never tick the box to install third party software because it brings in a proprietary video driver. Which was fine about 18 months ago but of late I have experienced many problems with the Nvidia drivers. Today I installed 13.04 twice and I did not have any problems but If I try to use a proprietary Nvidia driver I get a broken desktop.

Regards.

---

### Post by OnlyZak on 2013-04-14
I don't really know much about my hardware  but somehow i got to that purple screen with safex boot thing.

---

### Post by OnlyZak on 2013-04-14
I'll just reinstall the OS

---

