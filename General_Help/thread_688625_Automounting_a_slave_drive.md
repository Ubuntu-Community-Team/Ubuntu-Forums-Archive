---
title: "Automounting a slave drive"
date: 2008-02-05
forum: General Help
---

### Post by charlescarroll1 on 2008-02-05
I have an internal slave drive I want to auto-mount at start up instead of mounting it manually every time I start Ubuntu.  

My master drive has Ubuntu and WinXP dual booting.
Heres what I see in fstab...
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=d521d559-7f78-4c5b-94fe-66b36a490312 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=0CB81050B8103AA2 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda3
UUID=78fc3ec4-8528-414c-8339-12020ef88ebe none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


```
The location of SLAVE is /media/SLAVE, and the filesystem is NTFS.
I tried to do it myself, but I failed because I am not too familiar with fstab and gedit.

Hopefully I put enough information in.
Any help or suggestions would be much appreciated.

---

### Post by zarqoon on 2008-02-05
I hope i assume correctly that your "slave" drive is a harddisk connected to the primary ide controller in slave mode this your primary drive beeing on the same cable in master mode and that the name of your partition on the "slave" drive is actually SLAVE.
That would let ubuntu mount it to /media/SLAVE if you click it in nihilus.

If thats all correct do this.
First you have to check which device the partition actually is. This would most likely be /dev/hdb1. Check if this exists if it does it should be it. If not post the outcome of
```
 ls /dev | grep hd 
```
your disc should be one of the results.

The next step is to create a folder to mount the partition on. I prefer a folder in /mnt for this but you can put it wherever you want. You may have to change ownership of the folder to your user if you had to create it with superuser privilegies and if you want to be able to write to the disc with your user. You do this with
```
 chown username folder 
```
After that you have to add a line to your /etc/fstab like this
```
 /dev/hdb1 /somefolder ntfs defaults 0 2 
```
replace /dev/hdb1 with the device name corresponding to your disc and /somefolder with the adress of the folder you created and the disc should mount at every boot from then on. Beware that if your windows did not shutdown clean at the last boot (bluescreen for example) you can not mount the ntfs drives or at least if have not yet figured out how. In that case boot windows and shutdown again.

---

