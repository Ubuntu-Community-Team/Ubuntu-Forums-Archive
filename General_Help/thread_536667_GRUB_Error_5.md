---
title: "GRUB Error 5"
date: 2007-08-28
forum: General Help
---

### Post by derekr44 on 2007-08-28
So I just got done loading and playing World of Warcraft through Crossover.

I rebooted my machine and am prompted with the following error:
> GRUB Loading.  Please wait...
Error 5

Help!  I can't do anything and I don't know what changed!

---

### Post by merlinus on 2007-08-28
Here is info on grub error 5:

[http://users.bigpond.net.au/hermanzone/p15.htm#5_](http://users.bigpond.net.au/hermanzone/p15.htm#5_)

-merlin

---

### Post by derekr44 on 2007-08-28
**sudo fdisk -l**

> Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *         572       24321   190771875    7  HPFS/NTFS
/dev/hda2               1         571     4586526    b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       18700   150207718+  83  Linux
/dev/hdb2           18701       19457     6080602+   5  Extended
/dev/hdb5           18701       19457     6080571   82  Linux swap / Solaris

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9728    78140128+   c  W95 FAT32 (LBA)

**sudo mount**

> proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw,mode=0755)
/dev/bus/usb on /proc/bus/usb type none (rw,bind)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda1 on /media/My Book type vfat (rw,nosuid,nodev,shortname=mixed,uid=999,utf8,umask=077)


---

### Post by merlinus on 2007-08-28
You have two boot flags set, one for windows and one for ubuntu.

Remove the one for ubuntu and restart.  Hopefully it will work.

-merlin

---

### Post by derekr44 on 2007-08-28
Yeah, I just read that only one needs to be Active.  How can I remove the active flag from the hdb1 partition?  Just uncheck "Boot" in GParted on that partition?

---

### Post by merlinus on 2007-08-28
That might work.  If not, use either the ubuntu live cd or gparted live cd, as you may not be able to change the boot flag on a mounted partition, and cannot unmount the one you are currently using.

-merlin

---

### Post by derekr44 on 2007-08-28
Ok...

I unchecked "Boot" on the hdb1 partition and rebooted... same error
I unchecked "Boot" on the hda1 partition and rebooted... same error

Finally got thinking for a second and unplugged my USB storage drive and rebooted... no error...

Any idea why my external drive would cause GRUB to throw that error?  Perhaps because the drive is loaded on boot in BIOS?

---

