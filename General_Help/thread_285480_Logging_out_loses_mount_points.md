---
title: "Logging out loses mount points"
date: 2006-10-26
forum: General Help
---

### Post by rianquinn on 2006-10-26
When ever I look out, my mount point (other harddrives disappear). 

Not sure why?

Kubuntu Edgy, Brand new install

---

### Post by chippy99 on 2006-10-26
Does the file /etc/fstab have all of your mount points defined in it ? If not you will have to edit it. Read the man pages on fstab for guidance.

---

### Post by rianquinn on 2006-10-27
Yes it has all of the mount points

---

### Post by rianquinn on 2006-10-27
Another thing I noticed is if I restart X (ctrl+alt+backspace) I the mount points are fine. Its only when you log out.

---

### Post by chippy99 on 2006-10-27
So what are you doing. Do you remount the partitions manually ? It still sounds like a problem with fstab.

---

### Post by rianquinn on 2006-10-28
Currently I am doing nothing. Not sure what I should do to fix the problem.

Here is my fstab

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=deceb96d-fff6-4bf3-ade1-d777dd58a8f9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=e867d64a-9d44-4021-91c8-6b649eff7335 /home           ext3    defaults        0       2
# /dev/sda1
UUID=1AD00756D0073791 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb1
UUID=880D-74CA  /media/sdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdc1
UUID=44A9-397B  /media/sdc1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=4ea055e9-dbc6-4881-8b2d-f1deda962bb8 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


```

---

### Post by rianquinn on 2006-10-28
nobody else has this problem?

---

### Post by rianquinn on 2006-10-30
Not sure why but I removed the UUID things from my fstab and replaced them with the actualy device name and everything is working fine. 

I have never seen these UUID things before. I am assuming they are new to Edgy. I'm not sure if they are working right.

---

### Post by timbonz on 2006-10-30
mmm first post and it's about a problem....

Yep I'm having this issue too, using kubuntu and if I log out then back in or my wife log's in after me any drives are umounted which is a real pain as we have our desktop backgrounds in /media/files (hda7) and root is hda4.

My question is what is umounting the it?  And why?

Regards
Tim
:cool:

---

### Post by chippy99 on 2006-10-30
Seems to be a known bug have look at [http://www.ubuntuforums.org/showthread.php?p=1301131]("http://www.ubuntuforums.org/showthread.php?p=1301131")

---

