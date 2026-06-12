---
title: "[SOLVED] Ubuntu wont start after moving /tmp"
date: 2008-05-31
forum: General Help
---

### Post by Dusenberg on 2008-05-31
Gutsy 7.10 on laptop
I added new ext2 partition for /tmp to existing system that had /tmp in root ext3 partition, but now can't boot into GNOME. I get "your session lasted less than 10 secs" error and kickout, with ref to it not being able to create something in tmp.
HELP!

System is dual boot with Vista.

What I did:
created new partition in Vista, unformatted
mkfs ext2 filesytem on the partition
changed partition type to 83 using sfdisk as vista had it as fat16
added entry to fstab:
/dev/sda9  /tmp     ext2    defaults   0      2 

If I blank out fstab entry for sda9 system starts perfectly.

Am I missing something obvious -  WHAT???:confused:

---

### Post by quelx on 2008-05-31
Open a terminal window while not using the new /tmp



```
sudo fdisk -l /dev/sda
sudo vol_id /dev/sda9
```

*IF* it says it is **ext2** then copy the UUID from the **vol_id** output and open up your fstab and paste it in the /dev/sda9 line. ie. replace **/dev/sda9** with **UUID=longgobedygookdiskidentifietrstring**

now mount the **/dev/sda9** partition and copy everything in **/tmp** to it.

```
sudo mount -t ext2 /dev/sda9 /mnt
sudo rsync -a /tmp/ /mnt/
sudo umount /mnt
```

and reboot...

---

### Post by Dusenberg on 2008-06-01
Thanks quelx - you solved it!! =D>

---

