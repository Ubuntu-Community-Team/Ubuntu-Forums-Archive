---
title: "Open Office 2.2 won't load"
date: 2007-06-03
forum: General Help
---

### Post by Bios Nova on 2007-06-03
Hey

I'm new to Ubuntu and i was wondering why Open Office 2.2 won't load up? I get to the splash screen, then that fades away then i get nothing. 

Thanks in advance for any help! oh I'm using Ubuntu 7.04

---

### Post by hvw on 2007-07-16
I had the same problem, but now it resolved. First of all, view installed openoffice components typing: “dpkg -l|grep openoffic”. You'll see many packages, try to remove core package, it would remove the others:
":~$ sudo apt-get remove --purge  openoffice.org-core"
It free up for about 50 Mb. Good work. Then you may use typical "Add/Remove" Gnome component  to add those parts of OpenOffice you need (for example OOo-Writer, OOo-Presentation).
You can install local-settings by typing:
After reinstall number of installed packages decreased from 27 to 7(!)

Try youself and you'll see.

---

### Post by Hagar Delest on 2007-07-19
First, you can rename your user profile /.openoffice.org2.
If no improvement, you can install the official version instead of the Ubuntu one, see here : [[Ubuntu] Installing OOo on Debian and Co.](http://www.8daysaweek.co.uk/forums/viewtopic.php?t=759)

---

