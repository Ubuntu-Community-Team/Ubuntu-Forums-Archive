---
title: "Unmoutable_Boot_Volume"
date: 2007-09-29
forum: General Help
---

### Post by lakrids on 2007-09-29
OK, I have read 80000 threads about this problem, with 0 advice which could help me. This is really getting frustrating, I don't want to spend days trying to dual-boot, so please help me with this.

Here is the complete list of things I did before I got the UNMOUNTABLE_BOOT_VOLUME error from the Windows boot screen.
1.  Using the Windows XP install CD, I formatted my whole 180 GB hard disk.
2.  I created a new partition (c:), and installed Windows XP. Worked fine. Excellent even.
3.  Using the Ubuntu 7.04 Live CD, I created manually a swap partition and a / ext3 main partition for Ubuntu.
4.  I installed Ubuntu. Worked fine.
5.  Next reboot, booted Windows from Grub menu. Windows loading screen appeared for a couple of seconds, then Blue screen of death : UNMOUNTABLE_BOOT_VOLUME.

Here's a list of all the thing I tried, without success : 
-  Using Windows CD, went into recovery mode and typed chkdsk, fixboot, etc..., always getting the error message "unrecoverable error on disk" or something like that.
-  Tried to boot Windows in Safe mode, w/ networking, etc...
-  Searched in BIOS
-  Read Microsoft documentation, and applied resolution methods
-  Searched internet and applied help found in forums.
Without success.

I assume when I manually created the partitions for Ubuntu WITH the Ubuntu CD, the partition table became unreadable by Windows.

Now I am reformatting the whole disk, and I need suggestions how to do it this time. Make partitions with Windows CD before installing Win and Ubuntu? That's a problem, because the Windows CD only recognizes 130 out of my 180 Gb disk. Create c: partition for windows and resize it with Ubuntu CD? I heard I can get the same problem this way. Create partition for Windows and use all available disk space for installing Ubuntu? Can get the same problem.

So please, anyone with suggestions or advice, please help! Let's find a solution to this problem.

Thank you,

Lakrids

---

### Post by dcstar on 2007-09-29
> **lakrids said:**
> OK, I have read 80000 threads about this problem, with 0 advice which could help me. This is really getting frustrating, I don't want to spend days trying to dual-boot, so please help me with this.

Here is the complete list of things I did before I got the UNMOUNTABLE_BOOT_VOLUME error from the Windows boot screen.
1.  Using the Windows XP install CD, I formatted my whole 180 GB hard disk.
2.  I created a new partition (c:), and installed Windows XP. Worked fine. Excellent even.
3.  Using the Ubuntu 7.04 Live CD, I created manually a swap partition and a / ext3 main partition for Ubuntu.
4.  I installed Ubuntu. Worked fine.
5.  Next reboot, booted Windows from Grub menu. Windows loading screen appeared for a couple of seconds, then Blue screen of death : UNMOUNTABLE_BOOT_VOLUME.

Here's a list of all the thing I tried, without success : 
-  Using Windows CD, went into recovery mode and typed chkdsk, fixboot, etc..., always getting the error message "unrecoverable error on disk" or something like that.
-  Tried to boot Windows in Safe mode, w/ networking, etc...
-  Searched in BIOS
-  Read Microsoft documentation, and applied resolution methods
-  Searched internet and applied help found in forums.
Without success.

I assume when I manually created the partitions for Ubuntu WITH the Ubuntu CD, the partition table became unreadable by Windows.

Now I am reformatting the whole disk, and I need suggestions how to do it this time. Make partitions with Windows CD before installing Win and Ubuntu? That's a problem, because the Windows CD only recognizes 130 out of my 180 Gb disk. Create c: partition for windows and resize it with Ubuntu CD? I heard I can get the same problem this way. Create partition for Windows and use all available disk space for installing Ubuntu? Can get the same problem.

So please, anyone with suggestions or advice, please help! Let's find a solution to this problem.

Thank you,

Lakrids

I would speculate that you have a bad sector on the hard disk, and as luck would have it, it only became apparent after you completed the Ubuntu install.

You may be able to find a diagnostics/rescue CD on the net to download and use to scan your hard disk, this may be able to find any bad blocks and do something about them.

---

