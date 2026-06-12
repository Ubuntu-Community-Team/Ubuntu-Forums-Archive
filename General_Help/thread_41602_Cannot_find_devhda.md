---
title: "Cannot find /dev/hda"
date: 2005-06-14
forum: General Help
---

### Post by Witchhammer on 2005-06-14
I recently wanted to make a dual-boot out of this Ubuntu system so I fiured checking the disk partitions. When I typed: *fdisk -l* it said: Cannot open /dev/hda

Also I tried searching for this but I couldn't find anything: Whenever I install a Windows thing with wine it shows that I still have WIndows directories (C: and all) on the harddrive but when I checked with cfdisk it didn't list them while it did with fdisk -l (when this was working).

My questions: How do I fix the Cannot open /dev/hda error? How do I permanently delete the Windows Partition? 

Any help would be greatly appreciated!

---

### Post by Alexander Kirillov on 2005-06-14
[QUOTE=Witchhammer]I recently wanted to make a dual-boot out of this Ubuntu system so I fiured checking the disk partitions. When I typed: *fdisk -l* it said: Cannot open /dev/hda

Also I tried searching for this but I couldn't find anything: Whenever I install a Windows thing with wine it shows that I still have WIndows directories (C: and all) on the harddrive but when I checked with cfdisk it didn't list them while it did with fdisk -l (when this was working).

My questions: How do I fix the Cannot open /dev/hda error? How do I permanently delete the Windows Partition? 

Any help would be greatly appreciated![/QUOTE]
 You need to run it as root, via sudo:
sudo fdisk -l

To permanetly delete a partition (if you are certain that you wion't need any files on it), use parted (command line tool), or better yet, install and use Gparted

---

### Post by Witchhammer on 2005-06-14
Yeah I just used the root account and it worked fine :) thanks anways :)

---

