---
title: "Running local boot scripts"
date: 2008-04-24
forum: General Help
---

### Post by tomgoos on 2008-04-24
Hi all,

About a month ago I installed xubuntu 7.10 which was working fine. I am really enjoying this OS and all the great community support.

However, for some reason xubuntu has stopped working. The boot stops at the line "Running local boot scripts (/etc/rc.local)   [ok]". After trying a couple of things I found here on the forum (e.g. ctrl-alt-F2 xstart) I thought, what the hey, I'll just install ubuntu 8.04. To my surprise booting from the desktop cd gives me the same behavior. I suspect something else is wrong, but I have no clue what it could be. Any thoughts on this?

Thanks in advance and greetings,
Tom

---

### Post by justleen on 2008-04-24
what happens when you press a key, when you have that message on screen?

(i have one system with server edition installed.. it will "hang" on that message,but its actually waiting for input..)

---

### Post by tomgoos on 2008-04-24
I can just type some stuff and it gets displayed on the screen. And if I press ctrl-alt-F2 i get to log in but only in text mode. Is there some kind of log file that I could check to see what went wrong?

---

### Post by justleen on 2008-04-24
/var/log/messages
or, login in text mode, and issue a "dmesg"

---

### Post by tomgoos on 2008-04-24
The messages file ends at some PCMCIA messages
 
something like:
[   97.856000] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.

oh, I did a |grep error and it gives me the following error several times:
ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.

Also, I should mention that sometimes the screen goes blank for a second and then returns again. :confused:

---

### Post by justleen on 2008-04-24
sounds like X is not starting for some reason.
try logging in in text mode again, and reconfigure the Xserver
```
 sudo dpkg-reconfigure xserver-xorg
```

---

### Post by tomgoos on 2008-04-24
jeeehaaa! That worked. It's up and running again :) Thanks a bunch!

Any idea how this could happen? I'll check now if I can run the boot cd now as well.

---

