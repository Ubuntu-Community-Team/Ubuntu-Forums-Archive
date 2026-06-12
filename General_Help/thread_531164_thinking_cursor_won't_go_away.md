---
title: "thinking cursor won't go away"
date: 2007-08-21
forum: General Help
---

### Post by manno on 2007-08-21
Whenever my mouse cursor is over my desktop (like when I've just rebooted and logged in) it displays the animated "thinking" icon. once I hover over a menu, or a window it goes back to the correct arrow cursor, until I hover over the desktop again. Does anyone out there know how to fix this, and why(if it's my fault) it happened? 

thanks,
-manno

---

### Post by Dave54 on 2007-08-21
I'm guessing it's an app and hoping gnome's not broken.

Go to "System > Preferences > Sessions" and list here what startup programs you have selected. You can also disable them one at a time, restarting after you disable it, to try to figure out which one is the cause.

Or, while you still have the thinking cursor, go to "System > Administration > System Monitor". On the "Processes" tab, click "% CPU" to organize it by cpu usage and try to identify the culprit.

---

