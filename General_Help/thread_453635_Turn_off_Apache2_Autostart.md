---
title: "Turn off Apache2 Autostart"
date: 2007-05-24
forum: General Help
---

### Post by BigDH01 on 2007-05-24
I installed Apache2 in kubuntu via apt-get and it went perfectly.  However, I just installed apache to do some testing from my home machine.  I don't want it on all of the time.  How can I turn off the autostart so I don't have to turn it off when I restart my machine?  Thank you for the help.

---

### Post by pbw on 2007-05-24
There's lots of ways, here's a couple.. 
Remove the symlink in /etc/rc2.d, Or
run update-rc.d -f apache2 remove, Or 
Install bum (boot up manager) for a gui solution.

Also, I don't use gnome, but you might like to check gnome-system-tools, it may provide an option to disable.

--pbw

---

### Post by BigDH01 on 2007-05-24
> **pbw said:**
> There's lots of ways, here's a couple.. 
Remove the symlink in /etc/rc2.d, Or
run update-rc.d -f apache2 remove, Or 
Install bum (boot up manager) for a gui solution.

Also, I don't use gnome, but you might like to check gnome-system-tools, it may provide an option to disable.

--pbw

Works, Thanks!

---

### Post by scott_g on 2007-05-24
In Gnome, you could go to System/Administration/Services and uncheck the service titled Web Server, although it looks like your problem has already been solved...

Scott

---

