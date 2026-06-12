---
title: "fstab - need help adding two hard drives"
date: 2007-09-02
forum: General Help
---

### Post by Robotman on 2007-09-02
After a bit of a [catastrophe]("http://ubuntuforums.org/showthread.php?p=3291458&posted=1"), I had to reinstall Ubuntu on my computer.  Now I need to edit fstab so that my two extra storage drives will mount when the system boots.  Here is what my fstab currently looks like:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=a8460eef-7445-411c-aa58-3fb1621027da /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=db62a564-6475-4a82-8151-7b7f18d3b56d none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```
and here is the info for the two extra drives:
```
dcb6e91e-1a2a-4d29-a243-711d7c9be063
hdd1 - BACKUP

e6c04b3a-9965-40a2-8cf2-32505dbb2d7f
hdb1 - MAIN
```
BACKUP and MAIN are the names I want to give the drives, so that they'll appear that way on the desktop.
I think excluding the UUIDs from fstab was part of the reason I had the aforementioned catastrophe, so I want to include them this time.  What should my fstab look like with the two hard drives added properly?

---

### Post by confused57 on 2007-09-02
See this guide for mounting linux partitions:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
note the info for changing owner

and this guide for mounting with UUID's:
[http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with](http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with)

---

### Post by Robotman on 2007-09-02
I'm still confused.  Would it cause any problems to edit fstab to appear like this?
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=a8460eef-7445-411c-aa58-3fb1621027da /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=db62a564-6475-4a82-8151-7b7f18d3b56d none            swap    sw              0       0
# /dev/hdb1
UUID=e6c04b3a-9965-40a2-8cf2-32505dbb2d7f none            swap    sw              0       0
# /dev/hdd1
UUID=dcb6e91e-1a2a-4d29-a243-711d7c9be063 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```
also, how can I rename hdd1 to BACKUP and hdb1 to MAIN?

---

### Post by confused57 on 2007-09-02
I believe you'll need to make new directories for the mountpoints:
```
sudo mkdir /media/Backup
Sudo mkdir /media/Main
```

Then add these mountpoints to your fstab:
```
# /dev/hdb1
UUID=e6c04b3a-9965-40a2-8cf2-32505dbb2d7f /media/Main           ext3    rw,user             0       1
# /dev/hdd1
UUID=dcb6e91e-1a2a-4d29-a243-711d7c9be063 /media/Backup         ext3    rw,user             0       1
```

Then see the first link I gave you for changing ownership of the drives...this is for mounting ext3 partitions.  For mounting other filesystems:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)
or
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Added:  Here's a howto by bodhi.zazen that explains fstab much better than I can:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by Robotman on 2007-09-02
I added the text you posted, but the drives don't mount automatically when the system boots.  They can't be mounted at all now.  When I try to mount them manually, I get an error message that says "Cannot mount volume.... mount point /media/Backup does not exist"
How can I fix this so that the drives are mounted automatically when Ubuntu boots?
Should I change the term "user" to my own name in fstab?
Permissions are already set by the way.

---

### Post by Robotman on 2007-09-02
:redface:
Disregard that... I missed a step. 
Everything works the way it should now.  Thanks! :D

---

### Post by confused57 on 2007-09-02
> **Robotman said:**
> :redface:
Disregard that... I missed a step. 
Everything works the way it should now.  Thanks! :D

Great, glad it worked...guess you needed to make the directories?

---

### Post by Robotman on 2007-09-02
Yep.
Again, thanks.

---

