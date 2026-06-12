---
title: "Help me log In, please !"
date: 2007-04-15
forum: General Help
---

### Post by EverHardy on 2007-04-15
Hi EveryBuddy

I'm (rather I was) running Ubuntu (Feisty Fawn Beta). I recently installed democracy tv player (0.9.2.1) from synaptic package manager. It kept closing itself after every video clip, so I thought to compile latest version from the official website, as synaptic was unable to resolve some dependencies for the latest version.

I installed the packages somehow in ubuntu and ran the run.sh script from the democrarcyplayer's latest source files (0.9.5). Since then, I'm unable to log In to my GNOME Desktop.Please, don't laugh at my stupidity, I'm a new comer to Linux and wanted to compile an application from it's source. I tried logging in to KDE as well, but system gave me same problem (as shown below from .xsession-errors file)

-----------------------------------------------------------------
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp

/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w 

/var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "everhardy"

/etc/gdm/Xsession: Beginning session setup...
mkdtemp: private socket dir: No space left on device

--------------------------------------------------------------------------------

Can anybody please help me recover from this problem ? I don't want to stay in Windows XP for long.

with regards
EverHardy

---

### Post by llamakc on 2007-04-15
Your home partition is full. 

** mkdtemp: private socket dir: No space left on device**

If you did not create a separate home partition, then your / partition is full.

---

### Post by EverHardy on 2007-04-15
Thanks llamakc for your prompt reply.

Yes, I'm using separate /, /boot and /home partitions and it's unbelievable to see my 7 GB /home partition full (only 354 MB left). I'm going to increase that partition space. Thanks again, llamakc.

By the way, is there any ubuntu software for graphically checking how the disk space is being consumed by all applications and data ?

with regards
EverHardy

---

### Post by TheWizzard on 2007-04-15
> **EverHardy said:**
> By the way, is there any ubuntu software for graphically checking how the disk space is being consumed by all applications and data ?

use xdiskusage! 
also check out this link:
[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

---

