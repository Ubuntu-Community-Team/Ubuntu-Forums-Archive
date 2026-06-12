---
title: "Reformatted an NTFS to ext3--now getting an &quot;8&quot; error code from fsck??"
date: 2006-12-23
forum: General Help
---

### Post by wilberfan on 2006-12-23
I just converted an NTFS partition (that I had used to screw around with a Vista beta).  Using gparted I deleted it, recreated it, and reformatted it as ext3.

I changed my fstab to reflect that it was now a different kind of partition.   (I also changed the permissions, etc.)

It mounts OK, but I get an error code: "8"  for that partition from fsck?  (I think I'm remembering that correctly...)

How can I repair this?

---

### Post by taurus on 2006-12-23
What does your /etc/fstab look like then?

Applications -> Accessories -> Terminal
```
cat /etc/fstab
```

---

### Post by wilberfan on 2006-12-23
> **taurus said:**
> What does your /etc/fstab look like then?

Applications -> Accessories -> Terminal
```
cat /etc/fstab
```

Voila:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=56cc28c4-c1e3-4db1-b6aa-d5591a64aa63 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda7
UUID=0886b29a-a615-4eca-88b1-47b02a79a879 /home           ext3    defaults        0       2
# /dev/sda1
UUID=AA806D0D806CE0F5 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=B1A2-2BC5  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=78B0A359B0A31D1E /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=4defc807-fa96-4551-9f41-0baead72fc7b /media/sda8     ext3    defaults        0       2
# /dev/sdb5
/dev/sdb5 /media/sdb5     ext3    defaults        0       2
# /dev/sdb1
/dev/sdb1 /media/sdb1     ext3    defaults        0       0
# /dev/sda10
UUID=6d65406b-dda7-489a-9cf8-20286e13445b none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
#mount samba share from DELL
//DELL-Ubuntu/DellFiles /media/dellshare cifs credentials=/root/.smbcredentials,file_mode=0777,dir_mode=0777 0 0




sdb1 is the partition I reformatted, and I believe that's kicking out the error...

---

### Post by taurus on 2006-12-23
Which ext3 partition is giving you a problem?  And by the way, I recommend you change the last value from "1" to "0" for ntfs & vfat partitions...

---

### Post by wilberfan on 2006-12-23
Gawd, it's so hard to be a n00b sometimes...

The partition spitting out the error was sda8...it was my old Dapper root or home partition--and I reformatted it in anticipation of...I don't know...Feisty?

I commented out the line in the fstab--which made everything peachy--but I'd like to understand what the error was about...    It said something about "unresolved..." something...  It was probably used to seeing "Dapper" data there and got concerned when it turned up missing?

Thanks for the tip about 1's and 0's....is there an easy explanation for what those suckers *mean??*

---

### Post by taurus on 2006-12-23
Maybe gparted screwed up the /dev/sda8!  If there is no data on it, why not format it again from a terminal, assuming it's not mounted right now because you can't format a partition when it's mounted...

```
sudo mke2fs -j /dev/sda8
sudo mount -t ext3 /dev/sda8 /media/sda8
```
Also, if you keep formatting the drive, it's better to replace the "UUID=" with the actual parition.  Therefore, replace this line in /etc/fstab

```
 UUID=4defc807-fa96-4551-9f41-0baead72fc7b /media/sda8 ext3 defaults 0 2
```
with

```
/dev/sda8   /media/sda8   ext3   default   0   2
```

---

### Post by wilberfan on 2006-12-23
Duuuuuuuuude!   That was _mega_ helpful!    Everything booted OK (no errors), and the little sucker  is sittin' there all mounted and warm on the desktop!  8) 

If I don't WANT it mounted (I've got a LOT of disc icons on my desktop!) do I just comment it out of the fstab?   Or is there a better way to do that?

Thanks again for your oh-so-helpful advice!  :D

---

### Post by taurus on 2006-12-23
Just unmount it from a terminal with

```
sudo umount /dev/sda8
```
But of course, it will be mounted again next time you boot...  If you don't want it to mount automatically upon boot, then comment it out by placing a # in front of it.  And if you want to mount it so you can use it, then mount it by hand from a terminal!  ;)

---

### Post by zekopeko on 2006-12-23
try searching the forums for more info.

but  i believe that it is an option in gconf-editor(this you type in terminal to start the editor) under  apps > nautilus.

there is also a disk mounter applet for the panel. just right click on a panel, Add to Panel and then look for Disk Mounter. it works only for NTFS/FAT formated drives.

---

