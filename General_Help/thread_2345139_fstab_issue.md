---
title: "fstab issue"
date: 2016-11-30
forum: General Help
---

### Post by rgsara on 2016-11-30
I have ubuntu 16.10, which automounts a HDD (called bigdisk) on startup to /media/richard/bigdisk. The disk is in an array of 4 disks in an Acer AC100 server which are hot swappable (but not set up as raid).
I want to change the mountpoint , so using /dev/sdx in fstab wont work as the discs seem to be automounted in random orders, ie bigdisk is sometimes sda, sdb.
I have read the fstab tutorials here and tried to follow the instructions but I am making some, probably stupid, error.  Here are the relevant lines from fstab:

#bigdisk mounted at /home/richard/bigdisk
UUID=8b86039f-a284-4693-81e9-f341f3f113ba       /home/richard/bigdisk   ext4   user,auto,noexec,utf8    0       0

something is wrong, the system wont boot with these settings or any similar settings (changing mountpoint, changing options)
All suggestions welcomed.
Thanks in advance.

---

### Post by papibe on 2016-11-30
Hi rgsara.

Could you post the content of your current /etc/fstab, and also run these commands, and post back the results?
```
sudo blkid 

lsblk 
```
Regards.

---

