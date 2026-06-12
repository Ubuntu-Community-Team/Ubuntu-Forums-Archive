---
title: "Ubuntu 17.10 - desktop Nautilus drag and drop bugs"
date: 2017-10-28
forum: General Help
---

### Post by ioewqnf on 2017-10-28
Getting two different bugs on Ubuntu 17.10 with dragging and dropping files, and they're both between nautilus and nautilus-desktop program interactions.

1. When dragging a file from the desktop (nautilus-desktop) over onto a nautilus window, nautilus-desktop becomes unresponsive and must be restarted (or logging out and back in).  Dragging and dropping files around within the desktop works fine, and within nautilus windows works fine as well.

2. When dragging a file from a nautilus window onto the desktop, it doesn't freeze either of them up, but it does make a copy of the file instead of moving the file, even though both files are on the same filesystem.  When dragging and dropping files within a nautilus window, or within the desktop, files are moved as expected and not copied.

Posted to [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1727057](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1727057) in case that is the same bug, but also wanted to report it here too for awareness.

Also of note: The issue doesn't happen when booting into a live USB environment for 17.10.  The issue remains even after a fresh installation.  This is on a laptop with a touch pad and touch screen, too, if that makes a difference.

EDIT 1: If you log into a Xorg session, this bug is gone.  The bug is only in Wayland logins.  Perhaps Xorg is the default when booting into the USB live environment and that's why I didn't see it there.

---

### Post by Frogs Hair on 2017-10-28
Hello and Welcome 

I experienced some unusual drag and drop behavior during the 17.10 testing phase and this can affect productivity. I would select the Ubuntu on Xorg session when you login and see if drag & drop works better. In my case the folders were getting stuck on the desktop and I would login to the Xorg session where moving the files/documents  worked as expected.

---

### Post by ioewqnf on 2017-10-29
> **Frogs Hair said:**
> Hello and Welcome 

I experienced some unusual drag and drop behavior during the 17.10 testing phase and this can affect productivity. I would select the Ubuntu on Xorg session when you login and see if drag & drop works better. In my case the folders were getting stuck on the desktop and I would login to the Xorg session where moving the files/documents  worked as expected.

Confirmed!  Xorg works fine, the bug is on the Wayland side.  Perhaps Xorg is the default when booting into the USB live environment and that's why I didn't see it there.

Thanks!

---

### Post by autarchex on 2017-11-03
I am seeing same thing on a desktop with mouse... and Wayland.  It is mildly infuriating.

---

### Post by gr-theus on 2017-11-05
I can confirm this bug on my system, too. Nautilus is hanging, with a strange side effect: space key is not working anymore. (Ubuntu 17.10 with "apt full-upgrade")

---

### Post by gr-theus on 2017-11-05
Another strange behaviour with nautilus desktop and dragging icons: I cannot drag an icon on the desktop straight from one side to the other, if the icon has to be moved across an open window on the desktop. The icon is moving back to its origin if I do that. I have to "surround" the open windows if I want to stay the icon on the target place. On Xorg desktop no problem.

---

### Post by alelephant on 2017-11-23
I'm experiencing the same exact problem with both drag and drop (the cursor freezes on the "closed hand" image) and the space bar that stops working.

Anybody came up with a solution for that?

---

### Post by Frogs Hair on 2017-11-23
There are bug reports on the problem and one reason both Wayland and Xorg sessions were included on 17.10. Xorg could be default on 18.04 if some of the bugs aren't fixed.

---

### Post by alelephant on 2017-11-24
I'll just skip to Xorg then. Nothing dramatic. I hope they will fix this on 18.04 though.

---

### Post by Frogs Hair on 2017-11-24
> **alelephant said:**
> I'll just skip to Xorg then. Nothing dramatic. I hope they will fix this on 18.04 though. Other Linux distributions using Wayland are also affected.

---

### Post by quakestring on 2017-12-01
I'm experiencing same more problem,
1. Drag and drop not working in nautilus or desktop, 
2. Select items on nautilus does not work as it should work.
3. Cant select items using shift and arrow key.
4. when write click on any folder or file on nautilus its scroll to top row.
5. after working few hours, if I try to restart or shut-down, the shut-down dialog box take very very long time and while that time desktop goes completely unresponsive. 

and all of this happening in Wayland as well as on xorg. (ubuntu 17.10 is fresh installation)
this problem not happened with I was using 17.10 upgraded from 17.10.

---

### Post by veredas on 2017-12-29
Hello,

I've the same problem here. When i'm going to move an item, it starts selecting all items around. Does anyone know how to solve it?

---

### Post by Frogs Hair on 2017-12-29
Bugs have been filed  , I would suggest using the Ubuntu on Xorg session option during login. 

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1704765](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1704765)

---

