---
title: "Permissions for fat32 partition"
date: 2005-06-03
forum: General Help
---

### Post by artinla on 2005-06-03
I have a second hd with a fat32 partition.  I edited my fstab with the following line to mount it:

/dev/sdb1     /media/windows  vfat    defaults,user,auto  0  0

Now I can read it, but can only write to it as a super user.

When booting, the following lines are displayed:

mounting local filesystems
/dev/sdb1  /media/windows  rw,noexec,nosuid,nodev

What do I need to do so that I can paste files to it in nautilus without having to use sudo to start it?

Thanks,

Art

---

### Post by bored2k on 2005-06-03
Change your sdb1 line in /etc/fstab with this one:

> 
/dev/sdb1       /media/windows  vfat    umask=000       0       0

Or
> sudo mount /dev/sdb1 /media/windows/ -t vfat -o umask=000
[http://ubuntuguide.org/#mountunmountfat](http://ubuntuguide.org/#mountunmountfat)

---

