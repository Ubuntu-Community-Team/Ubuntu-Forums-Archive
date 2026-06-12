---
title: "Cannot get two JFS partitions mounted, fstab."
date: 2014-05-11
forum: General Help
---

### Post by killabee44 on 2014-05-11
Hi all,

I have a mythbuntu install in which I am trying to get two JFS partitions mounted. Im sure the problem lies in the fstab file, but I have tried multiple options, but cannot get them mounted. Your help will be appreciated!

Here is some info: 

sudo blkid
```

/dev/sda1: UUID="569c202e-fbc1-4d7b-9070-47c5ae4c5056" TYPE="ext4" 
/dev/sda3: UUID="2dfd438b-957d-403c-99c7-95fd6b44726c" TYPE="ext4" 
/dev/sda5: UUID="ec39da7c-894d-436f-879e-6ebdc6b1cf4d" TYPE="jfs" 
/dev/sdb1: LABEL="mythtv" UUID="7ce01738-5525-4afe-bd89-0af7e1fd969d" TYPE="jfs"
```

/etc/fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=569c202e-fbc1-4d7b-9070-47c5ae4c5056 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=2dfd438b-957d-403c-99c7-95fd6b44726c /home           ext4    defaults        0       2

#JFS MEDIA:
UUID=ec39da7c-894d-436f-879e-6ebdc6b1cf4d    none         jfs     defaults,noauto,rw,user     2
UUID=7ce01738-5525-4afe-bd89-0af7e1fd969d    none         jfs    defaults,noauto,rw,user     2


```

I have tried using the auto option in fstab but end up with an error during boot that says "cannot mount, press s to skip" on both partitions. 

Thanks in advance!

---

### Post by tfrue on 2014-05-12
Your missing parameters. You need to specify a mount point, and a dump number. Here is a generic layout using the some of your info:
```

UUID=7ce01738-5525-4afe-bd89-0af7e1fd969d /mnt/share jfs defaults,users,noauto 0 2
```
That will mount the specified device at /mnt/share with jfs as the FS and take the default options (rw, suid, dev, exec, auto, nouser, and async) with 0 for dump and 2 for pass. You will obviously need to create the mount point (/mnt/share in my example) before you try to mount it.

Here is Ubuntu's help page for fstab:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Chris

---

### Post by killabee44 on 2014-05-12
> **tfrue said:**
> Your missing parameters. You need to specify a mount point, and a dump number. Here is a generic layout using the some of your info:
```

UUID=7ce01738-5525-4afe-bd89-0af7e1fd969d /mnt/share jfs defaults,users,noauto 0 2
```
That will mount the specified device at /mnt/share with jfs as the FS and take the default options (rw, suid, dev, exec, auto, nouser, and async) with 0 for dump and 2 for pass. You will obviously need to create the mount point (/mnt/share in my example) before you try to mount it.

Here is Ubuntu's help page for fstab:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Chris

Thanks for your reply..

I tried with your settings and did not get errors at startup. So that is good. 

Im not sure how to create the shares, so I opened up a file browser (thunar) with sudo and created the two folders in /mnt. I then changed the owner to users and permissions to r/w.  When I click the folders I cannot see my files though, so Im sure that is not correct.

When I have the file browser logged as sudo, I can see the drive on the left side, but when I try to access it I get the following error:

```
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

This is the way my fstab file looks now:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=569c202e-fbc1-4d7b-9070-47c5ae4c5056 /               ext4    errors=remount-ro    0       1
# /home was on /dev/sda3 during installation
UUID=2dfd438b-957d-403c-99c7-95fd6b44726c /home           ext4    defaults        0       2

#JFS MEDIA:
UUID=ec39da7c-894d-436f-879e-6ebdc6b1cf4d   /mnt/music         jfs    defaults,users,noauto    0   2
UUID=7ce01738-5525-4afe-bd89-0af7e1fd969d   /mnt/mythfiles     jfs    defaults,users,noauto    0   2
```

---

### Post by tfrue on 2014-05-14
You cannot have the files in the directory before you mount the drive. So if you have /mnt/music in an un-mounted stage and place files in the directory, when you mount the device to that directory, those files will not be there until you un-mount the device. 

Also, you have the option **noauto** so the lines that you have added to fstab will not mount at boot, you will have to manually type out the mount command for each single line.

Would you also post the output of:
```
dmesg | tail
and
ls -ll /mnt
```

Let's make sure that those partitions are actaully JFS, type:
```
sudo fdisk -l
and
sudo fsck -N /dev/sdb1
and
sudo fsck -N /dev/sda5
```

Also, 

Also, try and just mount the device from the terminal and see what happens, try:
```
sudo mount -t jfs -o noauto,user,defaults /dev/sdb1 /mnt/mythfiles
```

We will work on the sharing bit next, we first need to get them mounted Ha!

---

### Post by killabee44 on 2014-05-14
> **tfrue said:**
> You cannot have the files in the directory before you mount the drive. So if you have /mnt/music in an un-mounted stage and place files in the directory, when you mount the device to that directory, those files will not be there until you un-mount the device. 

Also, you have the option **noauto** so the lines that you have added to fstab will not mount at boot, you will have to manually type out the mount command for each single line.

Would you also post the output of:
```
dmesg | tail
and
ls -ll /mnt
```

Let's make sure that those partitions are actaully JFS, type:
```
sudo fdisk -l
and
sudo fsck -N /dev/sdb1
and
sudo fsck -N /dev/sda5
```

Also, 

Also, try and just mount the device from the terminal and see what happens, try:
```
sudo mount -t jfs -o noauto,user,defaults /dev/sdb1 /mnt/mythfiles
```

We will work on the sharing bit next, we first need to get them mounted Ha!

Tfrue,

What I meant is that the drive (and the other paritition  I am trying to mount) both have data on them, so I am just talking about accessing that data.

Here are the outputs:

dmesg | tail:

```
[ 5541.419270] sd 9:0:0:0: [sdc] Mode Sense: 03 00 00 00
[ 5541.420251] sd 9:0:0:0: [sdc] No Caching mode page found
[ 5541.420257] sd 9:0:0:0: [sdc] Assuming drive cache: write through
[ 5541.424280] sd 9:0:0:0: [sdc] No Caching mode page found
[ 5541.424290] sd 9:0:0:0: [sdc] Assuming drive cache: write through
[ 5542.271371]  sdc: sdc1
[ 5542.275094] sd 9:0:0:0: [sdc] No Caching mode page found
[ 5542.275105] sd 9:0:0:0: [sdc] Assuming drive cache: write through
[ 5542.275112] sd 9:0:0:0: [sdc] Attached SCSI removable disk
[ 5553.978527] FAT-fs (sdc1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
```

ls -ll /mnt:
total 8
```
drwxrwxrwx 2 root users 4096 May 12 19:13 music
drwxrwxrwx 2 root users 4096 May 12 19:13 mythfiles
```

sudo fdisk -l
```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000207b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    61545014    30772476   83  Linux
/dev/sda2       125033895  1250258624   562612365    5  Extended
/dev/sda3        61545015   125033894    31744440   83  Linux
/dev/sda5       125033958  1250258624   562612333+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00029fe9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907024895  1953511424   83  Linux

Disk /dev/sdc: 33.5 GB, 33525071872 bytes
255 heads, 63 sectors/track, 4075 cylinders, total 65478656 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x88a941fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    65464874    32732406    c  W95 FAT32 (LBA)
```

sudo fsck -N /dev/sdb1
```
fsck from util-linux 2.20.1
fsck: fsck.jfs: not found
fsck: error 2 while executing fsck.jfs for /dev/sdb1
```

sudo fsck -N /dev/sda5
```
fsck from util-linux 2.20.1
fsck: fsck.jfs: not found
fsck: error 2 while executing fsck.jfs for /dev/sda5
```

sudo mount -t jfs -o noauto,user,defaults /dev/sdb1 /mnt/mythfiles
```
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```


Hmm, so does that mean that those are not seen as JFS partitions? I looked on Gparted just now and it does show them as being JFS, but it said that I needed the software package jfsutils in order to see details. I loaded that package and am rebooting.

Edit:

Ok, after installing jfsutils, I get:

sudo fsck -N /dev/sdb1
```
fsck from util-linux 2.20.1
[/sbin/fsck.jfs (1) -- /mnt/mythfiles] fsck.jfs /dev/sdb1 
```

sudo fsck -N /dev/sda5
```
fsck from util-linux 2.20.1
[/sbin/fsck.jfs (1) -- /mnt/music] fsck.jfs /dev/sda5
```

I still can't mount via the command line with the same error I posted above.

Edit again..
 
Ok, after doing: sudo fsck.jfs /dev/sda5 and sudo fsck.jfs /dev/sdb1  I am now able to mount and see my files, but only as sudo. I went ahead and edited my fstab to automount. 

After reboot, sda5 and sdb1 automounted, but I can only see the drives when I run Thunar as sudo. 

I then changed fstab again since I realize that I wrote users instead of the user option by mistake. That allowed me to see and edit the files in those mounts with a non sudo username. 

The mounts still don't show up under devices, but at least I can create a shortcut in Thunar for the mount points.

---

### Post by tfrue on 2014-05-15
The *fdisk* command showed that you have a file system type of 83 which is the Linux ext file system. So what I would do now is just to try and mount with mount auto detecting the FS and mount under the /media directory. So first unmount and at least comment out the new lines you added regarding these two partitions by adding a # (hast-tag) infront of each new statement and save the file. You can issue *mount* to see if you still have the two partitions (/dev/sda5 and /dev/sdb1) mounted.

So, type:
```

sudo mkdir /media/mythtv
sudo mount -t auto /dev/sda5 /media/mythtv

```
That will create the mythtv directory under /media and then we'll tell mount to auto detect the FS type of /dev/sda5 and mount it at /media/mythtv. You can now type *mount* to see if it mounted it.

You should also make another directory under /media for the /dev/sdb1 partition and name the new directory anything you want and use the same syntax as before to mount /dev/sdb1 on the new directory. (e.x. sudo mount -t auto /dev/sdb1 /media/newDirectory)

So after all this, I would like to see some output, lol. Please type:
```

mount
and
sudo fdisk -l
and
sudo blkid
and
ls -ll /media
and
cat /etc/fstab
```

Thanks,
Chris

---

### Post by tfrue on 2014-05-15
I also meant to mention that you may have to change the ownership of the two new directories /media/mythtv and the other one you should've made for /dev/sdb1;So first make sure that they are mounted because if they are not the permissions you set for them now will not stay when you do mount to them,so you will need to type(I'm using tfrue but you will need to use your username):
```
sudo chown tfrue.tfrue /media/mythtv
and
sudo chown tfrue.tfrue /media/newDirectory (For the /dev/sdb1 directory)

```

Chris

---

### Post by killabee44 on 2014-05-15
Ok, I did as you said and commented out the two lines in my fstab. I then manually mounted them using the command you gave me.

Here's mount:

```
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
none on /sys/fs/pstore type pstore (rw)
/dev/sda3 on /home type ext4 (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
/dev/sdc1 on /media/htpc1/MusicandVideo type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda5 on /media/music type jfs (rw)
/dev/sdb1 on /media/mythfiles type jfs (rw)
```

sudo fdisk -l:

```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000207b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    61545014    30772476   83  Linux
/dev/sda2       125033895  1250258624   562612365    5  Extended
/dev/sda3        61545015   125033894    31744440   83  Linux
/dev/sda5       125033958  1250258624   562612333+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00029fe9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907024895  1953511424   83  Linux

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003c482

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63  2930272064  1465136001    7  HPFS/NTFS/exFAT

```

sudo blkid

```
/dev/sda1: UUID="569c202e-fbc1-4d7b-9070-47c5ae4c5056" TYPE="ext4" 
/dev/sda3: UUID="2dfd438b-957d-403c-99c7-95fd6b44726c" TYPE="ext4" 
/dev/sda5: UUID="ec39da7c-894d-436f-879e-6ebdc6b1cf4d" TYPE="jfs" 
/dev/sdb1: LABEL="mythtv" UUID="7ce01738-5525-4afe-bd89-0af7e1fd969d" TYPE="jfs" 
/dev/sdc1: LABEL="MusicandVideo" UUID="2AA91D326971D565" TYPE="ntfs" 

```

ls -ll /media

```
total 8
drwxr-x---+ 3 root root     4096 May 14 22:51 htpc1
drwxr-xr-x  5 root root       24 Mar 22  2010 music
drwxrwxrwx  5 root utempter 4096 Feb 11  2013 mythfiles
```

cat /etc/fstab

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=569c202e-fbc1-4d7b-9070-47c5ae4c5056 /               ext4    errors=remount-ro    0       1
# /home was on /dev/sda3 during installation
UUID=2dfd438b-957d-403c-99c7-95fd6b44726c /home           ext4    defaults        0       2

#JFS MEDIA:
#UUID=ec39da7c-894d-436f-879e-6ebdc6b1cf4d   /media/music         jfs    defaults,user,auto    0   2 
UUID=7ce01738-5525-4afe-bd89-0af7e1fd969d   /media/mythfiles     jfs    defaults,user,auto    0   2       

```

So, it looks like they are seen as JFS, no? I still don't understand why fdisk sees them as type 83 linux..

Edit: after looking around it seems that type 83 linux can be various filesystem types including JFS.

---

### Post by killabee44 on 2014-05-15
> **tfrue said:**
> I also meant to mention that you may have to change the ownership of the two new directories /media/mythtv and the other one you should've made for /dev/sdb1;So first make sure that they are mounted because if they are not the permissions you set for them now will not stay when you do mount to them,so you will need to type(I'm using tfrue but you will need to use your username):
```
sudo chown tfrue.tfrue /media/mythtv
and
sudo chown tfrue.tfrue /media/newDirectory (For the /dev/sdb1 directory)

```

Chris

Ok, I got the permissions. But, will the mythtv service still be able to access the /media/mythfiles with me as the owner?

Thanks.

---

### Post by tfrue on 2014-05-16
While reading through a MythTV article, it seems as though we will need the permissions to be owned by mythtv user and group and then add your user account to the mythtv group.

So lets try again, type:
```
sudo chown mythtv.mythtv /media/mythtvfiles
and
sudo chown mythtv.mythtv /media/newDirectory (For the /dev/sdb1 directory)
and
sudo useradd -G mythtv YourUserName (Which will add you to the mythtv group)
```
Were you succesfully able to mount and view the files by manually mounting? If so, I would say it would be safe to remove the comments you made on the /etc/fstab as I reviewed them and they seemed to be a proper mount syntax

---

### Post by killabee44 on 2014-05-25
> **tfrue said:**
> While reading through a MythTV article, it seems as though we will need the permissions to be owned by mythtv user and group and then add your user account to the mythtv group.

So lets try again, type:
```
sudo chown mythtv.mythtv /media/mythtvfiles
and
sudo chown mythtv.mythtv /media/newDirectory (For the /dev/sdb1 directory)
and
sudo useradd -G mythtv YourUserName (Which will add you to the mythtv group)
```
Were you succesfully able to mount and view the files by manually mounting? If so, I would say it would be safe to remove the comments you made on the /etc/fstab as I reviewed them and they seemed to be a proper mount syntax

Sorry I havent replied. Just havent had much time to work on this.

Ok, Igot the permissions and ownership done. Yes, I was able to mount. Removed the comment (#) and all is working properly. Thanks for all your help with this. Much appreciated!

---

