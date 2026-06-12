---
title: "partimage, boot partition, general partitions, mbr, partition tables"
date: 2006-11-01
forum: General Help
---

### Post by sefs on 2006-11-01
So

I've backed up a boot partition using partimage, i've backed up its mbr with dd, and logical partitions with sfdisk.

I've restored that partition to the boot partition of another drive.  Do I also have to restore the mbr as well? or would this new disk already have its own mbr created by gparted/qparted.  I created the boot partition on the new disk using qparted and just set it to active so far and restored the backed up partition from another boot partition on another disk.

Thanks.

---

### Post by sefs on 2006-11-01
Hi I've managed to get things sorted out I think. but still one remain problem.

I have a partition called hda6 which i mount to /mnt/hda6
and a partition called hdb1 which i mount to /mnt/hdb1

I want hda6 to be able to be r/w to any user that logs onto the system but its not even writable to the main user when I log in, although hdb1 is ... which is a totally differnt disk.

my fstab is below ... maybe it has something to do with my parameters if anyone can see something fishy let me know.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>          <options>                               <dump>  <pass>
proc            /proc           proc            defaults                                0       0
/dev/hda1       /               ext3            defaults,user_xattr,errors=remount-ro   0       1
/dev/hda5       /home           ext3            nodev,nosuid,errors=remount-ro          0       2
/dev/hda6       /mnt/hda6       ext3            defaults,auto,rw,user,errors=remount-ro 0       2
/dev/hdb1       /mnt/hdb1       ext3            defaults,auto,rw,user,errors=remount-ro 0       2
/dev/hda7       none            swap            sw pri=1                                0       0
/dev/hdb5       none            swap            sw pri=0                                0       0
/dev/hdc        /media/cdrom0   udf,iso9660     user,noauto                             0       0
/dev/fd0        /media/floppy0  auto            rw,user,noauto                          0       0

```

---

