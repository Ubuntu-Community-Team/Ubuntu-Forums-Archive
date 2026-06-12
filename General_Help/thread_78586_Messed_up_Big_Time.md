---
title: "Messed up Big Time"
date: 2005-10-18
forum: General Help
---

### Post by torstenprahl on 2005-10-18
Where to begin....

I Beleive i installed GTK2 over another version of GTK.  Now when i boot up i end up in console w/ no option of loggin in with gnome or KDE.

I am not sure what do do here.  Any suggestions?

Thanks,

Torsten

---

### Post by mlomker on 2005-10-18
Have you tried **sudo dpkg-reconfigure gdm** from a prompt?

You could then try **sudo gdm**.  If that doesn't work then take a peek at the logs with **nano /var/log/Xorg.0.log**.

---

### Post by torstenprahl on 2005-10-18
tried that...rec'd:

gdm brooken or not fully installed.

how would I bring up the nano/var/log/Xorg.o.log file?

I'm new to the linux world so.......

Thanks,

T

---

### Post by mykey on 2005-10-18
[QUOTE=torstenprahl]
gdm brooken or not fully installed.

how would I bring up the nano/var/log/Xorg.o.log file?
[/QUOTE]

you are supposed to type 'nano /var/log/Xorg.0.log' in a terminal

this does not sound like a gdm issue but a xserver configuration issue - to get the x-server to run after an installation can be a little tricky

try **sudo dpkg-reconfigure xserver-xorg**

---

### Post by torstenprahl on 2005-10-19
I Think I am pretty much hosed.  Will be doing a re-install now.  Thanks for the help though.

T

---

