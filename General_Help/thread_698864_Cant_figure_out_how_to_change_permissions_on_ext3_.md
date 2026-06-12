---
title: "Cant figure out how to change permissions on ext3 partition..."
date: 2008-02-16
forum: General Help
---

### Post by NoSmokingBandit on 2008-02-16
I have a new ext3 partition but for the life of me i cant get read/write permission on it.
Heres my fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=386784dc-7adc-4a9c-a083-254fd6bce53d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=1f842ab9-38b7-4828-9f29-9de75263a446 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```
I have no idea what any of that means. Its the 2nd partition on my drive, so there should be a "sda2" somewhere in there but there isnt. When i right click->properties on the drive and check the Volume tab it says it is mounted in /media/disk. Like i said, im lost. Any help?

---

### Post by sisco311 on 2008-02-16
please post the output of the command: 
```
sudo fdisk -l
```

---

### Post by NoSmokingBandit on 2008-02-16
```

Disk /dev/sda: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         608     4883728+  83  Linux
/dev/sda2             609        3616    24161760   83  Linux
/dev/sda3            3617        3738      979965   82  Linux swap / Solaris

```

---

### Post by disturbedite on 2008-02-16
if you're trying to do this with gparted or qtparted, take note that the partition you want to modify must not be mounted...

---

### Post by sisco311 on 2008-02-16
yes it's sda2

1.) create a mount point:
```
sudo mkdir /media/my_disk
```2.) get the uuid of your partition:
```
sudo vol_id /dev/sda2
```3.) edit your fstab:
```
sudo gedit /etc/fstab
```> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=386784dc-7adc-4a9c-a083-254fd6bce53d / ext3 defaults,errors=remount-ro 0 1
# /dev/sda3
UUID=1f842ab9-38b7-4828-9f29-9de75263a446 none swap sw 0 0
[B]#/dev/sda2
UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx /media/my_disk ext3    defaults        0       2[/B]

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0replace **xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx** with the uuid you get from 2.)

4.) to get write permission chown the mount point:
```
sudo chown -R **your_username:your_grup** /media/my_disk
```by default **your_group** is your user name:

```
sudo chown -R **your_username:your_username** /media/my_disk
```5.) remount the partitions:
```
sudo umount /dev/sda2
sudo mount -a
```done

---

### Post by NoSmokingBandit on 2008-02-16
Awesome, worked perfectly, thank you so much! :guitar:

---

### Post by photopath on 2008-05-03
That one had me stumped for a while too.

SOOOOO obvious once someone pointed me in the right direction! :KS

---

### Post by texasone on 2008-06-13
ok. This worked perfectly.  the only problem is umount via GUI.  It works fine using **sudo umount dev/sdxy**, but when I try to unmount the drive using right-click option on the desktop, it always says that I need to have root options.  any ideas, if not, i can just use terminal for unmounting the drive.

---

