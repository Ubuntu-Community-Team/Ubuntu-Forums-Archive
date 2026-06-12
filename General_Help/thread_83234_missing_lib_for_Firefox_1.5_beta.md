---
title: "missing lib for Firefox 1.5 beta ?"
date: 2005-10-28
forum: General Help
---

### Post by jyhelle on 2005-10-28
I followed the Ubuntu  [wiki HOWTO]("http://ubuntuforums.org/showthread.php?t=79283") to replace Firefox 1.07 by the faster 1.5beta version.
Firefox now complains about the missing libgtk-x11-2.0.so.0 ... I tried installing the libgtk2 and -dev packages with adept, but that doesn't seem to be the cure.
Could someone give me some advice before I break something ?

thx, JL

---

### Post by shakin on 2005-10-28
[QUOTE=jyhelle]I followed the Ubuntu  [wiki HOWTO]("http://ubuntuforums.org/showthread.php?t=79283") to replace Firefox 1.07 by the faster 1.5beta version.
Firefox now complains about the missing libgtk-x11-2.0.so.0 ... I tried installing the libgtk2 and -dev packages with adept, but that doesn't seem to be the cure.
Could someone give me some advice before I break something ?

thx, JL[/QUOTE]

x86 or x86-64? Have you searched your drive for that library? I have it in /usr/lib/. I think x86-64 has separate 64-bit and 32-bit lib directories so you may need so symlink to the file from the other lib dir.

---

### Post by jyhelle on 2005-10-28
in fact, I found .so and .so.0.800.6, the first one beeing a link to the second, so I added another link with the .so.0 name... 
Firefox still reports the same error, but since I am becoming used to Konqueror I think I'll wait for an official release of the 1.5 version ;) 

JL

---

### Post by shakin on 2005-10-28
[QUOTE=jyhelle]in fact, I found .so and .so.0.800.6, the first one beeing a link to the second, so I added another link with the .so.0 name... 
Firefox still reports the same error, but since I am becoming used to Konqueror I think I'll wait for an official release of the 1.5 version ;) 

JL[/QUOTE]

I've made the switch to Konqueror as well, ever since I started using Krusader as my file manager.

You might want to try the Firefox installer. I got it working that way. I just installed it in /opt/firefox so it wouldn't interfere with the existing version.

---

