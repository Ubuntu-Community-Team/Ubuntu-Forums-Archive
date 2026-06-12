---
title: "Need for partitions in fstab?"
date: 2018-06-24
forum: General Help
---

### Post by Robbyx on 2018-06-24
I have just reinstalled 16.04.4 and have noticed what appears to be a change in the way Ubuntu deals with partition.  I hope you will be able to give me an explanation:

In the past fstab had to have every partition I wished to access.  This time I have not needed to do that. The reinstallation produced the usual short form of fstab ie system, home and swap, as below. All the other partitions are appearing and are accessable in pcmanfm and nautilus.  I have not needed to set them up in fstab. In other words of the 11 partitions shown by blkid  only 3 are in fstab, but all are accessable  via the file managers.   Is this a change in the way Ubuntu loads partitions?

> # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=c2f2cb53-1a03-4d94-8859-6e08f5dd2053 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda7 during installation
UUID=B1BA-7E06  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/sda3 during installation
UUID=bf95a4fd-9e7a-4a06-afed-e82fdb82ac63 /home           ext4    defaults        0       2
# swap was on /dev/sda1 during installation
UUID=82ec0704-5c1e-4b9d-bdcf-4c5fb10cb548 none            swap    sw              0       0

blkid:
dev/sda1: UUID="82ec0704-5c1e-4b9d-bdcf-4c5fb10cb548" TYPE="swap" PARTUUID="00083267-01"
/dev/sda2: UUID="c2f2cb53-1a03-4d94-8859-6e08f5dd2053" TYPE="ext4" PARTUUID="00083267-02"
/dev/sda3: UUID="bf95a4fd-9e7a-4a06-afed-e82fdb82ac63" TYPE="ext4" PARTUUID="00083267-03"
/dev/sda5: LABEL="mydocs" UUID="8d99bfc8-90ab-4488-b7da-87e7676aff19" TYPE="ext4" PARTUUID="00083267-05"
/dev/sda6: LABEL="Data inc AV" UUID="1a2e8d10-7b93-4de1-b551-31db6a621276" TYPE="ext4" PARTUUID="00083267-06"
/dev/sda7: UUID="B1BA-7E06" TYPE="vfat" PARTUUID="00083267-07"
/dev/sdb1: LABEL="XHD_VFAT" UUID="13AC-9C9E" TYPE="vfat" PARTUUID="846a1f97-01"
/dev/sdb2: LABEL="xhd system data" UUID="23fcb4e3-c94e-44de-b7a9-105da58918c6" TYPE="ext4" PARTUUID="846a1f97-02"
/dev/sdb3: LABEL="xhd old bacs" UUID="c99be12f-3a2d-4411-ab7c-5696167482dc" TYPE="ext4" PARTUUID="846a1f97-03"
/dev/sdb4: LABEL="spare4" UUID="84a9cb0b-6006-4996-8b4a-2edc07cc25c4" TYPE="ext4" PARTUUID="846a1f97-04"



---

### Post by deadflowr on 2018-06-24
It's been that way for a long time.
You don't need anything in fstab except what you want to have mounted at start.
I believe it's the udisks utilities that allow you to simply use the file managers to mount anything else you want after start.
Or something in that vein.

---

### Post by again? on 2018-06-24
I think it has to do with the development of GIO and gvfs.
[https://en.wikipedia.org/wiki/GIO_(software)](https://en.wikipedia.org/wiki/GIO_(software))

---

### Post by Robbyx on 2018-06-24
Thank you both for your help.

Robin

---

