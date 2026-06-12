---
title: "[SOLVED] FSCK not checking all my partitions"
date: 2008-05-15
forum: General Help
---

### Post by BigSilly on 2008-05-15
Hi there Ubuntu-ites. 

Just noticed today that when Ubuntu (Hardy) performs its fsck check at boot, it isn't performing the check on all my partitions like it used to in Ubuntus past. I have 3 partitions - one main 40gb EXT3 for Ubuntu, a spare 20gb FAT32 for saving stuff, and another 20gb EXT3for Mandriva 2008.

This is my fstab just in case it helps:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e194d288-584e-4342-8711-013ed4b77329 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=c7208c52-e601-11dc-bf2c-fbaa335115b0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

I notice that neither sda5 (my FAT32 partition) nor sda6 (Mandriva) appear in Ubuntu's fstab. Am I okay to just paste them in from Mandriva's fstab, as everything seems correct there (other than the drive names - hda for sda etc)? This is it:

```
# Entry for /dev/hda6 :
UUID=ad86545e-2166-4f82-b985-ce6d8d4e8c97 / ext3 defaults 1 1
none /proc proc defaults 0 0
# Entry for /dev/hda7 :
UUID=c7208c52-e601-11dc-bf2c-fbaa335115b0 swap swap defaults 0 0
# Entry for /dev/hda1 :
UUID=e194d288-584e-4342-8711-013ed4b77329 /media/hd ext3 defaults 1 2
# Entry for /dev/hda5 :
UUID=6A2B-24BB /media/hd2 vfat defaults 0 0
```

Thanks all. Still trying to figure out these things even though I've been using Linux for a while!

---

### Post by TeoBigusGeekus on 2008-05-15
If you want Ubuntu to check your volumes for errors on boot up, you have to replace the last 0 in their fstab entries with 2.

As for your other partitions, adding the mandriva fstab entries won't probably work, as ubuntu might have other mount points for them.
Post us the output of 
```
sudo fdisk -l
```

and

```
mount
```

and we will work it out...

---

### Post by BigSilly on 2008-05-15
Thanks for your reply, Teo. sudo fdisk -l -

```
Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb1d0b1d0

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4510    36226543+  83  Linux
/dev/sda2            4511        9964    43809255    f  W95 Ext'd (LBA)
/dev/sda5            4511        7197    21583296    b  W95 FAT32
/dev/sda6            7198        9827    21125443+  83  Linux
/dev/sda7            9828        9964     1100421   82  Linux swap / Solaris
```

mount

```
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/kproject/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=kproject)
/dev/sda6 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda5 on /media/disk-1 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
```

Thanks again. :)

---

### Post by TeoBigusGeekus on 2008-05-15
Add these lines at the end of your fstab file
```
/dev/sda5     /media/disk-1     vfat     relatime     0     2
/dev/sda6     /media/disk     ext3     relatime     0     2
```

---

### Post by BigSilly on 2008-05-15
That's excellent! Excellent, excellent, excellent!!

Thanks very much. Is it too difficult to point out how you worked that out? Never mind if it is, I'm thrilled either way.

Thanks again! :)

---

### Post by TeoBigusGeekus on 2008-05-15
```
man fstab
```
You, having english as your mother language, will probably understand more than me.

---

### Post by BigSilly on 2008-05-15
> **TeoBigusGeekus said:**
> ```
man fstab
```
You, having english as your mother language, will probably understand more than me.

Ah right. I think I kind of understand that, and it's handy to know for future reference. Thanks again, and see you around the forums!

:guitar:

---

