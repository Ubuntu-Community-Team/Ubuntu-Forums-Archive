---
title: "BusyBox on start-up?"
date: 2008-05-22
forum: General Help
---

### Post by She's My Man on 2008-05-22
Hi!!!
I just installed Ubuntu 8.04 on my 3 GHZ/736 MB RAM/10 GB free space on the partition I choosed for Ubuntu. But when I booted and selected Ubuntu from the avaible partitions, I got the boot screen and then:
> BusyBox v1.3.1 Debian inbuilt shell (ash).
(initramf)
I really know that there are only two kinds of people in the world: those who understand binary and those who don't... Like just what is BusyBox? A command-line thingy? I never was able to work with them! And what is a inbuilt shell "ash" or this (initramf)? I know, I'm a noob. Help is appreciated! TIA!
Don't forget: I'm an absolute noob, "beginner language" is the only thing I get.
Thanks guys!!! :KS

---

### Post by pointone on 2008-05-22
initramfs is an initial filesystem loaded into RAM that mounts your hard drive and generally does everything necessary to boot your system. When something goes wrong, the initramfs contains a built-in shell, BusyBox to allow you to troubleshoot and solve the problem.

Usually, there's an error message printed right before the BusyBox shell appears letting you know what happened. If you could be so kind as to try booting again and posting the last 10 or so lines that appear EXACTLY as you see them, it would really help us troubleshoot the problem.

---

### Post by Sporkofconfusion on 2008-05-22
I also had the same problem.  
If you boot in recovery mode, it will show you the errors that lead to a failure to boot.

Mine just failed to mount the disks.  Also said that "/etc/fstab" doesn't exist.  I tried restarting a few times, played around with thigns in the shell and the bootloader, etc.  No luck.  
My problem went away after I rebooted into windows, used it for 5 minutes, then shut down and restarted.  The non-technical logic behind this is... "Ubuntu, you better work or I can go back to windows... I don't want to, but I will if you force me."
There was also no logic to why it started having issues.  I didn't change any settings or anything...

Also make sure you don't have a cd in your drive.  Everytime its failed to boot I realized that there was a disk in the drive when booting.  Usually this does nothing, but its worth a shot.

---

### Post by damis648 on 2008-05-22
Actually, with usplash on you will not see the errors. Do the following and maybe we can help:

At the grub, press on on your default Ubuntu selection. Press e again when the menu changes. You will see a line with "quiet splash" at the end. ONLY delete those last two words and press enter. Now press b. Wait from the busybox prompt, then scroll up and give us a screenshot of the errors or just type them here and we may be able to help.

---

### Post by She's My Man on 2008-05-23
AAAA! I solved it! I simply reinstalled Ubuntu! Now it rocks! But I have one more question: I have three partitions. C: is for Windows and "my documents", D: For "my music" and for videos and stuff and E: is for Ubuntu. How do I access my documents/music/photos... etc which are on the other parttitions? TNX!

---

### Post by blank89 on 2008-07-09
> **Sporkofconfusion said:**
> I also had the same problem.  
Mine just failed to mount the disks.  Also said that "/etc/fstab" doesn't exist.  I tried restarting a few times, played around with thigns in the shell and the bootloader, etc.  No luck.  
My problem went away after I rebooted into windows, used it for 5 minutes, then shut down and restarted.  The non-technical logic behind this is... "Ubuntu, you better work or I can go back to windows... I don't want to, but I will if you force me."
There was also no logic to why it started having issues.  I didn't change any settings or anything...


Just for anyone who finds this post through google with the same problem:
More than likely, an NTFS partition was marked as dirty. In the error message it tells you to clean this partition by booting in to windows and running "chkdsk -r". This will try to clean the disk and mark it as clean so that Ubuntu doesn't have a problem mounting it on startup.

---

### Post by rfd123 on 2008-07-29
Boot up MS, go into Accessories, load the Command Prompt and type in "chkdsk" to scan the drive(s) - when it completes, reboot into Ubuntu and all will be just peachy keen. :)

---

