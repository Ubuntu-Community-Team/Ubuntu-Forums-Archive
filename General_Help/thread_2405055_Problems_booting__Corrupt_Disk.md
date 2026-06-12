---
title: "Problems booting / Corrupt Disk"
date: 2018-10-31
forum: General Help
---

### Post by Chanester on 2018-10-31
Having a problem with my main hard disk


When I tried to switch on tonight and couldn't boot to ubuntu and was presented with `grub rescue` due to a bad sector.
I tried `insmod normal` but that wouldn't run with the same bad sector error.


So I booted from a usb and ran `fsck` on the drive, there were a few errors and I y them all.


Tried to boot again, grub rescue again this time `insmod normal` cannot find files.


Back to the usb boot and I run 
```
mkdir /mnt/hdd
sudo mnt /dev/sda1 /mnt/hdd

```

But there doesn't seem to be any files in there.


I check the disk utility and its showing the disk as 86% full.


How do I get back up and running with my data?

---

### Post by oldfred on 2018-11-02
In Disks and upper right corner icon is Smart Status. It can run lots of tests, but all I know is if drive is good or bad. 

Did you run full fsck on all ext4 partitions?
 To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

