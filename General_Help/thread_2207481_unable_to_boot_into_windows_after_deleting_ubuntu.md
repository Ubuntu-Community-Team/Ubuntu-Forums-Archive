---
title: "unable to boot into windows after deleting ubuntu"
date: 2014-02-23
forum: General Help
---

### Post by umut2 on 2014-02-23
[COLOR=#000000][FONT=Segoe UI]I accidentally deleted Ubuntu partitions with GParted and when i restarted the pc it was unable to find the grub bootloader (which was the primary bootloader) and didn't let me boot into windows b/c i had installed ubuntu alongside windows, not into a completely distinct partition. now it's only showing grub rescue screen when i boot the pc, which i can't use since there isn't left anything related to ubuntu on hdd. i tried to boot into ubuntu installation usb stick, but it kept showing the grub rescue screen. then i prepared a windows recovery usb stick, it made it to the installation screen but there wasn't any repair option. probably b/c windows keeps recovery files in the same partition with the main part. do you see a way out of this situation other than reinstalling windows? And if not, would i preserve everything i have in windows.old?  [/FONT][/COLOR]

---

### Post by jeanjd63 on 2014-02-24
Hello

If you can boot on recovery key of windows, and you can open a recovery console, you have only to do :
On XP :
**fixmbr**
on Vista and others :
**bootrec  /fixmbr**

---

### Post by Mark Phelps on 2014-02-24
> I accidentally deleted Ubuntu partitions with GParted and when i restarted the pc it was unable to find the grub bootloader (which was the primary bootloader) and didn't let me boot into windows b/c i had installed ubuntu alongside windows, not into a completely distinct partition. 

This is a contradiction -- you say you deleted the Ubuntu partition but then, you next say you did not install into an Ubuntu partition.

When you do the first, Ubuntu installs GRUB -- and if you have an MBR hard disk, it installs a small part of it to the MBR, with the bulk of it being installed to the first Linux filesystem partition. If you then remove that partition, GRUB will fail.

When you do the second (install from inside Windows), GRUB is NOT installed because Ubuntu exists in a single file (root.disk) located inside the first Windows filesystem partition.  You remove Ubuntu in those cases by uninstalling it -- like any other Windows app.

So -- which of these is really the case?

Also, which version of Windows are you using -- need to know to provide detailed advice.

---

