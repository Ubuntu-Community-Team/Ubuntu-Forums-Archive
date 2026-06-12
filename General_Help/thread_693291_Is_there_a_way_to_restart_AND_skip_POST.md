---
title: "Is there a way to restart AND skip POST?"
date: 2008-02-10
forum: General Help
---

### Post by diablo75 on 2008-02-10
I was just curious if there's a way to restart Ubuntu without doing a full restart.  Just for the hell of it  :lolflag:

---

### Post by nemilar on 2008-02-10
Not entirely sure what you're asking here.

POST is only one part of booting up...a very small fraction of it, actually.  You POST before GRUB even launches.

---

### Post by MighMoS on 2008-02-11
It depends on what you want to restart. If you don't feel bad for dropping down to the terminal, you can type ```
telinit 1
``` This will drop you down to runlevel 1, where only one user (root) is logged in and ALL services are stopped. Typing ```
telinit 2
``` will restart them all.

Note that by no services running that includes X (or everything graphical).

Note 2: This won't reload the kernel, so if you're trying to avoid a full restart after updating your kernel, this isn't good enough. Only a full restart can avoid that.

---

### Post by HappyFeet on 2008-02-11
no, the POST (power on self test) is necessary to detect available drives, ram, etc.

the closest thing to a restart without powering down would be ctrl-alt-backspace. which will restart x.

---

### Post by diablo75 on 2008-02-11
Well, what I was interested in doing is changing something so that when you go to restart the computer, it shuts down the OS as normal, but when it goes to restart, it bypasses post and goes strait to GRUB, cutting restart time by about 10 seconds or so.

---

### Post by MighMoS on 2008-02-11
I've never heard of a way to do what you describe -- basically grub is loaded by the BIOS when it executes the first 512KB of your hard drive.

---

### Post by diablo75 on 2008-02-11
Well you can do it with windows:

[http://dailyapps.net/2007/08/restart-windows-without-restarting-bios/](http://dailyapps.net/2007/08/restart-windows-without-restarting-bios/)

---

