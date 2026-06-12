---
title: "Two xorg.conf files, one for Bigdesktop and one for xgl/beryl"
date: 2007-03-14
forum: General Help
---

### Post by atariman on 2007-03-14
Hi all,

Is it possible to have two (2) xorg.conf files, one for running BigDesktop and one for running xgl/beryl? When I tried to enable the BigDesktop code in my xorg.conf file, xgl/beryl didn't play nice with it and X crashed (or rather, X failed to load). I've read that the two don't play nice together, but ultimately I want to run a normal Gnome session at home with BigDesktop so that I can take advantage of my external widescreen LCD and run a xgl/beryl session while I'm on the road (needless to say that I have a laptop). I have both running fine independently, but when I try to run both at the same time, that's when problems occur. Any help would be greatly appreciated.

Kev

---

### Post by bruenig on 2007-03-14
Assuming that all that has to be done to switch between the two is modify the xorg.conf then it seems perfectly plausible that you could just have two xorg.conf and switch them out at need.

---

### Post by atariman on 2007-03-14
Thanks for the reply.

What I would like to do is this. At the login screen (the graphical login screen), when I change sessions, I would like to load one xorg.conf file optimized for BigDesktop when I select Gnome, and when I select xgl, to load the other xorg.conf file. Is this possible, and if so, how would I do that? I am not that new to Linux, but I'm also not a guru (yet).

Thanks in advance.

Kev

---

