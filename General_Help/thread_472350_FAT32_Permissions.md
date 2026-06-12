---
title: "FAT32 Permissions"
date: 2007-06-12
forum: General Help
---

### Post by golf22r on 2007-06-12
Hi, I have a FAT32 external HDD.  I need to change the permissions of this HDD, but as it is a FAT32 drive, I do not know how to change it.  Does anybody know how to change the permissions of this type of drive?  Thank you!

---

### Post by merlinus on 2007-06-13
How is it mounted in /etc/fstab?

-merlin

---

### Post by Patrick K on 2007-06-13
I don't have external HDD but for my FAT32 partitions I changed (or added as needed) UID to 1000 (UID=1000). I am now the proud owner of all my partitions/drives. No more permission problems. 

Here is an example:
# /dev/sda1
UUID=4598-9D46  /media/C        vfat    defaults,utf8,umask=007,uid=1000,gid=46 0       1

How well this will work for an external, I don't know.

---

### Post by golf22r on 2007-06-13
The drives are mounted in /media/disk, there is no information listed on the external drives in /etc/fstab.  Where would I find the mount options for the Disks?

---

### Post by ikonia on 2007-06-13
fat32 as a file system doesn't actually support permissions, only the inital mount permissions may be set.

---

