---
title: "[SOLVED] Gutsy grub (and feisty) alters the disk it points to"
date: 2007-10-07
forum: General Help
---

### Post by dredwerker on 2007-10-07
Every time I get a Kernel update it gets the boot partition wrong.

HD0,1 is the correct partition - although I don't remember how i know this.

On my main boot disk I have:

ntfs, ext3(ubuntu root), swap, ext3.

Anyway It changes the partition for booting to HD2,1 everytime Gutsy or Feisty.

---

### Post by dredwerker on 2007-10-07
Here is the fdisk -l output:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=7fd0f7a2-54b3-455a-834f-6de9c2cdb9b6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=1146BED92BDA5DF1 /media/hda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hdb5
UUID=4600895F008956B9 /media/hdb5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=A044C1BA44C19386 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=322f0ea9-d1db-4ed4-85d7-55ee63b0691b /media/sda4     ext3    defaults        0       2
# /dev/sdb5
UUID=FC40C0EC40C0AF28 /media/sdb5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=e153c3d5-3740-45d3-8fad-9bf269083233 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

---

### Post by Bigbluecat on 2007-10-07
You need to set the grub root partition on your menu.lst file.

Open menu.lst in a suitable editor and look for a line starting with groot.

You need to make this groot=hd0,1

---

### Post by dredwerker on 2007-10-07
Does this stop the Kernel updates affecting it? or will it sort itself out now that groot is set.

Thanks BTW.

---

### Post by Bigbluecat on 2007-10-08
This sets the grub root partition to HD1,0. Kernel updates should not longer affect where grub thinks the root parition is. I had the same issue as you when I first started.

See the below link for the best grub reference guide:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by dredwerker on 2007-10-08
Thanks very much for your help :)

---

