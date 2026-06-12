---
title: "Upgrade gets black screen and tty1"
date: 2018-04-29
forum: General Help
---

### Post by tajreed on 2018-04-29
Upgraded from 17.1 to 18.04 using "update-manager -cd" and get black screen with tty1 and login. I can log in but can't get beyond the command line.
Any thoughts?

---

### Post by dino99 on 2018-04-29
Proposing the usual tweaks via the command line:

- first login to gnome on xorg (dropdown gir icon)
- as its a rolling installation, try to clean the system via clean/autoclean/autoremove  and using 'gtkorphan' & 'bleachbit' (as root but carefully select the options) 
- then update and run 'sudo apt-get install -f' & 'sudo dpkg --configure -a'
- and logout/in

if the problem persist, then glance at warnings(bright lines) and errors (red lines) via 'journalctl -b'

it can be also a graphic driver issue: if nvidia is active then purge it to use 'nouveau', then install a driver <390

---

### Post by tajreed on 2018-04-29
No luck. What is tty1 and how did I get there after upgrading to 18.04? Been upgrading on this machine for several years with no problems. 18.04 is fully updated and autoremove has been used to clean things up.

Any more help out there UBUNTU land.

Thanks

---

### Post by tajreed on 2018-04-29
More info-'GTK -warning'. Cannot open display.

---

### Post by Frogs Hair on 2018-04-29
18.04 no longer in development. Moved to *General Help. *

---

