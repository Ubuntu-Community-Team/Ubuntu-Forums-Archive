---
title: "problems with lvm automount via fstab"
date: 2014-01-16
forum: General Help
---

### Post by PyrexKidd on 2014-01-16
Hello,

I need help mounting an lvm partition at boot.  I've done this a thousand times, but for some reason I'm doing something wrong...

I can mount the partition directly:

```

root@chef1:~# mount /dev/mapper/VolGroup00-lv--opt /opt/
root@chef1:~# mount | grep opt
/dev/mapper/VolGroup00-lv--opt on /opt type ext4 (rw)
root@chef1:~# umount /opt 
root@chef1:~# mount /dev/VolGroup00/lv-opt /opt/
root@chef1:~# mount | grep opt
/dev/mapper/VolGroup00-lv--opt on /opt type ext4 (rw)
root@chef1:~# umount /opt

```

But when I attempt to mount via `mount /opt`, or at boot time, I get an error:

```

root@chef1:~# mount /opt
mount: wrong fs type, bad option, bad superblock on /dev/mapper/VolGroup00-lv--opt,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Here is my fstab, the commented out lines are other failed iterations I've attempted:

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=4e86f9a9-b9af-4259-8c37-d17540400d70 /               ext4    errors=remount-ro 0       1
/dev/mapper/VolGroup00-lv--opt /opt     ext4    error=remount-ro        0       2


# failed iterations
#/dev/VolGroup00/lv-opt /opt    ext4    default 0       2
#/dev/VolGroup00/lv-opt /opt    ext4    default 1       2
#/dev/VolGroup00/lv-opt /opt    ext4    error=remount-ro        0       2
#/dev/mapper/VolGroup00-lv--opt /opt    ext4    default 0       2
#/dev/mapper/VolGroup00-lv--opt /opt    ext4    default 1       2

```

What am I doing wrong?

Thanks, I appreciate the assistance.

EDIT: IF it makes a difference, Ubuntu 13.10 x86_64

```

root@chef1:~# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 13.10
Release:        13.10
Codename:       saucy
root@chef1:~# uname -a
Linux chef1 3.11.0-14-generic #21-Ubuntu SMP Tue Nov 12 17:04:55 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by PyrexKidd on 2014-01-20
"defaults" not "default"

---

