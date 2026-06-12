---
title: "New Video card. Linux freezes on startup"
date: 2007-12-29
forum: General Help
---

### Post by Fire(storm) on 2007-12-29
Well, the long and short of it. i used to have a 8600GT. Took me forever to find the proper drivers in order to get that working. Now I have the new 8800GT. 
Linux will not boot up whatsoever now. Just freezes after I use my login.

How do I get rid of the old driver or get a working driver in when I can;t even get past login?

---

### Post by perlluver on 2007-12-29
You will probably have to run sudo dpkg-reconfigure xserver-xorg, pick the nv driver, then re run the Restricted Drivers.

Edit: You can do this from X before you login, or press Ctrl>Alt>F2 and that should take you to the x terminal, then just run it from there.

---

### Post by perlluver on 2007-12-29
If the Restricted Drivers do not work, you can also try [Envy]("http://albertomilone.com/nvidia_scripts1.html")

---

