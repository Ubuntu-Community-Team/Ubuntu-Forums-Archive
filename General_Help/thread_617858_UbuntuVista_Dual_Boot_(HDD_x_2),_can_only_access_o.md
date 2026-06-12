---
title: "Ubuntu/Vista Dual Boot (HDD x 2), can only access one partition of vista drive."
date: 2007-11-19
forum: General Help
---

### Post by Kn1v3s37 on 2007-11-19
I'm dual booting with Vista and Ubuntu, separate Hard Drives. Vista has 2 partitions (one for the OS, one for installed games). While in Ubuntu, I can only access the partition with Vista, not my games partition, I click on it, it asks for my password, then just puts me to the root folder in my Ubuntu drive.

Any help?

Thanks,
Ryan

---

### Post by Pumalite on 2007-11-19
What's the format of this games partition?

---

### Post by Kn1v3s37 on 2007-11-19
It's FAT32.

---

### Post by Pumalite on 2007-11-19
Post:
mount

---

### Post by Kn1v3s37 on 2007-11-19
Not too sure what you mean by that, but when I right click and click on mount, it asks me for my password, I type the password, then it told me it was invalid, I typed it again and nothing happened, and it just went back to my root directory.

---

### Post by Pumalite on 2007-11-19
At the Terminal type:
mount
Post the output here.

---

### Post by Kn1v3s37 on 2007-11-19
/dev/hdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/hda5 on /media/disk type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

Hope that's right.

---

### Post by teryowen on 2007-11-19
type into terminal:
sudo fdisk -l /dev/hda
sudo fdisk -l /dev/hdb

and post the out put.

is /dev/hda5 the vista partition, looks to me like you have one of the paritions from the first hard drive mounted that being hda5, once you post what you get hopefully we will be able to mount the other partition and get you access.

---

### Post by Kn1v3s37 on 2007-11-19
First:
Disk /dev/hda: 30.8 GB, 30806180352 bytes
255 heads, 63 sectors/track, 3745 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x93dd3679

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1873    15044841    c  W95 FAT32 (LBA)
/dev/hda2            1874        3745    15036840    f  W95 Ext'd (LBA)
/dev/hda5            1874        3745    15036808+   7  HPFS/NTFS

Second:
Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x439f439e

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       19080   153260068+  83  Linux
/dev/hdb2           19081       19457     3028252+   5  Extended
/dev/hdb5           19081       19457     3028221   82  Linux swap / Solaris

---

### Post by teryowen on 2007-11-19
to mount your FAT32 partition do the following: create a mount point:
```

mkdir /media/hda1

```

Next mount the drive:
```

sudo mount /dev/hda1 /media/hda1 rw

```

this will mount it at /media/hda1 as read-write

---

### Post by Kn1v3s37 on 2007-11-19
It didn't work with rw at the end, it gave me:
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

So I took out the rw and it mounted it as a read only.

---

### Post by teryowen on 2007-11-19
sorry i think the correct syntax woul dhave been

sudo mount /dev/hda1 /media/hda1 -rw

i forgot the dash

and if the -rw doesn't work just dont use it should work without too i think.

So unmount it and then remount:

sudo umount /dev/hda1
sudo mount /dev/hda1 /media/hda1 -rw

---

