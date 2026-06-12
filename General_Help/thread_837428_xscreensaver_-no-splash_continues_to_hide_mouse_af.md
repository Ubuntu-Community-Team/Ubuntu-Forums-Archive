---
title: "xscreensaver -no-splash continues to hide mouse after inactive"
date: 2008-06-22
forum: General Help
---

### Post by memories on 2008-06-22
Hello. I set my xscreensaver-demo settings (I use blacksheep but this happens with any screensaver) and when I leave the screen, or lock it, everything is fine until I try to get back on the desktop. 

After entering my password, I can use the keyboard, but the mouse pointer is unavailable/gone/hidden. The mouse LED remains on, and a quick fix is to alt+ctrl+F1 into a terminal and "killall xscreensaver" or kill it by pID. Doing so brings the mouse back.

Sometimes I see gnome-screensaver is also on.. could it be because both screensaver software are conflicting? I've never setup or needed gnome-screensaver. 

Hardy Heron 8.04 w/ current default installation of Xorg and official nvidia drivers installed via nVidia's run script.

---

### Post by Anduu on 2008-06-22
You can disable the Gnome screensaver.

Run ```
gconf-editor
``` in a terminal.

Go to apps/gnome_settings_daemon/screensaver and uncheck the start_screensaver box.Restart.


This should take care of any conflicts.Can't promise it will fix the mouse problem but it will eliminate one possible cause.

---

