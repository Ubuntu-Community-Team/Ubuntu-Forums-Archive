---
title: "need help installing and running programs from removable media"
date: 2008-05-04
forum: General Help
---

### Post by jorik42 on 2008-05-04
ok, so i have read that it is possible to install and run programs from removable media (flash drives, sd cards, ect).  so i gave it a shot, seeing as my eeepc doesnt have alot of hard drive space.  installing seems to go fine; i declare the destination folder to be a location on the removable disk (in this case, /media/disk).  but i cannot run programs from the disk.  whenever i try, i get an error that says something like "error while loading shared libraries.."  specifically, in this instance, i have installed matlab to my sd card; when i attempt to run it, i get the following:

/media/disk/matlab/bin/glnx86/MATLAB: error while loading shared libraries: libicudata.so.32: cannot open shared object file: No such file or directory

i get similar errors for other programs that i try to run...any ideas?  

thanks
jorik

---

### Post by sekinto on 2008-05-04
Maybe the program is looking for files it uses in the wrong directory, instead of looking in /media/disk/... it is probably looking in /usr/... To solve this you could make a link in /usr/... linking to /media/disk/...

---

### Post by bodhi.zazen on 2008-05-04
Another thought is your removable media is mounted noexec.

In this case, edit /etc/fstab, add exec to the options, and re-mount.

Other option is to copy the files to /home or try sh

```
sh /media/cdrom/application
```

---

### Post by jorik42 on 2008-05-05
so, i went to edit my /etc/fstab as suggested, but, as far as i can tell, the disk (/media/disk) isnt even in there..

cat /etc/fstab shows:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=14c15153-898d-4d9c-b8c1-7808303fc0fd /               ext3    defaults,errors=remount-ro 0       1


which shows my /proc and /dev/sda1 drives, but no others.  any ideas?  am i reading this wrong?

jorik

---

