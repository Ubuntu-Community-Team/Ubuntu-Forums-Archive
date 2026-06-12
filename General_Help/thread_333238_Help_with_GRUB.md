---
title: "Help with GRUB"
date: 2007-01-07
forum: General Help
---

### Post by the.dark.lord on 2007-01-07
I ran into a spot of trouble with GRUB. I installed Ubuntu on my cousin's computer with on an old 20GB HDD(no troubles with installation, awesome :D ). He runs Win XP -God, help him- on an other hard disk drive. When I reboot the computer GRUB  loads up, and gives a choice of OS to run-this happens only when my hard disk is in his computer. When I remove my hard disk drive, GRUB still remains, and tries to load and says Error 21. Help please.

Thanks.

---

### Post by Koybe on 2007-01-07
Error 21 mean grub can't find the disk. This is because grub is installed on his disk but the informations for the grub menu are on yours. Why do you remove the hd?

If you need to be able to remove it, i think the best way is to install grub on the removable hd and just boot windows normaly on the original hd.

---

### Post by orb9220 on 2007-01-07
the grub is installed on the first disk where his xp resides. If you remove the second drive from the system grub has no way of knowing that.

You have to restore the mbr by:

Well the easy way is to boot up with your xp disk and enter recovery mode.

Use the Windows Setup floppy disks or the Windows CD-ROM to start your computer. At the "Welcome to Setup" screen, press F10 or press 'R" to repair.

After you start the Windows Recovery Console, you receive the following message:
Microsoft Windows(R) Recovery Console

The Recovery Console provides system repair and recovery functionality.

1: C:\WINDOWS

Which Windows Installation would you like to log on to
(To cancel, press ENTER)?

type 1 and enter
then type fixboot and enter
or fixmbr and enter

Type EXIT to quit the Recovery Console and restart the computer.

and that should do it.

---

### Post by the.dark.lord on 2007-01-08
> **orb9220 said:**
> the grub is installed on the first disk where his xp resides. If you remove the second drive from the system grub has no way of knowing that.

You have to restore the mbr by:

Well the easy way is to boot up with your xp disk and enter recovery mode.

Use the Windows Setup floppy disks or the Windows CD-ROM to start your computer. At the "Welcome to Setup" screen, press F10 or press 'R" to repair.

After you start the Windows Recovery Console, you receive the following message:
Microsoft Windows(R) Recovery Console

The Recovery Console provides system repair and recovery functionality.

1: C:\WINDOWS

Which Windows Installation would you like to log on to
(To cancel, press ENTER)?

type 1 and enter
then type fixboot and enter
or fixmbr and enter

Type EXIT to quit the Recovery Console and restart the computer.

and that should do it.

Thanks, but I think he doesn't have the recovery disk still. Is there any other way?

---

### Post by confused57 on 2007-01-08
If he has a floppy drive, this might be an option:

[http://www.users.bigpond.net.au/hermanzone/p18.htm#fdisk_mbr](http://www.users.bigpond.net.au/hermanzone/p18.htm#fdisk_mbr)

---

