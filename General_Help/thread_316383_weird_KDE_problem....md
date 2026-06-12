---
title: "weird KDE problem..."
date: 2006-12-10
forum: General Help
---

### Post by sunami88 on 2006-12-10
Hey all, im having some trouble with my Ubuntu 6.06. I was fooling around in Gnome, and decided to try out KDE. So i did "apt-get" KDE, and everything was fine for a while. Then, one day in Konqueror, wanted to change the size of the icons so i went to View->Icon Size, and then picked "smaller" or whatever, and Konqueror froze. I had to do a hard reboot, and still, if i open a Konqueror window, Ubuntu freezes up.

what the heck?

Iv tried deleting my .kde and .konqueror folders in /home, iv tried reinstalling KDE, and a few other things, but it still keeps freezing on me. Anybody else got any ideas aside from "upgrade to Ubuntu 6.10"?

P.S.
    When i use Gnome, everything is fine until i try and open a KDE program. i.e. a program that i installed when using KDE. I dont have any idea if this means anything, or if its even possible haha, but it happens...

---

### Post by ardvark71 on 2006-12-10
Hi...

This sounds similar to the problem I had when I installed KDE, however I was getting other weird anomolies rather than lockups. 

I unexpectantly solved the problem by reinstalling "kubuntu-desktop" over "KDE" in apt get. I wonder if that will work for you?

Best Regards...

:KS

---

### Post by igknighted on 2006-12-10
For future reference, whenever you install a DE like KDE or Xfce, you should always use aptitude and never apt-get.  It makes it easier to deal with issues like this because you can do a clean uninstall and reinstall.  At this point I would try using aptitude to install kubuntu-desktop and seeing if that helps you out at all.

---

### Post by ardvark71 on 2006-12-10
> **igknighted said:**
> For future reference, whenever you install a DE like KDE or Xfce, you should always use aptitude and never apt-get.  It makes it easier to deal with issues like this because you can do a clean uninstall and reinstall.  At this point I would try using aptitude to install kubuntu-desktop and seeing if that helps you out at all.

Ah yes, "aptitude", thanks for the correction 8) 

:KS

---

### Post by sunami88 on 2006-12-10
> **ardvark71 said:**
> Hi...

This sounds similar to the problem I had when I installed KDE, however I was getting other weird anomolies rather than lockups. 

I unexpectantly solved the problem by reinstalling "kubuntu-desktop" over "KDE" in apt get. I wonder if that will work for you?

Best Regards...

:KS

cool, "kubuntu-desktop", eh? il give it a try.

UPDATE: seems to work now :D. Thanks.

---

