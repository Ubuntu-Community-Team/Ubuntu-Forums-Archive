---
title: "Hang on Boot"
date: 2013-01-11
forum: General Help
---

### Post by Mike Green9 on 2013-01-11
[FONT=Arial, sans-serif]Hi. [/FONT]
  

 [FONT=Arial, sans-serif]I have a dual boot (Windows 7 & Ubuntu 12.10) system, with 2 drives. The second drive (partitioned identical to the first) is used purely for backups.  When I boot, Ubuntu is finding some problems on my second drive:[/FONT]
 

 [FONT=Arial, sans-serif]	Udev [  ] /sbin/blkid -0 udev -p /dev/sdb9   (Windows partition)[/FONT]
 [FONT=Arial, sans-serif]	Udev [  ] /sbin/blkid -0 udev -p /dev/sdb1   (Windows partition)[/FONT]
 

 [FONT=Arial, sans-serif]It then gives me the option to 'i'gnore the problem. I enter 'I', and the boot continues successfully.[/FONT]
 

 [FONT=Arial, sans-serif]The second drive is fine. I use Windows to backup data onto it, and have in fact, disabled the first drive, and run successfully solely on the second drive.[/FONT]
 

 [FONT=Arial, sans-serif]I have also tried 'sudo fsck /dev/sdb9' and   sudo fsck /dev/sdb1' and they came out 'clean'.[/FONT]
 

 [FONT=Arial, sans-serif]I have set up the BIOS to ignore the second drive. Windows respects this, but Ubuntu seems to ignore the BIOS setting??[/FONT]
 

 [FONT=Arial, sans-serif]I have played a little with FSTAB (System – Preferences - Disks) , but the problem seems to occur before FSTAB is in play. No matter how I alter FSTAB, the second drive is being accessed during the boot.[/FONT]
 

 [FONT=Arial, sans-serif]To further complicate the matter, I occasionally get other errors while booting:[/FONT]
 [FONT=Arial, sans-serif]	Ubuntu: Inode Table for group 0 in not in group[/FONT]
 [FONT=Arial, sans-serif]                          				&[/FONT]
 [FONT=Arial, sans-serif]	Errors were found while checking the disk for /[/FONT]
 

 [FONT=Arial, sans-serif]Question: How can I tell Ubuntu to forget about the second drive, as well as other partitions in the first drive ? [/FONT] 
 

 [FONT=Arial, sans-serif]Thanks,[/FONT]
 

 [FONT=Arial, sans-serif]M....[/FONT]

---

