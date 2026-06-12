---
title: "Keyboard layout reset on reboot"
date: 2014-10-10
forum: General Help
---

### Post by Skyflier on 2014-10-10
Hi.

I'm having a problem with Ubuntu 14.04. Every time I reboot the system, the keyboard layout reverts back to English (US) and I always need to change it back to the one I want in the settings which is frustrating.
How can I sort this out?

---

### Post by jamesisin on 2014-10-10
This might be useful.

[http://askubuntu.com/questions/209597/how-do-i-change-keyboards-from-the-command-line](http://askubuntu.com/questions/209597/how-do-i-change-keyboards-from-the-command-line)

---

### Post by Skyflier on 2014-10-12
I tried to use setxkbmap to set the keyboard layout but to no avail. Ubuntu keeps resetting the keyboard layout to English US.

---

### Post by jamesisin on 2014-10-13
I'm not clear what might be causing the issue, but I suppose you could just add that code to your bashrc file.  I realize that's more workaround than solution.

---

### Post by Skyflier on 2014-10-13
It seems like this happens with the 64 bit version or with UEFI boot. I have a friend with 32 bit version and it doesn't have this issue. It seems like only Ubuntu 14.04 has this behavior in my PC.

---

### Post by amilopowers on 2015-04-24
Thanks Skyflier that helped! 

I had to disable "UEFI-Boot" in the setup menu.

---

