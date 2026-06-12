---
title: "How to swap Caps Lock and Enter keys?"
date: 2015-06-01
forum: General Help
---

### Post by Alabaster_Jones on 2015-06-01
xmodmap is no longer supported and xkb doesn't seem to have this as an option.

Thank you

---

### Post by aeden.d on 2015-07-16
I don't understand how xmodmap is not supported? 

x11-xserver-utils is available by default after your Ubuntu install and it includes:
iceauth
sessreg
showrgb
xcmsdb
xgamma
xhost
xkeystone
**xmodmap**
xrandr
xrdb
xrefresh
xset
xsetmode
xsetpointer
xsetroot
xstdcmap
xvidtune

As of today the current stable version is: x11-xserver-utils 7.7+2ubuntu1 and Canonical provides critical updates for X server utilities until May 2019.

Maybe I'm missing something?

---

