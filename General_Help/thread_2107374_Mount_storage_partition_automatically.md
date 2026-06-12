---
title: "Mount storage partition automatically?"
date: 2013-01-21
forum: General Help
---

### Post by aem0512 on 2013-01-21
I'm setting up a Lubuntu 12.10 system for my friend and I'd like to have the ntfs storage partition automount at startup, but at the moment it's requiring you to click on it in pcmanfm and put in the password. 

I checked the options for pcmanfm and it says it should be automounting volumes at program start but it isn't mounting these other partitions.

Anyone know how to do this?

thanks!

---

### Post by papibe on 2013-01-21
Hi aem0512.

The simplest way would be to create an entry on the file /etc/fstab

Take a look at this [tutorial]("https://help.ubuntu.com/community/Fstab") for the details.

Let us know how it goes.
Regards.

---

### Post by MrZorg2012 on 2013-01-23
> **papibe said:**
> Hi aem0512.

The simplest way would be to create an entry on the file /etc/fstab

Take a look at this [tutorial]("https://help.ubuntu.com/community/Fstab") for the details.

Let us know how it goes.
Regards.

Yeah, read that, it's still all greek.

---

### Post by aem0512 on 2013-01-23
> **MrZorg2012 said:**
> Yeah, read that, it's still all greek.

My sentiments exactly...sigh...

---

### Post by papibe on 2013-01-23
I would gladly guide through the process.

Could you post the result of these commands?
```
cat /etc/fstab

mount -l

df -h

sudo fdisk -l

sudo lshw -C disk
```
Regards.

---

### Post by MrZorg2012 on 2013-01-24
> **papibe said:**
> I would gladly guide through the process.

Could you post the result of these commands?
```
cat /etc/fstab

mount -l

df -h

sudo fdisk -l

sudo lshw -C disk
```
Regards.

root@larrys:/home/larry# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=db09de44-235a-4544-a33d-2e46ff4fd38a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=135fd3e1-fb91-4dd7-80ec-41577b1d0ba9 none            swap    sw              0       0
root@larrys:/home/larry# 
root@larrys:/home/larry# mount -l
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
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
gvfsd-fuse on /run/user/larry/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=larry)
/dev/sr0 on /media/larry/Lubuntu 12.10 amd641 type iso9660 (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks2) [Lubuntu 12.10 amd64]
root@larrys:/home/larry# 
root@larrys:/home/larry# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        65G  8.9G   53G  15% /
udev            1.7G  4.0K  1.7G   1% /dev
tmpfs           690M  816K  690M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.7G   72K  1.7G   1% /run/shm
none            100M   24K  100M   1% /run/user
/dev/sr0        699M  699M     0 100% /media/larry/Lubuntu 12.10 amd641
root@larrys:/home/larry# 
root@larrys:/home/larry# sudo fdisk -l

Disk /dev/sda: 74.4 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders, total 145226112 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c3471

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   137887743    68942848   83  Linux
/dev/sda2       137889790   145225727     3667969    5  Extended
/dev/sda5       137889792   145225727     3667968   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf41be56d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdb2          206848    42004479    20898816    7  HPFS/NTFS/exFAT
/dev/sdb3        42004480   488396799   223196160    7  HPFS/NTFS/exFAT
root@larrys:/home/larry# 
root@larrys:/home/larry# sudo lshw -C disk

With sdb3 as being my storage partition on extra drive :-)

---

### Post by papibe on 2013-01-24
Ok.

Let's try to make a manual test before making it permanently.

Create a mount point:
```
sudo mkdir /media/MyStorage
```
Mount the partition:
```
sudo mount -t ntfs /dev/sbb3 /media/MyStorage
```
Now browse the directory /media/MyStorage to make sure everything is OK.

Unmount the partition:
```
sudo umount /media/MyStorage
```

If all went well, please post the result of this command to finally proceed to create the mount point on /etc/fstab
```
sudo blkid
```
Regards.

---

