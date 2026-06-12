---
title: "only root can mount/umount"
date: 2007-10-29
forum: General Help
---

### Post by natsbar on 2007-10-29
Ok, the only way I can mount or unmount a drive is as root or with sudo, which makes it pointless to be able to right click on the drive's icon which is right on the desktop and choose to mount or unmount.  I want to be able to mount or unmount as a user.  I did my research and added the "user" option to my fstab, and I rebooted.  What am I missing to give the user permission to mount the drive.  /dev/hda2 is the only drive I want like this, /dev/hda1 is shut down intentionally.  Here is my /etc/fstab with the /dev/hda2 line separated for clarity:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda4
UUID=cf05a560-d8f4-43a6-a86c-8171104f70ad /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=5A20F05F20F04393 /media/hda1     ntfs    noauto,noexec,umask=007,gid=46 0       1

# /dev/hda2
UUID=CE702BE0702BCE51 /media/hda2     ntfs    user,umask=007,gid=46 0       1

# /dev/hda3
UUID=0b95f542-2f81-4686-bbc3-47393cff6cd1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0



Thank you in advance for your help.

---

### Post by natsbar on 2007-10-29
Changed the "user" to "users", but that was only a partial fix.

Now I can unmount /dev/hda2, but I still can't mount it.

Any ideas how to fix this one?

Thanks again for the help in advance.

---

