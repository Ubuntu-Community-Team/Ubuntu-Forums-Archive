---
title: "Sturtup Grub problem!!"
date: 2007-01-11
forum: General Help
---

### Post by moonliter on 2007-01-11
When I turned on computer today I got this error:

> GRUB loading, please wait.....

ERROR 17

so I can't even go ubuntu recovery or choose to start winxp thah I have on other partition.I use egy live cd now. What is happening 
Please help

---

### Post by geek_Man on 2007-01-11
Have you added a hardrive recently? I've been having this same problem, so I know more about it than I'd ever want to know.

---

### Post by moonliter on 2007-01-11
No I didn't but last night I couldn't shutdown ubuntu so I run fsck in recovery mode and just gave me some error i think mount problem error.After that this is happening

---

### Post by geek_Man on 2007-01-11
This just might be silly (but it has worked when stuff isn't working). Pop your Live CD in and turn it on. You don't really need to do anything, just turn on Ubuntu. Turn it off and try booting it again.

BTW, do have a memory card reader on your computer? 'Cause if you left a card in when you turned your computer off, GRUB might think that the card is the hardrive it should be looking at.

---

### Post by moonliter on 2007-01-11
I tried you suggusted but still same
I got this when run fdisk-l in terminal:

> Disk /dev/hda: 4311 MB, 4311982080 bytes
255 heads, 63 sectors/track, 524 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         523     4200966    7  HPFS/NTFS

Disk /dev/hdb: 15.0 GB, 15020457984 bytes
255 heads, 63 sectors/track, 1826 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         892     7164958+   7  HPFS/NTFS
/dev/hdb2             893        1825     7494322+   f  W95 Ext'd (LBA)
/dev/hdb5             893        1784     7164958+  83  Linux
/dev/hdb6            1785        1825      329301   82  Linux swap / Solaris


and also when I run gparted  for partition /dev/hdb5 where is ubuntu saying that is uknown

---

### Post by moonliter on 2007-01-11
anyone?

---

### Post by geek_Man on 2007-01-11
What do you mean "when I run gparted for partition /dev/hdb5 where is ubuntu saying that is uknown"?

---

