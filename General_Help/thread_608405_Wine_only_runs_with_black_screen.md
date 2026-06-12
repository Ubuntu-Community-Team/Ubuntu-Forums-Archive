---
title: "Wine only runs with black screen"
date: 2007-11-10
forum: General Help
---

### Post by jmetal88 on 2007-11-10
I have no idea what's going on here, and I've done about an hour and a half of searching. Whenever I run a program using wine, the screen goes black. The program is running however, as I can exit it blindly, and, in the case of games, I can hear the sound. Winecfg produces the same kind of output. This behavior started after my motherboard swap, and I am now using Intel integrated graphics, which I believe is the issue, but I'd like to know if anyone has any suggestions other than putting my Nvidia card back in the machine (there really isn't enough room for it due to the rather large heat sink).

---

### Post by hikaricore on 2007-11-10
To be honest people have about 50/50% luck with Intel cards.

You seem to fall into the category of those without luck.
Nvidia really is the way to go currently when it comes to these sorts of issues.

Besides, you could always remove the heatsync and put a fan on the damned thing.  ^_^

---

### Post by jmetal88 on 2007-11-10
Alright, alright. :rolleyes:

I just jammed the Nvidia card back in there and Wine is once again working as it should. I hope somebody, sometime figures out what the intel issue is, though.

---

### Post by hikaricore on 2007-11-10
We already know what the intel issue is..

Crap drivers that Intel created, and sub-standard hardware integrated chipsets that should never have been thought up.

---

### Post by oudalrich on 2007-11-17
This will not solve your problem, but maybe point you in the right direction: I had a similar, but less severe problem, also with an Intel integrated graphics machine. It's a laptop that I usually use with an external monitor attached. The screen would go black one or several times when starting a Wine application, however it would always come back. The solution was to turn off the laptop's internal display by typing
```
xrandr --output LVDS --off
```
in a terminal. No more blackness. So maybe the Intel graphics chip in your system thinks there are two outputs, in which case you could use xrandr to turn off the one you're not using.

---

