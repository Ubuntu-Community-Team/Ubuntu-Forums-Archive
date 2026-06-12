---
title: "QT Parted error"
date: 2006-11-28
forum: General Help
---

### Post by le_vainqueur on 2006-11-28
I am dual booting XP and Ubuntu on two hard drives.  I left XP on my 40GB HD and made it the slave, and installed Ubuntu on my new 160GB HD.  I'm trying to create a FAT32 partition on my 160GB HD to share with XP, but when I start QT Parted I get an error saying 

> No device found.  Mabye you're not using root user?

Any advice?

---

### Post by xopher on 2006-11-28
Make sure you run the program as root - or more specifically as sudo

Just put sudo infront of the command when running it.

---

### Post by le_vainqueur on 2006-11-28
How do I run it with a command?  I was just opening it from the applications menu.

---

### Post by le_vainqueur on 2006-11-28
Ok, I finally found a guide to help me.  I ran it and I get this error:

> :~$ sudo qtparted
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Error: File system was not cleanly unmounted!  You should run e2fsck.  Modifying an unclean file system could cause severe corruption.
No Implementation: Support for opening ntfs file systems is not implemented yet.Error: File system was not cleanly unmounted!  You should run e2fsck.  Modifying an unclean file system could cause severe corruption.
No Implementation: Support for opening ntfs file systems is not implemented yet.Error: File system was not cleanly unmounted!  You should run e2fsck.  Modifying an unclean file system could cause severe corruption.


---

### Post by le_vainqueur on 2006-11-29
In an attempt to circumvent this error I tried to run qt parted from the live CD.  I can run the program without errors, but when I right click my ext3 partition, I cannot resize it.  The option is greyed out.  This is the partition that I need to resize in order to add a partition for a shared drive.  Any advice with this new issue?

---

### Post by konst88 on 2006-11-29
Make sure this partition is not mounted. If yes, unmount it.

---

