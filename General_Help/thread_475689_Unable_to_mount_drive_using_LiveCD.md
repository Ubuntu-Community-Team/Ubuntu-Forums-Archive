---
title: "Unable to mount drive using LiveCD"
date: 2007-06-16
forum: General Help
---

### Post by tefflox on 2007-06-16
Hi, I've been scouring the forums for hours on different techniques to restore the hdd after having it corrupted by the windows mbr.  I have a first drive (sda) containing ubuntu feisty, and a second drive (sdb) containing windows xp.  So far I am able to load xp fine, and I have gone into the settings to disallow any usage of the first hard drive from within windows.  however, it is too late now.

The best advice i can find says to load the LiveCD and use the command:

sudo mount -t ext3 /dev/sda1 /media/recovery
(where the latter directory is already established)

but this does not work.  I am unable to mount this partition from the live cd to continue fixing the "job control turned off" errors associated with running windows.  Please help.

---

### Post by Reugen on 2007-06-16
So whats the terminal output when you mount the first hard drive?  How do you mean corrupted, if it is only that you cannot access it then you might want to try supergrub, it will write a new bootloader that will allow you to boot into both operating systems [http://supergrub.forjamari.linex.org](http://supergrub.forjamari.linex.org). If windows made any changes to sda besides writing the bootloader it would have reformatted it in either ntfs or fat32 (unless you have Diskinternals Linux Reader or something akin to it installed)-if windows had r/w access to the drive then  -t ext3 wouldn't  work.  Anyways you should probably try supergrub since it sounds like you didn't let windows reformat the first drive.

---

