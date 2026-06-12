---
title: "Cant install ntfs-3g"
date: 2007-06-15
forum: General Help
---

### Post by caramelsoul on 2007-06-15
I have been reading through the posts to find an answer for this. I tried a guide but i could not progress beyond a certain point. 

The reason i want to install this is so Ubuntu can recognise the hard drives that are in my system.

I think i need help, i have been trying to do this since last night. I even have the book Ububtu for Dummies, lol. I need help, please.

Update : When i try to install it it tells me that i already have the newest version. Bit i cant get the NTFS cofiguration tool.

---

### Post by caramelsoul on 2007-06-15
home@home-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=23add783-ee2a-465f-8acb-643c66b091c1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=d2d2d83c-8749-49eb-84c6-91f2029759bd none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
home@home-desktop:~$

---

### Post by geeforce on 2007-06-15
Hi. I installed the NTFS thing via add/remove software in the application menu. Then I did a restart and my NTFS partition was visible.

Have you already restarted Ubuntu? That's how it worked for me.

---

### Post by caramelsoul on 2007-06-15
Yeah i have already rebooted several times. 

I have looked in the add/remove software menu and cant find it...

---

### Post by caramelsoul on 2007-06-15
OK, going by the guide i get to here....

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=23add783-ee2a-465f-8acb-643c66b091c1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=d2d2d83c-8749-49eb-84c6-91f2029759bd none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

Anyone?

---

