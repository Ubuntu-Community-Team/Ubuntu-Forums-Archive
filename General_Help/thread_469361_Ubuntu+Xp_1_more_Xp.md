---
title: "Ubuntu+Xp 1 more Xp"
date: 2007-06-09
forum: General Help
---

### Post by Spyros_Gre on 2007-06-09
Hello! I did a search and couldn't find something as silly as what I want to do and here it is.

I have a dual boot system with Ubuntu and Xp in the same disk different partition.
I used to have vista and ubuntu but got rid of vista and then installed xp and reinstalled grub through the live cd.
I now want to make a third partition bootable with xp in it again. 
I don't know if I can do this and if I will be able to repair grub again. 

{{Somehow when I uninstalled  vista grub already had 1 windows entry and when xp came up and i repaired grub it showed xp just fine (automatically since I just reinstalled grub with root(hdo) and another command that I've forgoten)}}

please anybody who has done that cause I don't dare doing it without first knowing it is possible.
thanx
this is my sudo fdisk -l 


Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4526    36355063+   7  HPFS/NTFS
/dev/sda2            4527        6887    18964732+   f  W95 Ext'd (LBA)
/dev/sda3            6888        9039    17285940   83  Linux
/dev/sda5            4527        6787    18154446    7  HPFS/NTFS             <====***
/dev/sda6            6788        6887      803218+  82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

the <====*** is pointing to the partition I want to install second xp .

---

### Post by smoker on 2007-06-09
i believe this should be ok, xp will detect your previous xp install, and as long as you're installing to a different partition won't complain. in the past i had xp and w2000 and ubuntu installed. grub would start offering a choice of ubuntu or xp, and when xp was chosen, a windows option would come up to choose either xp or w2000.

one point, my three installs were all on primary partitions, not sure how it would work if a logical or extended partition was used!

best of luck

---

### Post by Spyros_Gre on 2007-06-10
Thanx for the fast response.
All went fine!!!!
2 XP partitions + 1 Ubuntu 


order



installed fist   -     second   
------------------      ------------------
            || ---------------------------  ||
            \/ ---------------------------  \/
        
|time|        
1st   |  Vista        -----     Ubuntu
2nd  | Ubuntu      -----         Vista asta la vista! (erased):D
3rd   |  Ubuntu     -----       XP
4th   |  Ubuntu     -----      XP - XP
:D

---

