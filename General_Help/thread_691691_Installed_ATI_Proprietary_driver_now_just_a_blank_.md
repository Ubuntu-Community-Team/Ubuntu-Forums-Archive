---
title: "Installed ATI Proprietary driver now just a blank screen"
date: 2008-02-08
forum: General Help
---

### Post by Sabar on 2008-02-08
I

---

### Post by forrestcupp on 2008-02-09
You need to give a lot more info than that.  For instance, what kind of video card do you have?

If you haven't already gotten back to your desktop, boot to the recovery console by choosing that option in your GRUB menu.  When you get to the command line, type:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```If it gives you a choice, choose vesa drivers.

With the lack of info, I can only guess that you have a card that either is older than what the driver supports or newer.  I can also guess that you used the Restricted Drivers Manager, because it's not an updated driver.  If you have an older ATI card, you should just use the open source Radeon drivers.  If you have one of the new HD cards, they aren't supported in the version in Gutsy's repos.  So if that is the case, I would use [Envy](http://albertomilone.com/nvidia_scripts1.html).  It automatically downloads and installs the latest ATI drivers from their web site.  Those drivers support the newer cards.  But I don't think the HD 3xxx cards are supported at all.

Edit:
If you're really using Ubuntu 5.10, which is a very old version, you may have Kernel incompatibility problems, and I suggest upgrading to a newer version.  But maybe the 5.10 is a mistake.

---

### Post by pointone on 2008-02-09
Duplicate thread.

---

