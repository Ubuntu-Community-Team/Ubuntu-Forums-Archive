---
title: "How do i change my mounted partition to read onlY/"
date: 2007-04-21
forum: General Help
---

### Post by fokuslee on 2007-04-21
hi i have a shared fat32 partition between windows and linux i would like to mount it read only sometimes 
in fstab it has umask=000 so anyways 
is it right to use mount -t vfat -o remount,ro /dev/hdb1 /share ? 
hdb1 is the fat32 harddrive 
/share is the mount point 
and after that can i just remount again with rw to have write back? 
i heard some pplz can not get it back to write after mounting it ro so I wanted to ask before hand


on a side note i used gparted live cd to make the fat32 partition initally but somehow linux refuse to mount it bad fs type 
what??? i ended up using fdisk and mkfs.vfat -F 32 /dev/hdb1 (mkdosfs) to redo the partition and now its ok.  can someone explain why?

---

### Post by acormack on 2007-04-21
In Kubuntu you change this using

System Settings, Advanced, Disk and Filesystems

---

