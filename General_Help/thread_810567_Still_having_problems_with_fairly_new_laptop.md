---
title: "Still having problems with fairly new laptop"
date: 2008-05-28
forum: General Help
---

### Post by KrGAce on 2008-05-28
Hello all,

This laptop I am currently using is a Dell Latitude D830 and the video card within it is an NVIDIA Quadra NVS 130-140.  In Gutsy Desktop effects worked great with all the eye candy, however since I have upgraded to Hardy, I cannot get it to work, I get "cannot enable desktop effects".  I have used Envy to get the latest NVIDIA driver, but on reboot when it's installed my screen goes black and I have to use recovery mode to get my system back.

Is there a way to get this to work? Is this a work in progress as far as Ubuntu, or drivers are concerned?  Is there something else I should try?  I am grateful that I do have a working system that I love, however most everyone does enjoy the "extras" in relation to the eye candy.  In fact, I love showing it off!

Any help, or steps or direction is greatly appreciated ahead of time.


AceMan

---

### Post by Kevbert on 2008-05-28
Use the default display driver.  Try running compiz-check, it will advise you what you need to do.  It can be found here: [http://forlong.blogage.de/article/pages/Compiz-Check]("http://forlong.blogage.de/article/pages/Compiz-Check")

---

### Post by KrGAce on 2008-05-28
> **Kevbert said:**
> Use the default display driver.  Try running compiz-check, it will advise you what you need to do.  It can be found here: [http://forlong.blogage.de/article/pages/Compiz-Check]("http://forlong.blogage.de/article/pages/Compiz-Check")


Okay I did that, but don't know what to do with the output...here it is!

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation Quadro NVS 140M (rev a1)
 Driver in use:         nv
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

Thanks for the help thus far.

AceMan

---

### Post by Kevbert on 2008-05-28
It looks like the problem is your display driver.  I'm not sure of what to suggest but you could post the problem on the Compiz-fusion forum [http://forum.compiz-fusion.org/]("http://forum.compiz-fusion.org/")
where you may have better luck. It may be worth you posting the output of
```
glxinfo
```
in terrminal, on the forum.

---

### Post by Forlong on 2008-05-28
Your nvidia driver is not properly installed.

Post the output of ```
grep -v ^# /etc/X11/xorg.conf
``` and use the forum's [noparse][CODE][/noparse] tag please (# button)

---

