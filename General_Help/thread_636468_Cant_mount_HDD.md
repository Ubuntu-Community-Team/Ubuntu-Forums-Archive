---
title: "Cant mount HDD"
date: 2007-12-09
forum: General Help
---

### Post by iiDopDop!! on 2007-12-09
I cant mount my HDD but i think it is because the last time it was running was on windows XP, but i the computer wasnt shut down properly and i have intsalled Ubuntu over the Windows so i cant load up windows  to shut down the drive properly. How can i fix this so i can use my other drive again??

---

### Post by iiDopDop!! on 2007-12-09
sorry to bump

I pasted "sudo fdisk -l" into terminal and i got this

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb5feb5fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9447    75882996   83  Linux
/dev/sda2            9448        9729     2265165    5  Extended
/dev/sda5            9448        9729     2265133+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc07fc07f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9728    78140128+   7  HPFS/NTFS

(I Have 2 HDD's one has the OS the others for music n movies n junk)

---

### Post by taurus on 2007-12-09
You can try

```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force
```
Now, back up your files from /media/sdb1 and reformat it to ext3 filesystem.

---

### Post by iiDopDop!! on 2007-12-09
thanks alot it worked and i have it mounted and im backing it up now. Just one last question how do i format the drive?

---

