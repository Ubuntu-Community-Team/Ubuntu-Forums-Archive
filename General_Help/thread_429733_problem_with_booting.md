---
title: "problem with booting"
date: 2007-05-01
forum: General Help
---

### Post by japc126 on 2007-05-01
When I choose to boot ubuntu, it gets stuck in the loading screen. By loading screen I mean white letters in a black background that say 'loading'... any help?

---

### Post by ago on 2007-05-01
That's a regression due to some code changes upstream. It has been fixed but will only be available in next release.

For the time being all you have to do is wait 4-5min and the installation will continue.

---

### Post by japc126 on 2007-05-01
The program got stuck in a blue screen for about 20 minutes... What now?

---

### Post by ago on 2007-05-01
> **japc126 said:**
> The program got stuck in a blue screen for about 20 minutes... What now?

What hard disk do you have? 
Some sata disks are not well supported and disk i/o becomes much slower. If you give me detailed info on your hd I might be able to find the required driver and add it to next version.

---

### Post by japc126 on 2007-05-01
I think that my disk is supported because I had been able to install this before...

---

### Post by ago on 2007-05-01
If you hit Alt+F4 in the blue screen you can see where you got stacked. If you need to look at older logs, press Alt+F2 and execute: nano /var/log/syslog

---

