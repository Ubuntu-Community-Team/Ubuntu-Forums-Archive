---
title: "Restoring access to partitions in Windows XP"
date: 2007-09-29
forum: General Help
---

### Post by Learn_w_Graffix on 2007-09-29
I have a dual disk drive system. The computer WAS setup as follows:
drive 1 NTFS C: = windows xp sp2 ; drive 0 NTFS D: = old windows xp installation ; drive 0 E: = partition with documents & files ; drive 0 F: = partition with documents & files.
I disconnected the SATA wire to drive 1, and installed linux in partition D: (ext3), plus made a 4th partition of drive 0 for swap.
(I thought I would tell BIOS which drive to use for initial boots, rather than having linux's "choose your OS" startup menu.)
After installing linux in partition D: of drive 0, i reconnected (physically) drive 1.
All is well in linux. However, when I boot into Windows drive 1, C:, i have no access to drive 0. (Disk management says drive 0 is a dynamic disk that is unreadable.)
Is there any way to make partitions E: and F: (drive 0) available to Windows XP again? (Short of reformatting, please!) :) ?
Thanks very much!

---

### Post by Learn_w_Graffix on 2007-10-08
Does anyone have any ideas? I tried re-installing XP on the first partition -- partitions 2 and 3 still could not be read! Help! I now have Linux re-installed on partition 1 (and 4 for swap). I tried Ext2IFS_1_10c, but that only allows XP to read partition 1.
Thanks!

---

### Post by Learn_w_Graffix on 2007-10-09
What I eventually did was use BootIt NG to change partitions from "dynamic" to NTFS. Now can access both partitions from Windows just fine. Grub loader has vanished, however! Goes straight into Windows.

---

