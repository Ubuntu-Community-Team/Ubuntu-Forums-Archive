---
title: "Hard disk configuration"
date: 2007-03-30
forum: General Help
---

### Post by Dubstar_04 on 2007-03-30
I'm using 7.04 and think it is just brilliant, i've got mythtv with two tv tuners and it works well and very reliably. The problem i am now experiencing is this:

I setup ubuntu on a 40gb caviar drive with the intention of adding a second later. I have now added the second drive and partitioned it using gparted. it is a 250gb hard disk, with one 50gb partition for holding recorded tv and one 200gb partition for music, films, and picture. 

My first problem is that the partitions are not mounted at boot and have to be manually mounted. The second problem is that i can't rename the partitions.

The partitions are both 32fat, i don't know if this is a good format as i don't really understand the linux partitioning system as i'm still pretty new to linux.

I think i have to edit the fstab file but it looks really complicated to me!!

Any help would be great. 

Cheers Dubstar

---

### Post by taurus on 2007-03-30
If you want to mount them at boot, you need to add entries in /etc/fstab for them.  Open a terminal and post the output of these two commands here.

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by jerryrw on 2007-03-30
If the box is a pure linux box then fat32 is not really the best format.  If you are dual booting with MS then it most like likely is.  For a drive that size it's terribly inefficient though.

---

### Post by JohnPhys on 2007-03-30
Also, fat32/vfat can't hold files that are larger than 4 GB in size.  Depending on how you have your tv recording settings set, you can *easily* go over that for a 2 hour show.  I would recommend jfs or xfs.

---

### Post by Dubstar_04 on 2007-03-31
This is the output from the sudo fdisk -l cat /etc/fstab code:

```
 $ sudo fdisk -l
Password:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4678    37576003+  83  Linux
/dev/sda2            4679        4865     1502077+   5  Extended
/dev/sda5            4679        4865     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        6374    51199123+   b  W95 FAT32
/dev/sdb2   *        6375       30515   193912582+   b  W95 FAT32
$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=14620bd5-0fe1-4ba1-8fc5-e1bad47f6bc3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=a6602a11-fb2c-4b6f-bfde-3b3bd9609d21 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
$ 

```

Thanks for your help in advance.

---

### Post by taurus on 2007-03-31
From a terminal, edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and these two lines to the end of it.

```
/dev/sdb1   /media/sdb1   vfat   iocharset=utf8,umask=000   0   0
/dev/sdb2   /media/sdb2   vfat   iocharset=utf8,umask=000   0   0
```
Save it.  Then, create two new mount points and mount them.

```
sudo mkdir /media/sdb1 /media/sdb2
sudo mount -a
df -h
```

---

### Post by Dubstar_04 on 2007-03-31
Thanks for the help. I've changed the format to a xfs type now as adviced above. should the vfat entry be changed to something else? auto, ext3 ...etc?


```
 $ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4678    37576003+  83  Linux
/dev/sda2            4679        4865     1502077+   5  Extended
/dev/sda5            4679        4865     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        6374    51199123+  83  Linux
/dev/sdb2   *        6375       30515   193912582+  83  Linux
$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=14620bd5-0fe1-4ba1-8fc5-e1bad47f6bc3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=a6602a11-fb2c-4b6f-bfde-3b3bd9609d21 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/sdb1   /media/sdb1   auto   iocharset=utf8,umask=000   0   0
/dev/sdb2   /media/sdb2   auto   iocharset=utf8,umask=000   0   0
$ 
 
```

---

### Post by taurus on 2007-03-31
Then those two lines now need to look like these in /etc/fstab.

```

/dev/sdb1   /media/sdb1   xfs   defaults   0   1
/dev/sdb2   /media/sdb2   xfs   defaults   0   1

```

---

### Post by Dubstar_04 on 2007-03-31
That has worked great. Thankyou. What is they best way to change the permissios of the drive? Also is there any way to change the name of the partitions?

---

### Post by taurus on 2007-03-31
Assuming your login name is **john**, do

```
sudo chown -R **john**:**john** /media/sdb1
sudo chown -R **john**:**john** /media/sdb2
ls -la /media
```

---

