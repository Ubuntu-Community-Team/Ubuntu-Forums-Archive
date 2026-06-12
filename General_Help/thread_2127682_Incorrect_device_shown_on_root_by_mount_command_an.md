---
title: "Incorrect device shown on root by mount command and GParted."
date: 2013-03-20
forum: General Help
---

### Post by KSM0071 on 2013-03-20
I have 2 Ubuntu partitions 
   /dev/sda1 - Internal Laptop HDD with Ubuntu 12.10 installed
   /dev/sdb2 - External HDD with Ubuntu 13.04 installed (do daily build updates)

From GRUB2 I select to boot from /dev/sdb2, which by most evidence appears to boot the correct partition (Ubuntu 13.04)

However, when run mount i receive:
-/dev/sda1 on / type ext4 (rw,errors=remount-ro)
-/dev/sda1 on /media/kyle/26da9a54-ff10-415f-8133-3cce644adcc4 type ext4 (rw,nosuid,nodev,uhelper=udisks2)

GParted confirms the above info from mount.

No mention of sdb2. If I manually mount sdb2 (e.g. sudo mount /dev/sdb2 /media/test/) the files and any changes in /media/test, are reflected on current running OS (and vice versa). 

For example, /media/test/home/kyle/Desktop contains the files on my desktop and any changes are reflected on my current desktop. 

Files on /media/kyle/26da9a54-ff10-415f-8133-3cce644adcc4 are not reflected on the / directory of current running OS.

Questions:
  Is this likely to just be a bug in 13.04? If not, why is this happening and should I be concerned?

I discovered as I was going to try copy my sdb2 partition to sda1 since 13.04 seems stable for my at this time.
I am now reluctant since I am either confused about my partitions or Ubuntu is.

Thanks in advance for any reply.

---

### Post by dabl on 2013-03-20
With your external hard drive connected and mounted, run these commands and post the output:

```
sudo fdisk -lu
```

```
sudo blkid -c /dev/null -o list
```

---

### Post by KSM0071 on 2013-03-20
> **dabl said:**
> With your external hard drive connected and mounted, run these commands and post the output:

```
sudo fdisk -lu
```

```
sudo blkid -c /dev/null -o list
```

Thanks for the reply.

```
sudo fdisk -lu 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3833069c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   604661759   302329856   83  Linux
/dev/sda2       604661760   625141759    10240000   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000175828992 bytes
255 heads, 63 sectors/track, 121597 cylinders, total 1953468416 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a34ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1625788415   812893184    7  HPFS/NTFS/exFAT
/dev/sdb2   *  1646268416  1953468415   153600000   83  Linux
/dev/sdb3      1625788416  1646268415    10240000   82  Linux swap / Solaris

Partition table entries are not in disk order 
```

```
sudo blkid -c /dev/null -o list

device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ext4             (not mounted)  26da9a54-ff10-415f-8133-3cce644adcc4
/dev/sda2  swap             (not mounted)  2e525537-3c7e-4080-b409-66d770f79a54
/dev/sdb1  ntfs    My Passport /media/kyle/My Passport AA14A27114A23FE5
/dev/sdb2  ext4             /              26da9a54-ff10-415f-8133-3cce644adcc4
/dev/sdb3  swap             (not mounted)  acbdc84c-bffe-43e6-b9d8-00cda58be37b

```

Interesting, output from those commands seems be as expected.

```
mount

/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfsd-fuse on /run/user/kyle/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=kyle)
/dev/sdb1 on /media/kyle/My Passport type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb2 on /media/test type ext4 (rw)

```

Mount command output shows "/dev/sda1 on /".
This appears to be a bug possibly of/relating to mount and GParted.
What do you think?

---

### Post by dabl on 2013-03-21
Your problem is that the "/dev/sdx" device designations are not robust in the face of USB-connected bootable devices, and (as shown by blkid) you are actually booting the external partition that you know as /dev/sdb2, which is being reassigned to /dev/sda1 by the system when it is mounted as "/".  You need to use only UUIDs for identification of the bootable partitions, and if you intend to have grub installed on the mbr of the internal hard drive, you're going to have to reinstall grub-pc, because it appears to me it is on the second partition of the USB drive (see the *).  Also, FYI, you only need 1 swap partition on a given system.

There's a "boot repair" utility on the Live CD called "bootinfo" that you're going to need to use to fix it.  Here's guidance:

[http://ubuntuforums.org/showthread.php?t=2127636&p=12566482#post12566482](http://ubuntuforums.org/showthread.php?t=2127636&p=12566482#post12566482)

If you're not locked into this particular configuration, as general advice I would say put both your OS partitions, plus a small (1GB) swap space on the internal hdd, and use the external device for data storage only.  (You will see that this forum is relatively full of folks with similar problems as you have, when attempting to boot from USB drives.)

---

