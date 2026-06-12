---
title: "Why is auto-mounting a network share on boot so difficult?"
date: 2006-07-08
forum: General Help
---

### Post by zhenya on 2006-07-08
I've spent too much time on getting this to work properly already, but it's something I'd really like to have working.

I have a ubuntu server that shares files to all the computers in the house via Samba.  Samba won't mount automatically for me on my Dapper desktop.  My fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda2 /media/ipod vfat user,noauto,umask=000 0 0
//FileServer/250share /media/250share smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777,noauto 0 0 
//FileServer/160Share /media/160share smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777,noauto 0 0

```

If I remove the noauto option, the boot stalls for several minutes at "starting hardware abstraction layer hald" and doesn't mount them anyways.  With the noauto option I can mount them manually no problem.

I then spent several hours attempting to do the same thing via sshfs.  Again, I can mount them manually, but if I change my fstab to this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda2 /media/ipod vfat user,noauto,umask=000 0 0
sshfs#FileServer:/media/250Share /media/250share fuse defaults 0 0 

```

again, it doesn't mount automatically, although it doesn't return any errors either.  It just doesn't actually show me my files (although it apparently mounts, as I have to unmount it manually).

Is there any other way I might go about mounting these shares automatically?  Anyone have any suggestions for Samba or sshfs?

Thanks!

---

### Post by Thund3rstruck on 2006-07-08
I'm mounting to a Win2003 server and I noticed 2 things on this. I know you're host via smb so this may not apply but;

1. At least in my environment, smbfs will not mount. I have to use CIFS
2. I cannot point to a crudentials file in any home directory. I ended up saving the crudentials file in /etc/.crudentials

---

