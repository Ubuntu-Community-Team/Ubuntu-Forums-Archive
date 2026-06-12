---
title: "Trying to remove NTFS Partition."
date: 2019-01-06
forum: General Help
---

### Post by stonerrob420 on 2019-01-06
Hello everybody, I recently installed ubuntu mate 18.04.01 LTS on my Windows 10 machine on a seperate 320 GB hdd. Windows 10 is installed on a 230 GB ssd. I want to remove the NTFS partition on my hdd and allocate it all to ubuntu without messing up the side by side ubuntu/windows 10 installations. I examined the hdd with gparted and it will let me remove the NTFS partition on the 320 GB hdd but for the second operation it wont let me resize the ext4 partition to allocate the rest of the drive for ubuntu. Is there any way to do it safely? I am not a linux pro so I am kind of lost on how to do this correctly. Any help would be much appreciated. :o

---

### Post by CatKiller on 2019-01-06
You can't change a partition that's mounted. You can't unmount your / partition while you're using it.

Boot from the liveUSB and do it from there.

It's safer to resize Windows partitions in Windows, and Linux partitions in Linux.

---

### Post by stonerrob420 on 2019-01-06
Thank you very much! It worked great :p

---

