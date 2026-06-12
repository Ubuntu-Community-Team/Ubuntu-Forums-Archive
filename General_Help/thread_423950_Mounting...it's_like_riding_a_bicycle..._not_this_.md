---
title: "Mounting...it's like riding a bicycle... not this time!"
date: 2007-04-26
forum: General Help
---

### Post by fpwind on 2007-04-26
Greetings fellow Ubuntu friends

I'm trying to get a usb HD to mount and I'm having a bit of difficulty.  I formatted the drive using gparted to ext3.  When I plug in the drive it says that the disk cannot be mounted.
Rt. clicking on the drive =>Properties=>permissions reveals that the Owner is unknown.

So I'm trying to create a mount point and change permissions so i can use the drive.

when I try to mount the drive I get an error telling me to run dmesg | tail
here the output from that.

> Disk /dev/sde: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1        4998    40146403+  83  Linux
vega@Workstation:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/sde,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

vega@Workstation:~$ dmesg | tail
[64087.782657] sde: Write Protect is off
[64087.782659] sde: Mode Sense: 08 00 00 00
[64087.782661] sde: assuming drive cache: write through
[64087.782664]  sde: sde1
[64087.787973] sd 11:0:0:0: Attached scsi disk sde
[64087.788019] sd 11:0:0:0: Attached scsi generic sg4 type 0
[64088.270854] kjournald starting.  Commit interval 5 seconds
[64088.272344] EXT3 FS on sde1, internal journal
[64088.272594] EXT3-fs: mounted filesystem with ordered data mode.
[64267.983781] VFS: Can't find ext3 filesystem on dev sde.
vega@Workstation:~$ 

I've searched the forums but nothing I've tried is moving me forward. 
Thanks for looking.

---

### Post by taurus on 2007-04-26
Try

```
sudo mkdir /media/external
sudo mount -t ext3 /dev/sde1 /media/external
df -h
```

---

### Post by fpwind on 2007-04-26
wow Taurus a very big thanks to you! That got er' mounted no problems
I had previously tried to mount using  "sudo mount -a" after adding the mount point to  /etc/fstab
If you don't mind my asking what did "sudo mount -t ext3 /dev/sde1 /media/external" do differently to successfully mount the drive.
Thanks for your help and sharing your knowledge!

---

### Post by taurus on 2007-04-26
The first command is to create a new mount point, /media/external, for it.

The second command actually mounts your /dev/sde1 to /media/external with ext3 filesystem.

The third command lists all your mount partitions/directories.

The only problem is that you need to run the second command to mount your harddrive each time you boot or whenever you plug in your USB harddrive.

---

