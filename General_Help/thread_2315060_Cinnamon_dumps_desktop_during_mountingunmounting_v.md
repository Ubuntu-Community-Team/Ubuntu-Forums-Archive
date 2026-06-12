---
title: "Cinnamon dumps desktop during mounting/unmounting volumes."
date: 2016-02-25
forum: General Help
---

### Post by Robert_Gaines on 2016-02-25
I am using Cinnamon 2.8.6 on Ubuntu 15.10 64bit. When I mount or unmount a volume, the desktop changes to Ubuntu's default wallpaper, and two layers of icons overlay each other. Sometimes, the panels disappear. I think mounting or unmounting volumes is crashing Cinnamon and it is restarting poorly. I've tried manually restarting Cinnamon through various methods. If I do that, I usually loose the panels completely, and the desktop stays to Ubuntu's default wallpaper. The only good solution is to logout and log back in to a fresh desktop. Is there any solution to this bug? I originally upgraded Cinnamon to the latest version in hopes to be rid of the bug, but it is still there. I've tried not automatically displaying icons to my desktop when volumes are mounted or unmounted. Their is no difference. It still crashes on mounting and dismounting of volumes. Any volumes. Internal hard drives, USB flash or hard drives, and SD cards. It's really annoying.

---

### Post by SuperFreak on 2016-02-25
I have same issue

---

### Post by goofprog on 2016-02-25
I have the same problem too.  I guess it is because the windows managers are overlapping resources from an install.  The window manager may have to be chosen on installation time.  In Fedora, I used to install the window manager with yum install @cinnamon.  I do not know the difference between using the @ symbol in front or without.  Maybe try that. like sudo apt-get install @cinnamon.  I doubt it will help out though.

---

