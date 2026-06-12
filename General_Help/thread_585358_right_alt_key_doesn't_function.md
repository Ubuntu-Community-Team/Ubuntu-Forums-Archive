---
title: "right alt key doesn't function"
date: 2007-10-21
forum: General Help
---

### Post by jetpeach on 2007-10-21
EDIT: yeah, i fixed it. not exactly sure what i did, although the now working configuration of xorg.conf just has "#   Option          "XkbOptions"    "lv3:ralt_switch" " to comment it out. I think there was another change I made in the system settings that also made the difference.


I just upgraded to Gutsy and lost the function of my right ALT key. The left works fine, but now the left one appears to do nothing at all.
Below is the relevant part of my xorg.conf file, the way it was configured by default. I tried  commenting out the lv3:ralt_switch option and rebooting, but this didn't fix the problem. 

Does anybody else have this problem after upgrade to gutsy? Know a solution? My keyboard is the most generic standard keyboard ever, no special keys or anything just a nice simple keyboad with the standard layout.

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection


If I'm not alone in this bug, I'll file a bug with launchpad, but if it's just me then maybe its too specific to my configuration to waste developers time with a bug...

Thanks for any help,
jet

---

