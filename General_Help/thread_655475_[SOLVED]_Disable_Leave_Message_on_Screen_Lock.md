---
title: "[SOLVED] Disable Leave Message on Screen Lock"
date: 2008-01-01
forum: General Help
---

### Post by dethredic on 2008-01-01
Is it possible to remove or disable the option to leave a message when the computer is in screen lock?

---

### Post by dethredic on 2008-01-01
bump

---

### Post by steveneddy on 2008-01-01
As long as we are there, can we put a background image on screen while the screen in locked?

OH - I guess we could if we had a screen saver set.

But at the re log in part of the lock screen, can we put a BG image there?

---

### Post by NilsE on 2008-01-01
To disable the "Leave Message" option edit the lock dialog profile by entering the following in a terminal:

gksudo gedit /usr/share/gnome-screensaver/lock-dialog-default.glade

Locate     auth-note-button      somewhere around line 307 in the file.

Just below that is a line that reads

<property name="visible">True</property>

Change True to False. NOTE: It is case sensitive,

NOTE2: This only works if you have not changed the screensaver lock dialog theme.

---

### Post by dethredic on 2008-01-01
Thanks NilsE works great!

---

