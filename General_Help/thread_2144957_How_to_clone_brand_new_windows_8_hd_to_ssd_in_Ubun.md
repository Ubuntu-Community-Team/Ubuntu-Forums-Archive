---
title: "How to clone brand new windows 8 hd to ssd in Ubuntu"
date: 2013-05-13
forum: General Help
---

### Post by mulluysavage on 2013-05-13
Ordered new laptop with windows 8 and an ssd to upgrade out of the box. I only have Ubuntu on my tower and will set up dual boot immediately. I plan to take out the laptop HD and mount both that and the ssd in my tower, and clone. If I do that with dd, is it just one command, or do I have to do separate setups for MBR and GRUB? I'm thinking If I clone and then connect the ssd In the laptop, I can then boot to Ubuntu live cd and install dual- boot.

---

### Post by oldfred on 2013-05-14
UEFI does not use MBR, but has gpt partitioning and boots from the efi partition. It has a protective MBR with just one entry for the entire drive so old partition tools will not try to format a drive they may see as empty.

With UEFI the Windows serial number is in the UEFI.

If you use dd, you have to do entire drive as gpt partitions have internal data that does not copy correctly with dd, but entire drive should work with dd. But dd is intended for same size drives to same size drives. But you may be able to shrink the Windows partition in the laptop with Windows disk tools first. Also gpt has the backup partition table at the end of the drive, so I do not know how that will work with dd? Maybe gdisk would fix it?

       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)


 Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by mulluysavage on 2013-05-16
And If I shrink the Windows partition, will it then not work with dd because dd is designed to work with entire drives? Or is that basically what you are saying?

---

### Post by oldfred on 2013-05-16
IF you shrink it first it may work. There was just another thread where a user with just Linux but gpt used dd to back up a drive and then restore it. The restore needed some repairs with gdisk to resync backup & primary gpt partition tables and he ran fsck on the Linux partition, but then it worked.

Reinstall is a lot better way. But I do not know how with Windows 8.

---

