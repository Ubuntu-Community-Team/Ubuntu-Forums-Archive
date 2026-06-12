---
title: "keyboard problems"
date: 2007-05-23
forum: General Help
---

### Post by penguinattacks on 2007-05-23
Im having trouble configuring my keyboard to the german layout. It was working before I upgraded the nvidia drivers (which Im still not sure if its working because I am trying to get beryl to work and it wont, along with some games such as tremulous)

when I change the keyboard layout over in System - Preferences - Keyboard it gives me this error
> Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70200000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd




here are the results

> _XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "de", "de", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "de", "de", ""

>  layouts = [de  de,us]
 model = 
 options = [grp grp:alts_toggle]
 overrideSettings = true


thanks!

---

