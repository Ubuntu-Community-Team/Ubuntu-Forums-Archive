---
title: "Install software to ISO for Live CD usage"
date: 2006-12-24
forum: General Help
---

### Post by chocolatetoothpaste on 2006-12-24
Hey all,
  I was wondering if anyone could help me out in installing a couple applications to the edubuntu ISO, so they were available to use in Live CD mode.  Any help you could give, thanks.
  To be a bit more specific, I want to install Bubbles, and a couple other games to the ISO, so my buddy can let his little kids play some games without installing the OS, he just wants to run the live cd.

---

### Post by towsonu2003 on 2006-12-24
I think customizing the CD is too much of an effort for what you want. See [https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization) and [https://help.ubuntu.com/community/InstallCDCustomization/Scripts](https://help.ubuntu.com/community/InstallCDCustomization/Scripts)

but I would:
0. buy a usb flash drive
1. boot the LiveCD
2. ```
sudo apt-get install whateverpackagesyouwant
```
3. plug in the flash drive - it should launch nautilus with the contents of the flash drive
4. copy the contents (all) of /var/cache/apt/archive to the flash drive

now everytime your friend boots the liveCD, s/he has to put the contents of the flash drive back to /var/cache/apt/archive and issue ```
sudo apt-get install whateverpackagesyouwant
``` and the LiveCD will install the packages from its cache without net connection or anything. 

I like this way. 

If the kid will use the live cd, check around for ways to lock down gnome administrative menus! as the liveCD won't ask for passwords, the kid might decide to format your hard disk etc...

---

