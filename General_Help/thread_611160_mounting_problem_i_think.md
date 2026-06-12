---
title: "mounting problem i think"
date: 2007-11-12
forum: General Help
---

### Post by skinsfan317 on 2007-11-12
some help me please.. i dont really know what i did.. but i was in rythmbox when all of a sudden my songs started to delete themselves.. all of them. and then when i saw my desktop, my windows mounted drive wasnt there. i use windows as my primary os, and just installed ubuntu. how do i get things back to normal

---

### Post by taurus on 2007-11-12
Things back to normal as in remounting your windows partition!

How did the windows partition get mounted in the first place?  Can you post

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
mount
```

---

### Post by skinsfan317 on 2007-11-12
this is what came up when i ran that

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14122   113434933+   7  HPFS/NTFS
/dev/sda2           14123       18742    37110150   83  Linux
/dev/sda3           18743       19452     5703075   82  Linux swap / Solaris

---

### Post by taurus on 2007-11-12
What about the outputs of the last two commands?

---

### Post by skinsfan317 on 2007-11-12
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=d1bf33aa-3aca-439f-9f39-aac47473225f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=4468E62A68E61B06 /media/Windows  ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=4113fd3d-8da3-4968-99a7-3797f1e714e8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)

---

### Post by taurus on 2007-11-12
What happens when you run this command from a terminal?

```
sudo mount -t ntfs /dev/sda1 /media/Windows
```

---

### Post by skinsfan317 on 2007-11-12
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/Windows -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/Windows ntfs-3g defaults,force 0 0

---

### Post by taurus on 2007-11-12
Knew it.  You need to boot into windows and run a scandisk to fix your windows partition first if you wish.  However, you MUST shutdown windows cleanly.  This means no hibernation crap.

Now, boot back into Ubuntu and see if windows is now mounted to /media/Windows from /etc/fstab.

```
df -h
```

---

### Post by skinsfan317 on 2007-11-12
this is what i got

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              35G  4.9G   29G  15% /
varrun               1013M   88K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M   80K 1013M   1% /dev
devshm               1013M   16K 1013M   1% /dev/shm
lrm                  1013M   34M  979M   4% /lib/modules/2.6.22-14-generic/volatile

---

### Post by taurus on 2007-11-12
Already booted into windows and shut it down cleanly before you rebooted into Ubuntu?

---

### Post by skinsfan317 on 2007-11-12
yea but ill trry it again

---

### Post by skinsfan317 on 2007-11-12
o it worked thanks so much

---

