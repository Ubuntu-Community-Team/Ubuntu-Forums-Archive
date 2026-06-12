---
title: "fat32 and binding"
date: 2006-09-03
forum: General Help
---

### Post by LensCap on 2006-09-03
Hi, I'm an old user of ubuntu and just got around to installing it on another machine.  So far so good, but I'm having a problem with using my second hd (fat32 for storage). It's mounted fine and I can read from my normal user, but can't write because it won't let me change the permissions (even with sudo).

Here's my fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb1	/media/storage/	vfat	defaults	0	0	
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/media/storage/Media	/home/willum/Desktop/Media	none	bind	0	0

```
also, I have a folder in the 2nd hd (/media/storage/Media) bound to a desktop folder.  Is this the usual way to do this?

---

### Post by ciscosurfer on 2006-09-03
You can try changing your fstab to look like this```
/dev/hdb1       /media/storage vfat    iocharset=utf8,umask=000,users,user=user,group=group   0       0
``` 
I can mount my vfat file system fine with this line:```
/dev/hdb2       /media/hdb2     vfat    defaults,utf8,umask=007,gid=46 0       1
```As far as mounting drives, it doesn't really matter where you mount them (with a few exceptions)...if you like it mounted to your Desktop, then that's fine.  I usually mount my drives to /media and then set my volumes to be visible in nautilus (this includes the desktop, btw) through the Configuration Editor (gconf-editor).

---

