---
title: "Booting to Desktop, no menus"
date: 2004-11-03
forum: General Help
---

### Post by Foxfyre on 2004-11-03
So I had Ubuntu running and all was going good but this morning I turn it on and log in and then Ubuntu comes up to show the desktop wallpaper, but none of the images or menu show up. I didn't make any changes before shutting down so I don't know of any settings I need to undo.

System:
Ubuntu 4.1

Gateway Solo 5300
P2 900 mHz
128 megs Ram
Dual boot with WinXp

Anyone got a solution?

---

### Post by ulrich on 2004-11-03
have you tried adding a new user and logging in as this user to see if this happens systemwide?

what says /var/log/XFree86 log?
are there any warnings (WW) or errors (EE) ?

---

### Post by Foxfyre on 2004-11-04
Alright, finally some time to try and figure this out more:

Created a new user from the failsafe terminal.
Attempted to log in as new user at normal Gnome, stopped loading like previously.
Attempted to log in as new user at failsafe Gnome, stopped loading like previously.

Checking Xfree86 log shows no obvious errors, I would post it here but I'm currently on campus and stuck with a catch 22 for internet access from the terminal. I don't have lynx installed, and to get it via apt I need to log online and enter password for campus walkup network, but I need lynx to do that.

So I'll try some more this evening when I get home.

---

