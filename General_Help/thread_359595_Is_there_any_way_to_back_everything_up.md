---
title: "Is there any way to back everything up?"
date: 2007-02-12
forum: General Help
---

### Post by smcnally on 2007-02-12
Hi everyone, I'm very new to the Linux world so please bear with me.  I have  dual boot machine (XP on one drive and Ubuntu Edgy on a second drive).  I just about have Edgy where I want it.  I have Beryl installed and running well now and have 99% of what I need to make me feel as comfortable in Ubuntu as I have been in windows.  I was thinking last night that if anything were to happen to this PC, it would be aweful to not only remember everything I had to do to get it to where it is, but to actually have to install each thing again.  Is there any suggestions on how to back up what I've done so if I ever have to redo this system it is right there in front of me?  Any help would be great.  

Thanks,
-Steve

---

### Post by jazzgossen on 2007-02-12
Your home directory (including per-user settings) is in /home, most system configuration settings are stored in /etc, and you probably want to back-up /usr/local also. So simply copying these three directories (and their subdirectories) somewhere else will give you a reasonable system backup. To be complete, you can of course copy everything else as well, but the stuff that's in other directories should be easily recoverable from a new installation.

---

### Post by smcnally on 2007-02-12
Thanks!  That's exactly what I was looking for.

---

