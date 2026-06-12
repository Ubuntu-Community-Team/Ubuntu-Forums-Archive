---
title: "File System Went Read Only On Me"
date: 2006-09-06
forum: General Help
---

### Post by noob_Lance on 2006-09-06
Hey,

My Internal Partition.. went read only on me and i didnt do anything to it to Make it read only.. how can iu change the owner back to me instead of root and make it NOT read only anymore... i need heko. school starts tomorrow and i need VMware to work.. if it helps.. i just moved about 3.6 gigs of songs to my main partition and deleted it. then after it went read only.. 

please i cant figure it out!!!!

~Lance


*Edir... its a fat32 partition..

*EDIT EVEN THE ROOT PARTITON IS READ ONLY wtf!!!!!!!!! :@

---

### Post by Demio on 2006-09-06
Errm, nevermind. If it's fat32 then it has no ownership checks, you should be able to make it writeable....

---

### Post by noob_Lance on 2006-09-06
here is my fstab file

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       0
/dev/hda6       /media/Internal     vfat    iocharset=utf8,umask=000 0 0
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

i know ill have to boot into the live cd to fix it... but what do i have to put in to fix it instead???

---

