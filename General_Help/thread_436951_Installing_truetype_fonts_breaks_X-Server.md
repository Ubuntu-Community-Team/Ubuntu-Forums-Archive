---
title: "Installing truetype fonts breaks X-Server"
date: 2007-05-08
forum: General Help
---

### Post by kellner on 2007-05-08
Hello, 

after installing msttcorefonts and also copying a few customized ttf-fonts into /usr/share/fonts/truetype, and adjusting permissons, the X-server no longer starts - I just get black screens (dual head setup), with nice little circles circling, indicating some activity, but it just never goes any further. 

Xorg.0.log shows no errors, just these messages at the end: 

Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!

Could this be what delays X interminably? 

This is the second time this happens. I first believed it had to do with the graphics card, and reinstalled Ubunto from scratch. I even managed to configure a dual-head merged desktop with the ATI Radeon X1300, and got the correct resolution. The font path errors did not occur after the initial install, nor did they after the second clean install - it all happened after the truetype installation and copying. 

I deinstalled msttcorefonts and reset the font cache with sudo fc-cache -f -v, and I also deleted my customized ttf fonts from the font directory, but X still won't start. 

What's puzzling me is that only the /../cyrillic path is actually found in xorg.conf; the other's aren't. Even when I remove the /../cyrillic path, Xorg.0.log still gets these paths from somewhere. But from where? And could this really be the problem? 

A "grep" indicates that the problematic font paths /usr/X11Rc/... can be found in the binary file "Xorg". 

I'd really appreciate help. I don't want to reinstall Ubuntu again, and again, and again ....

Edit: Actually, the problm may well be gdm. The X-server starts with "startx", but it won't start with "gdm". 

These (apparently non-critical) errors are shown when the server is started with "startx":


(WW) fglrx: No matching Device section for instance (BusID PCI:2:0:1) found
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!

---

