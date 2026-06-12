---
title: "help my drive has been corrupted"
date: 2015-07-16
forum: General Help
---

### Post by Seun_LanLege on 2015-07-16
i  just recently installed ubuntu 15 and i had problems with ubuntu not mounting my hdd luckily i discovered fast boot on windows was the cause of all my woes  but heres the problem my drive is a total of 320gb but to partioned 160gb(windows 8.1) 80gb(ubuntu 15.04) the remaining 80 gb seems to be corrupted cause i cant find it anywhere in ubuntu and windows  i realized that while i was trying to get my internal hdd to work in ubuntu i formatted the now corrupted 80gb volume in slow format and i accidentally turned the system off before the process completed.and now its corrupted, please ive done every check disk command i know in windows,i still cant seem to un-corrupt the partitioned volume it doesnt even show up on the file explorer  is there a away i can fix this in ubuntu?

---

### Post by gdesilva on 2015-07-16
Try using gparted on Ubuntu. Gparted will show you the partitions and unallocated space on your disk, if there is any. If you had another partition in the 80GB space and if it did not have any data then you can delete that partition and create a new one, either ntfs of ext4 but the first step would be to check it out with gparted.

---

### Post by tgalati4 on 2015-07-16
First, get another drive, perhaps an external USB drive and back up your important data on your Windows and Ubuntu partitions.  Then use *gparted* to try to fix the bad volume.

---

### Post by NoWayWin8 on 2015-07-16
> **Seun_LanLege said:**
> the partitioned volume it doesnt even show up on the file explorer  Windows File Explorer only shows you the Windows (C) volume, or other FAT/NTFS partitions which are not marked as hidden.  Use Windows "Disk Management" instead. It's in Control Panel - System - Administrative Tasks as "Create and Format Disk Partitions". It should display all partitions.

---

