---
title: "Stop xserver (rc 3?)"
date: 2007-02-28
forum: General Help
---

### Post by Meson on 2007-02-28
I'd like to stop xserver, but I'm not sure how to make runlevel 3 be a terminal.  Or at least just stop xserver temporarily in any runlevel.  Why is 2 - 5 the same in Ubuntu?  Is there a command / method for running strictly in the shell?

(Trying to install nvidia drivers)

---

### Post by llamakc on 2007-02-28
Logout of Gnome(or KDE). Type:

ctrl-alt-F2

Login. Type:

sudo /etc/init.d/gdm stop (or /etc/init.d/kdm stop if you're on Kubuntu)

Now, run your script or do whatever it is you want to do that requires X to not be running.

---

