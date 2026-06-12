---
title: "Auto mount disk on boot"
date: 2008-02-02
forum: General Help
---

### Post by Impulse666 on 2008-02-02
Similar problem:
[http://ubuntuforums.org/showthread.php?t=684955&highlight=auto+mount+disk](http://ubuntuforums.org/showthread.php?t=684955&highlight=auto+mount+disk)

I however have a FAT32 drive and couldnt figure out exactly what to put in my fstab...

Disk I want auto mounted (fdisk result):
```
Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0af02e1f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641    b  W95 FAT32

```

cat /etc/fstab result:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=f8b4eb40-d2db-4b58-9230-2273807396ab /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=375fc314-7ece-4563-842f-473102c3bdbb none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

df -h result:

```
 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              49G  6.6G   41G  15% /
varrun                506M   96K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M  116K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile
/dev/sdc1             298G  219G   80G  74% /media/EXTERNAL_
/dev/sdb1             298G   98G  201G  33% /media/INTERNAL

```

Disk name is INTERNAL

---

### Post by Rocket2DMn on 2008-02-02
You will want an entry like this:
```
/dev/sdb1 [mount_point] vfat defaults 0 0
```
Where [mount_point] is where you want it to mount, like /media/internal - the directory must already exist
```
sudo mkdir /media/internal
```

See here for more info - [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

You can edit fstab with
```
gksudo gedit /etc/fstab
```
After editing, mount with 
```
sudo mount -a
```

Where I wrote "default", you can modify this, just look at that link I posted.

---

### Post by antiigrav on 2008-02-02
hi

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

you will want to create the directory for mounting, then give it full permissions.

sudo chmod 777 /media/whatever

---

### Post by Impulse666 on 2008-02-02
thanks both of you!

---

