---
title: "How to disable beep when power (un)plug"
date: 2006-12-11
forum: General Help
---

### Post by christophe123 on 2006-12-11
Is there a way to disable the beep triggered by plugging/unplugging the power? 
It started after my upgrade to edgy so I assume it's a feature but I can't find a place to turn it off.

Also is it possible to disable the screensaver login after a suspend/resume cycle? I would like to go straight to my desktop.

Thanks,
Christophe

---

### Post by organica on 2006-12-11
Check the Power Management Preferences.  I believe the screen lock is in there.  I have kubuntu rulling on my laptop, so just pulling from memory here.  If that doesn't work, turn off the "Lock screen when screensaver is active" in you screensaver preferences.  I noticed sometimes my screensaver would kick in before my laptop went to sleep.

---

### Post by christophe123 on 2006-12-12
Hi organica,

No such a setting in gnome power management settings. There is an option in the screensaver (to lock it up when the screensaver starts) but it's disabled.

Thanks,
Christophe

---

### Post by christophe123 on 2006-12-12
Concerning the beep, I figured I can disable it with gconf-editor by reseting 
/apps/gnome-power-manager/enable_pcskr_beeping
The description of this setting seems to imply that something is not happy when I plug/unplug the power.

---

