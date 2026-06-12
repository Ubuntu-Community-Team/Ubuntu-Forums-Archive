---
title: "cannot edit files on second hard drive."
date: 2007-06-15
forum: General Help
---

### Post by bohica8418 on 2007-06-15
I am a noob on linux and therefore ubuntu. I carefully organized all my documents under windows and put them on a second hard drive, now however i cannot edit the files in any way and am told they are read only. i can listen to the music and watch the videos contained there, but i want to create a new folder and put new items onto the drive and cannot. I beleive that it is a permission issue, but i do not know how to address it. 
Thanks in advance for your help!

---

### Post by NeoLithium on 2007-06-15
Open up a terminal window (Applications -> Accessories -> Terminal) and type the following command: ```
cat /etc/fstab
``` and copy and paste it here.  What mount point is it as well?

---

### Post by bohica8418 on 2007-06-15
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc2
UUID=bcbdfc42-23ee-4f52-86b2-9b4b90725dd3 /               ext2    defaults,errors=remount-ro 0       1
# /dev/hdc1
UUID=F80028FE0028C60A /media/hdc1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=E6D83BDCD83BAA27 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdc5
UUID=303e99c4-0914-430a-826e-0e06cb08ee5d none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0



And um im sorry i dont know what a mount point is... give me a few minutes to look what it is up and ill tell you!

---

### Post by bohica8418 on 2007-06-15
computer:///Berkeleys Documents    is that the information you needed?

---

### Post by NeoLithium on 2007-06-15
This walkthrough should help you out for reading/writing on NTFS partitions :
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

Hope it helps! :)

---

### Post by bohica8418 on 2007-06-15
Yes Thank you very much Neolithium!

---

### Post by NeoLithium on 2007-06-15
You're very welcome :)

---

