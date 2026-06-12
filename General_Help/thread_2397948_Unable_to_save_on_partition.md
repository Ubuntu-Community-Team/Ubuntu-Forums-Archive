---
title: "Unable to save on partition"
date: 2018-08-05
forum: General Help
---

### Post by thaddeus2 on 2018-08-05
HI,

I have two partitions

/dev/sda2 = 181 GB 
/dev/sda3 = 261 GB 

/dev/sda1  *         2048   1026047   1024000   500M  7 HPFS/NTFS/exFAT
**/dev/sda2         1026048 380741631 379715584 181,1G  7 HPFS/NTFS/exFAT**
/dev/sda3       429051904 976769023 547717120 261,2G  7 HPFS/NTFS/exFAT
/dev/sda4       380743678 429051903  48308226    23G  5 Extended
/dev/sda5       380743680 429051903  48308224    23G 83 Linux


I have my data on sda3 and i an read write but on sda2 the partition is empty and i cannot save anything on sda2 there is no option of right click new folder 

Please advise.

---

### Post by oldfred on 2018-08-05
Is one of those partitions Windows and what version.
If not running Windows be sure to have a Windows repair flash drive as NTFS will need chkdsk if any errors and you cannot run chkdsk from Linux.

If Windows 8 or 10 is fast start up on. That turns on the hibernation flag & Linux NTFS driver will mount as read only if hibernated or if it needs chkdsk to prevent any damage. Default mount will either not mount at all or mount read only.

Generally better to set any Windows system partition, the c: drive, as read only and use shared data partitions. But newer Windows still needs fast start up off as it sets all NTFS partitions as hibernated.

---

