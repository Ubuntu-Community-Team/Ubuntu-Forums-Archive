---
title: "Starting Ubuntu in Non Graphical interface"
date: 2007-03-03
forum: General Help
---

### Post by BlkMagik07 on 2007-03-03
Hey everyone, I have a question.

How do I start Ubuntu in a non-graphical state (Not running X server) so I can install the drivers for my new nVidia graphics card?  When running the driver install program they said that I can not be running the X server.

---

### Post by GTvulse on 2007-03-03
You have three options (in particular preferred order):

1. Select rescue mode in the boot loader menu

2. Drop to single user mode by typing "sudo telinit 1" at a terminal emulation window. Then return to full multiuser mode by typing "telinit 2" at the root text console.

3. Hit "Alt-Ctrl-F1" (it can be F1 to F6), login to your account and type "sudo /etc/init.d/gdm stop", when you are done, type "sudo /etc/init.d/gdm start".

---

### Post by tbodine on 2007-03-03
Also, if you want to actually have your computer start at a CLI login prompt all of the time, instead of the GNOME Display Manager, you can go into the System menu, select Services, and deselect GDM.
Then all you have to do to start X from the command line is type startx and GNOME should start up -- if you want a different window manager/desktop environment, edit your ~/.xinitrc

---

