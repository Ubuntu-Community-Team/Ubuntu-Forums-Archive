---
title: "window manager problems"
date: 2007-04-30
forum: General Help
---

### Post by stalefist on 2007-04-30
ive got beryl window manager installed and was messing around with the effects. i turned on the blur effect and suddenly my system stopped. is there a way to change the effects through a terminal or to change my window manager back to the default?

---

### Post by vav on 2007-04-30
Options:
Try Ctrl+Alt+Bksp to restatrt Xorg... sometimes that resets Beryl.
OR When you get the login page, go to the bottom options and select session - gnome failsafe, then start beryl-manager or beryl-settings and change your settings.
OR Open a terminal and edit the settings files in ~/.beryl/ folder using your favorite text editor, or delete the .beryl folder altogether and redo all your settings.

---

### Post by ajgreeny on 2007-04-30
You could always uninstall beryl temporarily (sudo apt-get remove beryl) and restart x, or reboot, though there may be a more direct way that I don't know about.
EDIT.  Whoops, I forgot about the .beryl folder.  Don't know how as I have had to do that myself a couple of times.

---

