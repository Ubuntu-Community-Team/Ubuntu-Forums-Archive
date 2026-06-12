---
title: "[SOLVED] .Xclient script"
date: 2008-01-31
forum: General Help
---

### Post by gerod on 2008-01-31
Hi to all. Sorry if this is not the appropriate forum.
I want to launch vncviewer automatically at startup with gdm auto login and a script.
In other distribution (CentOS) it is simply needed to edit the .Xclient-default script adding the desired line (for me vncviewer ....)
The autologin is not a problem.
I tried with Ubuntu 7.04 creating a new user and adding .Xclient and .Xclient-default in the home directory (as i did successfully for CentOS), but it seems not to work.

Any idea? :confused:

---

### Post by pointone on 2008-01-31
Try either using /home/username/.xinitrc, or simply using the GUI session manager in System > Preferences > Sessions.

---

