---
title: "setting keyboard layout"
date: 2007-06-10
forum: General Help
---

### Post by smartduck on 2007-06-10
I installed Ubuntu 704 and I am unable to type numbers above qwerty(I have to use numeric keypad) and some special signs like dot and slovenian special letters

I am unable to change keyboard settings to Slovenia AND even just to reset my settings to default I get the same error:

Error activating XKB configuration.
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

xprop -root | grep XKB returns:

_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "cymotionlinux", "si", "pc-105", "lv3:ralt_switch"
_XKB_RULES_NAMES(STRING) = "xorg", "cymotionlinux", "si", "pc-105", "lv3:ralt_switch"

and  gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd returns:

gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = []
 model = 
 overrideSettings = true
 options = []


Please HELP ME - thanks - Grega smartduck

---

