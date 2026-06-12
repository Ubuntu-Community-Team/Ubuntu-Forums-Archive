---
title: "USB Write Protect (physical)Switch"
date: 2015-03-17
forum: General Help
---

### Post by mrJTparadise on 2015-03-17
Hey all,

I have a USB drive /dev/sdb, and inside sdb are some separate mount points ( /, /boot, and so on. )

I have a hardware write protect switch which I can flip to enable/disable write protect.

When I assert the write protect switch to the ON position, Linux automatically detects, "hey, write protect mode", and spits out the following whenever I am trying to autocomplete :

-bash: cannot create temp file for here-document: Read-only file system
This is great. This means my switch is working and is not letting bash create the temporary file.

However, 

When flipping the switch to the OFF position, Linux does NOT automatically detect the change in the write protect status.  The only way to reverse the write protect switch is to flip the switch to OFF and reboot.

Does anyone have any knowledge on how to update the write protect status of the drive?

---

