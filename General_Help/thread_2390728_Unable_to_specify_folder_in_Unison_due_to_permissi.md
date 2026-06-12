---
title: "Unable to specify folder in Unison due to permissions error."
date: 2018-05-01
forum: General Help
---

### Post by completeeclipse on 2018-05-01
Hello everyone, thank you for taking the time to read my question,

As the title says, in the Unison profile creator when I try to specify a folder which is located on a hard drive existing in an external bay I get an error stating "Error opening directory '/mnt': Permission denied" I am trying to sync the root of this drive with a folder on a drive that I will use specifically for backups also mounted under /mnt. Currently the permissions of /mnt are Owner= root rw Group=www-data rw and Others are read only. My local user is part of the www-data group. My fstab file is as follows. Any assistance to with this probably obvious error is greatly appreciated. 

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=d7226881-6034-435d-8dcf-28cc68a627e7 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=C448-08A2  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda7 during installation
UUID=3cd5090d-bd31-4acf-b3f2-8ada04841a31 none            swap    sw              0       0
/dev/disk/by-id/usb-WDC_WD40_EFRX-68N32N0_152D00539000-0:2-part1 /mnt/usb-WDC_WD40_EFRX-68N32N0_152D00539000-0:2-part1 auto nosuid,nodev,nofail,x-gvfs-show 0 0
/dev/disk/by-id/usb-WDC_WD20_EARS-00S8B1_152D00539000-0:1-part1 /mnt/usb-WDC_WD20_EARS-00S8B1_152D00539000-0:1-part1 auto nosuid,nodev,nofail,x-gvfs-show 0 0
/dev/disk/by-id/usb-SAMSUNG_HD103UJ_152D00539000-0:0-part1 /mnt/usb-SAMSUNG_HD103UJ_152D00539000-0:0-part1 auto nosuid,nodev,nofail,x-gvfs-show 0 0

```

---

