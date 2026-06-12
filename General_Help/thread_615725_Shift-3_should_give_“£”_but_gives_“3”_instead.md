---
title: "Shift-3 should give “£” but gives “3” instead"
date: 2007-11-17
forum: General Help
---

### Post by bristleburger on 2007-11-17
Since upgrading to gusty, the sterling character on my keyboard is no longer accessible. Shift-3 should give “£” but gives “3” instead.

Attempting to use system->preferences->keyboard to fix the problem results in the following message and sometimes locks my system up (although I am able to ssh in to reboot):
  Error activating XKB configuration.

  It can happen under various circumstances:

  - a bug in libxklavier library

  - a bug in X server (xkbcomp, xmodmap utilities)

  - X server with incompatible libxkbfile implementation



  X server version data:

  The X.Org Foundation

  10300000



  If you report this situation as a bug, please include:

  - The result of xprop -root | grep XKB

  - The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd


xprop -root | grep XKB gives:
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "uk", "gb", ""

_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "uk", "gb", ""


gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd gives:
 layouts = []

 model = 

 options = []

 overrideSettings = true



Any suggestions on how to fix this would be most welcome.

---

### Post by IanW on 2007-11-17
Your answer is in [this]("http://ubuntuforums.org/archive/index.php/t-69052.html") thread.

---

### Post by bristleburger on 2007-11-17
Outstanding! Thanks IanW.

---

