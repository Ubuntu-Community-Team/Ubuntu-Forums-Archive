---
title: "[SOLVED] Two HDD's sharing uuid and mount path"
date: 2007-11-15
forum: General Help
---

### Post by MachineBucket on 2007-11-15
I'm dual booting XP and Feisty on my laptop. Like previous versions of Ubuntu I've used, it automatically mounts the NTFS partition on boot. I also have a external 100GB USB HDD formatted as NTFS. When I booted with the external drive plugged in it mounted the external drive and ignored the internal HDD. It's easy enough to just mount it through the terminal but I would like fstab to be able to determine that there are two drives and mount them in different directories. I found that the system set the mount path to:
```
/media/hda1
```
These two drives are also sharing the same UUID.

How can I edit fstab to mount both drives?
Why are both drives sharing the same UUID?

---

### Post by bingoUV on 2007-11-15
Plug in both your drives, run the following commands, and post the output here : 
```

sudo fdisk -l
mount
ls -l /dev/disk/by-uuid/

```

---

### Post by anaconda on 2007-11-15
wow.. newer heard that two partitions had tha same uuid? how unlikely..

But you dont have to use uuid:s in your fstab. the good old /dev/xxx format still works just finely.. ANd I think it is even in your fstab.. they are just commented out with #..

alternate solutionwould be to re-format one of the disks, because uuid will change when formatting.

---

### Post by MachineBucket on 2007-11-16
My mistake, I'm using Gutsy not Feisty. Sorry.  :oops:

```
sudo fdisk -l
Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0503ecb1

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9582    76967383+   7  HPFS/NTFS
/dev/hda2            9583       12161    20715817+   5  Extended
/dev/hda5            9583       12052    19840243+  83  Linux
/dev/hda6           12053       12161      875511   82  Linux swap / Solaris

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8ec6571b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12161    97683201    7  HPFS/NTFS
```

```
mount
/dev/hda5 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/hda1 on /media/hda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
```

```
ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2007-11-16 04:12 0fe959fb-a5b3-43d9-804c-ea417145f399 -> ../../hda5
lrwxrwxrwx 1 root root 10 2007-11-16 09:20 46E1748373A5AFF6 -> ../../sda1
lrwxrwxrwx 1 root root 10 2007-11-16 04:12 eab4fc8f-843e-4111-8a66-15113e188d50 -> ../../hda6
```

---

### Post by MachineBucket on 2007-11-16
> wow.. newer heard that two partitions had tha same uuid? how unlikely..

I attached screenshots of the device manager so you can see the uuid for both drives.


> But you dont have to use uuid:s in your fstab. the good old /dev/xxx format still works just finely..

As far as I know, the actual dev path can change depending on which port a drive is plugged into. I suppose I could refer to each drive by its label. I'm still pretty new at this, as you can tell.

---

### Post by MachineBucket on 2007-12-07
So I eventually realized what I did. The hard drives are clones of each other. I replaced the drive in my laptop and used the orginal drive in the enclosure, only I just did a drive clone so I wouldn't need to reformat. I've been using the other drive for music and such, I just forgot that it used to have an OS on it. :oops:

---

