---
title: "fsck issue that disappears when gdm is installed"
date: 2016-01-23
forum: General Help
---

### Post by lilandra on 2016-01-23
Hi,

I recently installed xubuntu 15.10 (single boot) on an asus (x555) laptop.
I can afford to lose anything on this machine and would probably have reinstalled already except that I think my live cd is...not with me.

I decided to try gnome and installed ubuntu-gnome-desktop.
I wasn't happy with it so I tried un-installing it. Of course all the packages that the meta-package caused to be installed weren't marked auto so I uninstalled a few of the packages that were brought in.

I rebooted it a few times while trying to access recovery mode (never successful in figuring out when to press shift, maybe I am reading the wrong instructions) and
- once I got the error message: *ERROR* The master control interrupt lied (SDE)! after trying to run fsck on /dev/sda2
- it hung on fsck of /dev/sda2. I waited a good few hours and it didn't complete
- after doing ctrl+c on fsck, it started loading the xubuntu screen but eventually shut down my computer

I tried to reverse my steps but instead of installing the whole ubuntu-gnome-desktop again, I just installed gdm and let lightdm be the default. When I rebooted, it went into xubuntu without showing any fsck. No problems.

And then again, I went through the Ubuntu Software Centre and uninstalled every single package that was installed at the time I installed ubuntu-gnome-desktop, just so I can get rid of them all. I did it all at once (and apt-get autoremove) and rebooted and now it is stuck on fsck so...I repeated what I did last time (reinstalled gdm and now yay).

I'm not sure what I broke and how to get rid of gdm without breaking it again.

I googled how to uninstall the whole meta package but those options didn't work (remove, autoremove).
I read that I should wait for the fsck to complete. Well is four hours enough? Maybe not. But if it completed when gdm was installed that doesn't make sense? (that it didn't have enough time).
I tried booting into recovery mode but I wasn't able.

I figured I must have uninstalled a package I shouldn't have (duh). How do I figure out what package? A disk utility maybe? Ooo maybe a disk utility that gdm/gnome tells it to run but when I uninstalled everything, it is still being told but the package isn't there?
Thanks for any help.

Edited to add: Well, I figured out how to get into recovery mode. Esc not Shift.

---

### Post by lilandra on 2016-01-23
Oh well, I think I fixed it. Not really sure.
I installed ubuntu-gnome-desktop again and debfoster (forgot how much I used to love debfoster, forgot it existed).
Used debfoster to get the proper list of packages to uninstall. 
Uninstalled. Rebooted. Got same fsck hang.
Remembered when I was searching for help, somebody said delete Xorg.conf (which of course I couldn't find), so I reconfigured xserver-xorg and xinit (guessed/hoped it would work) and it rebooted ok (for now)

---

