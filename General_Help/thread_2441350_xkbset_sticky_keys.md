---
title: "xkbset sticky keys"
date: 2020-04-22
forum: General Help
---

### Post by frrobert on 2020-04-22
I use I3 and type one handed so I am trying to figure out xkbset sticky keys. The man page shows two options twokey and latchlock.  I am unsure of what the two options do.  Also am I correct - in front of the option turns it off and the option by itself turns it on.

Thanks

---

### Post by norobro on 2020-04-23
I know nothing about this but curiosity got the best of me. > **frrobert said:**
> ... The man page shows two options twokey and latchlock.  I am unsure of what the two options do. The page in the following link is dated 1996 but is included in the latest X11 release. 
TwoKeys info: [https://www.x.org/releases/X11R7.7/doc/libX11/XKB/xkblib.html#StickyKeys_Options](https://www.x.org/releases/X11R7.7/doc/libX11/XKB/xkblib.html#StickyKeys_Options)
Seems latch and lock are differnt keyboard states so I don't know what the combo means: [https://www.x.org/releases/X11R7.7/doc/libX11/XKB/xkblib.html#Keyboard_State_Description](https://www.x.org/releases/X11R7.7/doc/libX11/XKB/xkblib.html#Keyboard_State_Description)

>  Also am I correct - in front of the option turns it off and the option by itself turns it on.Yep, from the help displayed by executing xkbset with no options: > where <options> may be all or any of (the '-' switches the feature off, otherwise it is switched on)
HTH

---

