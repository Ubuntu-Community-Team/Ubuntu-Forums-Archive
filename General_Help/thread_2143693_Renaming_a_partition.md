---
title: "Renaming a partition"
date: 2013-05-09
forum: General Help
---

### Post by rmcellig on 2013-05-09
I have a partition on my drive The partition is sda2. The name of the partition is so long (eb1bb3e4-2004-41f9-90bf-1f942ffc5493). I need to rename it to something simple. Is this possible. This is what the name looks like in my Crontab.

```
rsync -r -t -p -o -g -v --progress --delete -s /media/eb1bb3e4-2004-41f9-90bf-1f942ffc5493/randy/Music/LPs/lps_recent /media/randy/usbdrive
```

Is it possible to use the name sda2 instead of the long name in my Crontab or do I have to rename it to something shorter? Another thing about this partition is that I always have to type a password to access it.

---

### Post by papibe on 2013-05-09
Hi rmcellig.

That looks like that partition is being automounted using that name, isn't it?

It looks like the partition does not have a label and is being mounted using its 'ugly' UUID.

I would try to set a label using 'Disk Utility'.

First, close all apps that are using that partition, and then unmount it. Open 'Disk Utility'. Select the disk, then the partition, on the right, and then press 'Edit Fylesystem Label' on the left.

Remount your partition.

Let us know how it goes.
Regards.

---

### Post by rmcellig on 2013-05-09
Thanks. I renamed my partition part2. It shows up in Thunar. Can I use the label in my crontab now instead of the long name I used before? How do I get around always having to type in a password when I initially select the partition? Is there maybe a way of doing this without having to go to the terminal?

---

### Post by papibe on 2013-05-09
Glad you are making progress.

You should be able to double click it on Thunar,  and with no password asked, it should be automount under /media using its new label.

Does that work?

Regards.

---

### Post by rmcellig on 2013-05-09
No. I still get prompted to enter my password.

---

### Post by ajgreeny on 2013-05-09
What filesystem does that partition use?
ext#, ntfs, fat32?

---

### Post by rmcellig on 2013-05-09
Here is the detail info on that partition.

---

### Post by papibe on 2013-05-09
Could you post the result of these commands?
```
cat /etc/fstab 

sudo fdisk -l

sudo blkid 
```
Regards.

---

### Post by rmcellig on 2013-05-09
```
root@debxfcev6:/home/randy# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda4 during installation
UUID=cc00455e-a42a-44d0-b016-4b65a8a1e0ca /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=eca5eb5f-6b0d-4c7c-9a2a-316ced0ce062 none            swap    sw              0       0
/dev/sr0        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

```
root@debxfcev6:/home/randy# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000be815

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    84004863    42001408   83  Linux
/dev/sda2        84004864   866899967   391447552   83  Linux
/dev/sda3       969631744   976773119     3570688   82  Linux swap / Solaris
/dev/sda4       866899968   969631743    51365888   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000204885504 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000157d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1953523711   976760832   83  Linux

```

```
root@debxfcev6:/home/randy# blkid
/dev/sda1: UUID="a3a60cbc-7354-43d1-a88b-2314723bb8a4" TYPE="ext4" 
/dev/sda2: UUID="eb1bb3e4-2004-41f9-90bf-1f942ffc5493" TYPE="ext4" LABEL="part2" 
/dev/sdb1: LABEL="usbdrive" UUID="c9b227db-0489-4454-978b-97581745ade9" TYPE="ext4" 
/dev/sda3: UUID="eca5eb5f-6b0d-4c7c-9a2a-316ced0ce062" TYPE="swap" 
/dev/sda4: LABEL="debian_xfce" UUID="cc00455e-a42a-44d0-b016-4b65a8a1e0ca" TYPE="ext4" 
```

---

### Post by papibe on 2013-05-09
Thanks.

First, unmount the partition in question.

Second, create the mount point:
```
sudo mkdir /media/usbdrive
```
Then, add these lines to the /etc/fstab:
```
# Manual mount point for partition label "usbdrive" (/dev/sda2).
UUID="eb1bb3e4-2004-41f9-90bf-1f942ffc5493"    /media/usbdrive    ext4    defaults,noauto    0    0
```
(the noauto option only makes the system aware of the mounting rule, but it avoid automatic mount).

Then either reboot, or run this command:
```
sudo mount -a
```
Now test if you can double click the partition in Thunar so it gets mounted without a password.

Hope it helps. Let us know how it goes.
Regards.

---

