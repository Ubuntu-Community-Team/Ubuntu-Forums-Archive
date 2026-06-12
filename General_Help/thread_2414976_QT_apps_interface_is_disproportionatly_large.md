---
title: "QT apps interface is disproportionatly large"
date: 2019-03-18
forum: General Help
---

### Post by necb on 2019-03-18
I'm noticing a problem with my most recent installation of Xubuntu 18.04.  Any Qt app I install has disproportionally large icons.  This happens with Openshot and Dolphin Emulator, which are the current QT apps I have installed.  The buttons, check boxes, drop down menus, and radio buttons are HUGE.  I don't have this problem with anything but QT apps so far.  Could this be an HiDPI problem?


[[img]https://i.ibb.co/3v5DSs7/Screenshot-2019-03-17-23-05-40.png[/img]](https://ibb.co/3v5DSs7)

---

### Post by mastablasta on 2019-03-18
yes, i believe my KDE install also defaulted to super large icons, which i then reduced. this is the issue with Nvidia drivers.

[https://forum.kde.org/viewtopic.php?f=17&t=140161](https://forum.kde.org/viewtopic.php?f=17&t=140161)
[https://www.reddit.com/r/kde/comments/8ywniu/kde_plasma_everything_is_larger_after/](https://www.reddit.com/r/kde/comments/8ywniu/kde_plasma_everything_is_larger_after/)

you basically need to say to x.org to force the font scale to certain DPI.

btw i don't have a HiDPI, thoguh i do have an HD TV connected (second screen, but treats it as first until boot) and the primary monitor i use is an old SVGA LG (1280x1024).

---

