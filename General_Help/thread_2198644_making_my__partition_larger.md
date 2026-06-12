---
title: "making my / partition larger?"
date: 2014-01-09
forum: General Help
---

### Post by sketchy1poker on 2014-01-09
this is a screenshot of my partition table in gparted

[IMG]http://i149.photobucket.com/albums/s59/sketchy1poker/gpartedtable_zps8b0bd84e.jpg[/IMG]

i want to do the following

A) get rid of any unnecessary ntfs/fat32 partitions from windows that aren't absolutely necessary to boot into windows 8.1 right now. so i am assuming the lenovo ntfs on /dev/sda11 is good to go, along with the recovery ntfs on /dev/sda6. the hidden ntfs/fat32 partitions i am questionable on, and i am keeping the windows partition on /dev/sda5 for the time being (until i am 100% sure i no longer need windows).

B) take the unallocated 200gb that i took from the windows partition that i should have just taken initially when forming my linux partitions, but didn't for whatever reason, and add it to my / partition on /dev/sda7 (or should i put it on sda8?? i am not sure). i finally got done cloning all of my ntfs/fat32 partitions onto an external hard drive today, and took the extra space from the windows partition seeing that i wanted more space for linux to operate/store files.

C) figure out how to take all of those extra gigabytes from the unneeded recovery partitions that i am getting rid of from part A and add them to my linux partition as well.

thanks in advance!

---

### Post by Impavidus on 2014-01-10
Better keep sda6 (the recovery partition) until you're sure you want to get rid of Windows. I don't know the purpose of most Windows partitions. sda2 is your /boot/efi partition, which is used by Ubuntu too. sda10 doesn't contain much useful, so, if you've got a backup on the external drive it must be safe to delete. Most of the others are quite small compared to the size of your drive, so don't bother until you want to get rid of Windows.

With a separate /home partition you don't need a large / partition. 20GB should be enough, unless you want some programs that come with huge amounts of data (flight simulators, planetarium programs, that kind of stuff). It's best to add the unallocated space to sda8, your /home partition.

Boot from your live disk to modify partitions. Move sda7 to the left. You may want to shrink it a bit in the process. Expand sda8 to the left. If you haven't done a lot yet on your Ubuntu system it will be quicker to make a backup of your /home, delete sda7 and sda8, create new ones to the left, restore the backup of sda8 and reinstall, selecting sda8 for your /home partition without formatting it.

---

