---
title: "HD Not seeming to show up"
date: 2007-10-21
forum: General Help
---

### Post by Pop_A_Squat on 2007-10-21
I just freshly installed gutsy and My secondary HD is not showing up at all. I went to gpart and repartitioned it to a ext2 and set it to boot but it still isnt showing, any advice on what i can do?

---

### Post by mahousaru on 2007-10-21
> **Pop_A_Squat said:**
> I just freshly installed gutsy and My secondary HD is not showing up at all. I went to gpart and repartitioned it to a ext2 and set it to boot but it still isnt showing, any advice on what i can do?

If you want a disk to be used as a non boot drive then you don't need to set it to boot.

Try:

sudo fdisk -l

The below is how I partition my single hard drive

```
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          24      192748+  83  Linux
/dev/hda2              25        2456    19535040   83  Linux
/dev/hda3            2457        6103    29294527+  83  Linux
/dev/hda4            6104        9729    29125845    5  Extended
/dev/hda5            6104        6589     3903763+  83  Linux
/dev/hda6            6590        9729    25222018+   b  W95 FAT32

```

The first IDE PATA (old fat connectors) drive will be hda, the second hda, and so on
The first IDE SATA (new thin connectors, counted as SCSI) drive will be sda, the second sdb, and so on
USB drives will also be counted as SCSI and will be labelled sd, but normally after the SATA drives.

Partitions are the numbers on the end.  For example:
The first partition on the master IDE PATA drive would be hda1 and the second partition would be hda2, and so on.

They should all reside in /dev, so would look like /dev/hda1 etc

*Thank god Ubuntu didn't go the way of OpenSuSE and alias hd drives as sd drives as it is bleeping annoying.*

Then type 

mount

This should show you what is mounted to what directory.  The newly created partition should not be in this list.  I won't show mine as they are all mapper devices and it looks confusing.

Once you identified what device your hard drive is you can map it to a temporary directory such as /mnt with

sudo mount /dev/hdb1 /mnt

This should allow you to access the drive via the directory /mnt

If you want the hard drive to be mounted automatically then you have to edit /etc/fstab.  Make a copy of it first then add the following line to the bottom.  **This is assuming that this is second hard drive, installed as a slave via a PATA interface and that you want to access it via /media/data**. 

/dev/hdb1 /media/data ext2 defaults 0 0

{device} {mount path} {fs type} {options and other funky things}

To test use 

sudo mount -a 

Then type

sudo mount

and it now should be displayed in the list.

For more details on editing the fstab check out this excellent guide:

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by Pop_A_Squat on 2007-10-22
Ok so i did fdisk and the Storage HD actually showed up so that has to be some good news
```
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9349    75095811   83  Linux
/dev/sda2            9350        9726     3028252+   5  Extended
/dev/sda5            9350        9726     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf164f164

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19929   160079661   83  Linux

```

Then i mount it to /mnt directory which it seems to be recognized from the termina
l
```
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb1 on /mnt type ext2 (rw)
/dev/sdb1 on /media type ext2 (rw)
```

Still can't see it if i navigate to the /mnt directory though.


So i Skip down to the fstab edit to see if i can get a better result from editing that. I edit the fstab with 
```
sudo gedit /etc/fstab
```

Type it in 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ef22b821-76dc-4e7b-980e-dd17a41be059 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=86fff655-1463-422e-bc5d-c5229b4fa42a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdb1 	/media/data 	ext2 	defaults 	0 	0
```

and test it out with the mount -a option

and get this

```
mount: mount point /media/data does not exist
```

---

### Post by mahousaru on 2007-10-22
You need a directory under /media called data, but before you do that I would investigate why you have 

```
/dev/sdb1 on /mnt type ext2 (rw)
/dev/sdb1 on /media type ext2 (rw)
```

Which says that the device is mounted to /mnt and /media

Your fstab looks pretty clean and shouldn't mount /dev/sdb1 to media (actually that directory is normally used as an overall container which holds directories that are mounted to).

So I would do

sudo umount /dev/sdb1

sudo mount

Check that there are no /dev/sdb1 references

then 

mkdir /media/data

sudo mount -a

Then if you cannot browse to the directory /media/data, check the rights of the device first.

ls -l /media

Make sure your user has rights to it.  if not then

sudo chown username:groupname /media/data

then try accessing the drive

---

### Post by Pop_A_Squat on 2007-10-22
Well, i mounted i got past the part of getting it to come up right in sudo mount and in the fstab. When i try to navigate to it i still cant get into the hard drive. Just has a lost+Found folder in the /media/data folder.
So i went and looked at ls -l /media

```
total 16
lrwxrwxrwx 1 root root    6 2007-10-21 17:16 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2007-10-21 17:16 cdrom0
drwxr-xr-x 2 root root 4096 2007-10-21 17:16 cdrom1
drwxr-xr-x 3 root root 4096 2007-10-21 18:42 data
lrwxrwxrwx 1 root root    7 2007-10-21 17:16 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2007-10-21 17:16 floppy0

```

This is like binomial to me so i skipped over this part a little

---

### Post by mahousaru on 2007-10-22
The line of interest if this

drwxr-xr-x 3 root root 4096 2007-10-21 18:42 data

It is owned, and grouped to root, so your normal user can only browse this device

So you need to do a one off

sudo chown username:groupname /media/data

Normally the group would be the same as your username, unless you have multiple users on the PC, then we need to discuss how you want to restrict access to it.

Just to increase your geek levels what the ls -l line means is this:

{d} {rwx} {r-x} {r-x}
From left to right....
d - directory
rwx - the owner can Read Write and eXecute this directory
r-x - any members of the group can Read and eXecute the directory
r-x - any user known to the system can Read and eXecute the directory

Rights on files and directory's are slightly different, For example write rights on a directory would allow you to delete a file or directory within it.  Write rights on a file would allow you to modify it.

---

### Post by Pop_A_Squat on 2007-10-22
Heres a question do i need a uuid to have it show as a regular hard drive?

---

### Post by mahousaru on 2007-10-22
> **Pop_A_Squat said:**
> Heres a question do i need a uuid to have it show as a regular hard drive?

You don't need the UUID, you can use /dev/devicename, but UUID will ensure that if something changes ie you plug in another usb hdd, the wrong drive isn't mounted by accident.

To list them use

```
ls /dev/disk/by-uuid -alh
```

---

### Post by Pop_A_Squat on 2007-10-22
Just want to say that i have a manly love for you, came home from work and wala it was mounted, guess it wasnt showing up before because i needed to restart the system

---

### Post by Pop_A_Squat on 2007-10-22
One more thing how do i get permissions so i can write to the disk as a regular user rather than having to put in gksudo nautilus?

Edit: Scratch that i looked at your advice up above and used that, Thanks for all the help again!!

---

### Post by mahousaru on 2007-10-22
I'm happy it helped :)

---

