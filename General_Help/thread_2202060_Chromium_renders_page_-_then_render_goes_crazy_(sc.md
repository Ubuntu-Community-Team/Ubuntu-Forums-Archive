---
title: "Chromium renders page - then render goes crazy (screenshot attached)"
date: 2014-01-27
forum: General Help
---

### Post by db579 on 2014-01-27
I'm running Ubuntu 13.10 on an Acer V7 using the Haswell integrated graphics and Chromium [COLOR=#303942][FONT=Ubuntu](Version 31.0.1650.63 Ubuntu 13.10 (31.0.1650.63-0ubuntu0.13.10.1~20131204.1)[/FONT][/COLOR]). Up until today everything was working perfectly no whenever I try to load a page it initially seems to render fine - then, once the page has fully loaded, the rendering goes crazy - it goes giant, slanty and generally unusable (for an example there's a screenshot attached).

This seems to affect almost every site I try (notable exceptions are Wikipedia and Amazon for some reason). It also affects chrome based web apps like Google Drive and Maps. Firefox and the rest of my desktop are completely unaffected.

I've tried restarting but beyond that I'm not sure how to solve this. I haven't installed any new extensions in the last couple of days (I have hangouts, translate, and the various drive extensions running but I've now disabled them all) and I haven't updated chromium itself.

I've also tried uninstalling and reinstalling through the software center (deleting the folder in .config and .cache)

---

### Post by db579 on 2014-01-27
I notice in the software center history I have a couple of graphics related updates from a couple of days ago: libgl1-mesa-dri, libglapi-mesa, libgles2-mesa, libgl1-mesa-glx, libopenvg1-mesa, xserver-xorg-video-intel

Is there any way I can rollback this update (or these packages) so I can see if that solves the problem?

---

### Post by db579 on 2014-01-28
Hmm a further software center update of most of those packages applied today seems to have fixed the problem.

---

