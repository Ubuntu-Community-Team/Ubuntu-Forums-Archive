---
title: "Xubuntu Splash Screen missing"
date: 2012-10-25
forum: General Help
---

### Post by ushills on 2012-10-25
Following my recent upgrade from 12.04 to 12.10 the splash screen on bootup does not display, in fact the screen sleeps.

Shutdown screen is fine.

What do I need to change to get a splash screen again, boot is set to splash and quiet.

---

### Post by diegomanule on 2012-10-27
I am stuck on the same, I'm running xubuntu 12.10 in a nokia booklet 3g and edited grub options to get the bright up/down buttons working after that no startup splash screen.

the strange thing is that shuting down splash screen its ok.

---

### Post by pqwoerituytrueiwoq on 2012-10-27
what gpu driver?
this might work for you
[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)
just use [FONT=Courier New]sudo hwinfo --framebuffer | grep "24 bits"[/FONT] to get a valid resolution

---

