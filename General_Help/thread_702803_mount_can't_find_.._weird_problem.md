---
title: "mount: can't find .. weird problem"
date: 2008-02-20
forum: General Help
---

### Post by sofamensch on 2008-02-20
Usually search my solutions myself but this time i gotta ask :-)

It's impossible to mount a certain NTFS drive via bash.

```

sofa@sofa-desktop:/etc$ sudo mount /dev/sda3
[sudo] password for sofa:
mount: can't find /dev/sda3 in /etc/fstab or /etc/mtab

```

but if i go to this drive with nautilus, and then check my mounts i can see it. and this when i type mount

```

/dev/sda3 on /media/Volume type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

```

How come? How to mount via bash? Its easily the 3.rd Partition on Primary HDD.

---

### Post by oooh on 2008-02-20
hej, i have it mounted like this, an ntfs:

fuseblk

mount tells me:
/dev/sda1 on /media/disk-2 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

---

### Post by sisco311 on 2008-02-20
please post the output from:

```
mount
```

```
sudo fdisk -l
```

```
cat /etc/fstab
```

---

### Post by sofamensch on 2008-02-20
here you go
(of course this is when the drive is not mounted as you see.

```


#$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb1 on /media/USB SAFE AL type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)

#$ 
#$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1794dc14

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2550    20482843+  83  Linux
/dev/sda2   *        2551        4462    15358140    7  HPFS/NTFS
/dev/sda3            4463        9434    39937590    7  HPFS/NTFS
/dev/sda4            9435        9729     2369587+  82  Linux swap / Solaris

Disk /dev/sdb: 1014 MB, 1014497280 bytes
65 heads, 32 sectors/track, 952 cylinders
Units = cylinders of 2080 * 512 = 1064960 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         953      990704    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(967, 64, 32) logical=(952, 39, 32)

#$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0827070a-d5b3-4fc7-bd05-dc050ed0fbb4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=6E1C16001C15C3CD /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=b063fe41-2ec1-45ce-a6fd-6729694d1196 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


```

in addition here the etc/fstab after mounting. sda2 still not here

```

#$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0827070a-d5b3-4fc7-bd05-dc050ed0fbb4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=6E1C16001C15C3CD /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=b063fe41-2ec1-45ce-a6fd-6729694d1196 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
#$ 

```

---

### Post by sisco311 on 2008-02-20
create a mount point:
```
sudo mkdir /media/my_disk
```mount the partition:
```
sudo mount -t ntfs -o nls=utf8,umask=0007 /dev/sda3 /media/my_disk
```to mount automatically on boot:

edit your fstab:
```
sudo gedit /etc/fstab
```add this line:

> /dev/sda3 /media/my_disk ntfs nls=utf8,umask=0007 0    0

---

### Post by sofamensch on 2008-02-20
Thanks this should help. 
I assume that the creation of this partition (probably under Win after Ubuntu install?) messed this up.
Shouldn't update /etc/fstab automatically?   otherwise it will stay the same like when installed on every system, what is not quite perfect for all us ubuntu users ;-) or am i so special ;-)

---

### Post by sisco311 on 2008-02-20
yes, you're right.

I don't have ntfs partitions so maybe the fstab entry is:

> /dev/sda3 <insert_existing_mount_point_here_like_:_/media/sda3>     ntfs defaults,umask=007,gid=46 0       1

and you can delete this lines:

> # /dev/sda5
UUID=6E1C16001C15C3CD /media/sda5     ntfs    defaults,umask=007,gid=46 0       1

***back up your fstab first

---

