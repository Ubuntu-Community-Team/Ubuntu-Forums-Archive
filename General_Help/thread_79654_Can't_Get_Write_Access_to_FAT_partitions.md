---
title: "Can't Get Write Access to FAT partitions"
date: 2005-10-20
forum: General Help
---

### Post by phanboy_iv on 2005-10-20
The other day I created a FAT partition on my HDD to use to transfer files back and forth between my NTFS based Windows XP partition and my Ubuntu partition, since both OS's can read/write to FAT partitions.

I set the FAT partition to mount at boot time and allow all users to read/write as demonstrated in the Ubuntu Starter Guide, except my partition is at /dev/hda2 and I created a directory /sharedFAT and mounted it there instead of at /media/blablabla. 

This is the line I added to /etc/fstab:  

/dev/hda2         /sharedFAT        vfat umask=000       0       0  

Windows can read and write to the FAT partition, but when I try to copy something to it under Ubuntu, I get a "write permission denied". I can see the files, I just can't write to the partition. I tried mounting it at /media/hda2 exactly like the Starter Guide said, but I still can't get write permission. I also tried changing the permissions and owner of the mount folder with sudo, but the system won't let me change it. Can someone help me? I KNOW Linux can write to FAT partitions.

---

### Post by mykey on 2005-10-20
change that line to

/dev/hda2 /sharedFAT vfat defaults 0 0

reboot - should do it

---

### Post by phanboy_iv on 2005-10-21
That did it. Thank you.

---

### Post by liaozi on 2005-10-21
[QUOTE=phanboy_iv]
This is the line I added to /etc/fstab:  

/dev/hda2         /sharedFAT        vfat umask=000       0       0  

[/QUOTE]
my fstab set line:
/dev/hda5 /mnt/C vfat defaults,iocharset=utf8,umask=000 0 0

maybe you try set uid and gid

---

