---
title: "[SOLVED] mount ntfs and fat32 partitions automatically"
date: 2007-11-19
forum: General Help
---

### Post by motoperpetuo on 2007-11-19
in addition to a 17.86GB ext3 partition on which ubuntu is installed, i have a 51.16GB ntfs partition on which windows XP is installed, and a 4.72GB fat32 partition that i use to for files i access from both operating systems. 

how can i get the fat32 partition and ntfs partition to mount automatically every time i log in to ubuntu? i assume i would do this with some kind of start-up script, but i can't figure out how.

thanks!

---

### Post by taurus on 2007-11-19
You would add two entries in /etc/fstab for your ntfs and vfat partitions.  Post

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by motoperpetuo on 2007-11-20
thanks very much for your reply. i added the following to my /etc/fstab:

# Entry for /dev/sda4 (FAT32 partition)
/dev/sda4 /media/disk fat32

i didn't know what to enter for "options" or "dump" or "pass" so i left those blank. i'm guessing that was wrong, and i'm guessing that i may have screwed up some of what i did enter, too.

the fat32 partition still doesn't mount automatically. when i try to mount it manually through the GUI now, i get an error saying that i don't have permission to do so. that's at least progress...it means the entry in fstab is doing something.

is it easy to say what the correct entry in fstab would be? if not, where's a good place for me to do some reading?

---

### Post by jocko on 2007-11-20
[This may help]("http://easylinux.info/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite"). [And this]("http://easylinux.info/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access").

Make your fstab line look something like this:
```
 /dev/sda4    /media/disk vfat  iocharset=utf8,umask=000  0    0
```
(It should say vfat, not fat32)
Make sure the mount point ("/media/disk") exists. Make it by:
```
sudo mkdir /media/disk
```
To mount it:```

sudo mount -a
```

---

### Post by motoperpetuo on 2007-12-16
I just thought I'd let everyone know that I finally figured this one out. Check out this link:

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

After about a fifteen minute read of the ironically titled section "Mounting partitions manually" I figured out how to get my FAT32 and NTFS partition to mount at login. It's awesome. I'm not even all that smart. You all should be able to figure it out, too.

---

