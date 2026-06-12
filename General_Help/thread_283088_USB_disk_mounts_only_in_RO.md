---
title: "USB disk mounts only in RO"
date: 2006-10-23
forum: General Help
---

### Post by vincentb on 2006-10-23
Hi,

I have an USB disk attached to my computer:

[I]root@vincent-ubuntuRC3:/etc# lsusb
Bus 002 Device 002: ID 072f:9000 Advanced Card Systems, Ltd ACR38 AC1038-based Smart Card Reader
Bus 002 Device 001: ID 0000:0000  
**Bus 001 Device 004: ID 1058:0403 Western Digital Technologies, Inc.** 
Bus 001 Device 001: ID 0000:0000  [/I]

It always mount in RO
once I type *mount -a*

then it is mounted in RW and I can delete / update files in this disk.
My fstab file looks like this:

[I]root@vincent-ubuntuRC3:/etc# more fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=c9b514c5-bd4e-4aa7-9a00-fa678472a066 /               ext3    defaults,error
s=remount-ro 0       1
# /dev/sda1
UUID=54CC6999CC6975E0 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46
 0       1
# /dev/sda5
UUID=A6487F69487F3761 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46
 0       1
# /dev/sda6
UUID=E4088E1B088DECBC /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46
 0       1
# /dev/sda7
UUID=DDE1-8098  /media/sda7     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda9
UUID=725cf7a7-136f-479d-ad77-2c4f22333c3c /media/sda9     ext3    defaults      
  0       2
# /dev/sdb5
UUID=9765d6ce-269e-42f6-8ecf-5fcc7376e0ba none            swap    sw            
  0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
[/I]

Would you know a way to automatically mount this disk in RW?
I use Edgy Eft (RC3).

Thanks in advance,
Vincent

---

