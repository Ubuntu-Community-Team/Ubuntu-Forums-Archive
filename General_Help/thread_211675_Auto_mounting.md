---
title: "Auto mounting?"
date: 2006-07-08
forum: General Help
---

### Post by boom2k1 on 2006-07-08
How do you configure Ubuntu to automount when a USB storage device is detected?

I remember when I first installed Ubuntu, it automatically detects my USB drive and camera and mounts it. 

Now, I still see the drive in "Computer". However, I cannot mount it because I am not the root user, so everytime I have to go into sudo nautilus, enter password,  and then double click the computer to mount it from there.


Thanks!

---

### Post by scxtt on 2006-07-08
System --> Preferences --> Removable Drives and Media

---

### Post by boom2k1 on 2006-07-08
The problem is, I already have the first 3 options selected, but it still doesn't automount.. Why?

Mount Removable drives when hot-plugged
Mount removable media when inserted
Browse removable media when inserted


Would it be because of this in my /etc/fstab?
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda10      /documents      vfat    iocharset=utf8,umask=000,shortname=winnt/dev/hda8       /home           ext3    defaults        0       2
/dev/hda2       /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0
   1
/dev/hda5       /windowsStorage ntfs    defaults,nls=utf8,umask=007,gid=46 0
   1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1       /PrimaryStorage vfat    iocharset=utf8,umask=000,shortname=winnt

```


Thanks!

---

### Post by boom2k1 on 2006-07-08
I have an external harddrive (enclosure):  And I gave it the name primarystorage
(see above)


I only have my ipod connected right now
When I double click on that ipod drive in "Computer":

Unable to mount the selected volume.
mount: only root can mount /dev/sda1 on /primarystorage


It is detected as sda1 too!

---

### Post by scxtt on 2006-07-08
from what i understand, this only applies to items which are mounted to /media/<mount_folder> ... so that fact that you're mounting things to / looks to be messing it up ...

---

