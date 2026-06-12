---
title: "Keyboard problems"
date: 2006-10-29
forum: General Help
---

### Post by LocoMan on 2006-10-29
I'm having some keyboard related problems in ubuntu.

First one is that the AltGR key just isn't working, no idea why. I'm using a Spanish keyboard and without it I can't do the at symbol (as in emails) or the pound symbol (which I need for IRC).

Another related issue is that I can't change the keyboard config (was trying to change it from Generic 104 key to Generic 105 key to see if it fixed the AltGR thing), but anytime I try that or try to add another language I get this error:

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70101000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

When I do those last two on the console, I get this:

xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc104", "sp", "", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc104", "sp", "", ""


gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = []
 model = pc105
 options = []
 overrideSettings = true


I'm using Edgy 6.10, originally 6.06 and then upgraded, but the AltGR didn't work before the upgrade either.

BTW, I'm kinda newbish, so if you ask to change something or check something, please tell me where to find it first... :)

---

### Post by gnomeza on 2006-11-12
Spanish key layouts are 'es', not 'sp'.

---

