---
title: "Dual boot with Windows 8 fails"
date: 2013-12-29
forum: General Help
---

### Post by sumit.r.agrnaya on 2013-12-29
So I here's what happened. I have a Windows 8 laptop and I tried to make a parition to put Ubuntu 12.04 on and that messed up my computer. It's constantly giving me an error message and I can't seem to get out. I put Ubuntu on live USb and that's how I'm talking here right now. Every time I try to boot it's giving some error saying "Boot failed". I also tried testdisk but that doesn't seem to work. I recently came across Boot-repair and my question is can it work to fix the Windows 8 boot problem?

Thanks!

---

### Post by kurja on 2013-12-29
Can you give the exact error message?

When running ubuntu off the cd, have you tried running fsck on your (unmounted) hard drive?

---

### Post by fantab on 2013-12-29
How did you "make a partition to put Ubuntu"?
What error message do you get?
I am not sure if Boot-Repair can help you, but what you need is a Windows Repair Disc or Windows Install Disc to repair your computer... You can also try OEM Recovery or 'reset to factory defaults'...

---

### Post by oldfred on 2013-12-29
Did you change boot mode in UEFI to CSM/BIOS/Legacy? If so Windows will not boot in that mode. Some do auto switch so it is not an issue, others have specific settings for each boot mode. Pre-Installed Windows 8 is UEFI only. And you should install Ubuntu in UEFI mode.

Always use Windows to shrink its own NTFS partition and reboot to let it run chkdsk. 
Always on hibernation or fast boot must be off.

Boot-Repair can do very little for Windows. It can install a BIOS/MBR boot loader, but not for UEFI.
Often if you have run Boot-Repair before it backs up boot files.
But often Windows needs chkdsk or its own repairCD or Flash drive.

 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by pouldney on 2013-12-29
I have an acer-axc-605  After installing ubuntu from DVD disk , I could not
boot wndows 8 .It did not appear in the grub menue.
 I ran Boot Repair from the installed ubuntu and it fixed the problem.

---

