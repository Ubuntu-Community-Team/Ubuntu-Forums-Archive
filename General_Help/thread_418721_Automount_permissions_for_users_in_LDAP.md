---
title: "Automount permissions for users in LDAP?"
date: 2007-04-22
forum: General Help
---

### Post by jw29 on 2007-04-22
Hello,

I am a student system administrator at a college and currently, we have an LDAP server which authenticates all of our users, and we have machines running Ubuntu.  The problem is that automounting doesn't work because the users are not in the "plugdev", "floppy", "disk", etc., groups.

I had fixed a similar sound permission issue where our users were not in the "audio" group by editing /etc/udev/rules.d/40-permissions.rules and adding MODE="0666" to the end of the line for sound...I tried doing the same thing to the lines involving disks and it didn't work.

I know I can add it in fstab and have the users do a mount /media/usb or something along those lines, but is there any way to have it mounted automatically when the USB flash drive devices are plugged in?

Thanks.

---

