---
title: "Basic disk display query"
date: 2014-02-22
forum: General Help
---

### Post by AlexHudghton on 2014-02-22
I have Ubuntu 12.04 on 2 systems (both dual boot with a version of Windows)

Laptop
single disk split into 2 WINDOWS and DATA

Desktop

5 disks
O/S
Backup
Film and TV 1
Film and TV 2
Film and TV 3

If I open any utility / application and use the 'open file' aspect of that program then I get this

On the laptop there is only one icon for WINDOWs and one for DATA

On the desktop there are 2 for each of the mounted disks - one shown as mounted, one not.

Why is this?

---

### Post by oldfred on 2014-02-22
How are you mounting drives?

 Mount in /media or /home will show in Nautilus left panel mounts in / or /mnt will not.
So I usually mount in /mnt and link folders back into /home.

      
 Duplicate mounts of partitions in Nautilus left panel
use /dev/disk/by-uuid/xxxxx...
[http://ubuntuforums.org/showthread.php?t=1561929](http://ubuntuforums.org/showthread.php?t=1561929)

Post this:
      
 cat /etc/fstab

---

### Post by AlexHudghton on 2014-02-22
So it's the use of UUID and it's a bug?

/etc/fstab

alex@desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=c031c8f3-b9c5-485a-af9f-d287480debdc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=2c27a986-d38c-4a52-a495-29b28566cf76 none            swap    sw              0       0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=83f00b1c-4dd6-43d8-b27e-9ea73354c68d    /media/Film\040and\040TV\0401    auto    rw,user,auto,exec    0    0
UUID=5AC4FAB2C4FA900D    /media/Film\040and\040TV\0402    auto    rw,user,auto,exec    0    0
UUID=F29426FD9426C3C7    /media/Film\040and\040TV\0403    auto    rw,user,auto,exec    0    0
UUID=5C5CF2585CF22D00    /media/backup    auto    rw,user,auto,exec    0    0

---

### Post by oldfred on 2014-02-22
No, it is the mount in /media. But just changing how UUID is used should solve issue.

I also prefer not to use spaces in my mounts or label or just about anything with Linux. Easier just to use under_score, CamelCase, or justonename. Then you do not have to escape the space or use quotes.

---

### Post by AlexHudghton on 2014-02-23
Thanks for that

As I said the systems are dual boot, so all the disks were already there.

It was easier to 'get round' the naming rather than go through and rename everything

---

