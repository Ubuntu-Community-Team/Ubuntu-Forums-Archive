---
title: "After kill - CTRL-ALT-F7 doesn't bring back the GUI.."
date: 2015-10-08
forum: General Help
---

### Post by simba4 on 2015-10-08
Hello there,

I am ~new to ubuntu but not new to computers.


It seems that one of my apps (XBMC aka KODI) tends to hang the system.  When this happened, the mouse keep moving but nothing is clickable and the keyboard doesn't seem to respond (or respond very late).


Well, after looking around, I found two terminal commands that can help in this situation.  pkill and killall.


The usage is the same: pkill -9 kodi or killall -9 kodi.

The problem is that after killing kodi, the GUI is gone too.

CTRL-ALT-F7 doesn't bring back the GUI and after that, also CTRL-ALT-F1 seem to be frozen (black screen).


I found some commands to restore the GUI but they bring it back 'clean', as if I just restarted the desktop.


Is there another way to kill kodi while keeping the rest of the Apps as they where?


James

---

### Post by CantankRus on 2015-10-08
When you kill kodi try reloading compiz as well.
eg
```
pkill -9 kodi && compiz --replace
```
For me kodi doesn't run very well in sessions where compiz is the window manager.(ubuntu/unity)
Runs better in it's own session or "gnome flashback (metacity)" session.

---

