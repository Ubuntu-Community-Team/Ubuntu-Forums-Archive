---
title: "Ubuntu Startup?"
date: 2008-04-30
forum: General Help
---

### Post by crashovaride on 2008-04-30
Hi all, 

I was playing around with my Ubuntu installation, and messing with  System > Preferences > [Session Options tab] i selected "Automatically Remember currently running applications when logging out." I deselected the option for this, and now, every time i start my ubuntu 7.10 box i get a shell prompt.

I have checked with BUM, i even checked in /etc/rc.* and i can't seem to find anything in there about gnome-terminal booting / launching when i get to my desktop. Any suggestions?

Thank you.

---

### Post by ryanhaigh on 2008-04-30
If you are getting a terminal openning when you login (as in the GUI still works but gnome terminal starts) close gnome terminal and anything else you don't want to open on login, go to system>prefs>sessions and press the remember currently running applications button.

---

### Post by crashovaride on 2008-04-30
Hey man, thanks it worked =)

---

