---
title: "Mounting movable device as user"
date: 2008-04-28
forum: General Help
---

### Post by satimis on 2008-04-28
Hi folks,


Since only root can mount moveable device I run "sudo mount" to do the job.  However all files copied onto the moveble device become owned by root.  Is there a clue to allow a selected user (NOT all users) to mount movable device as user NOT as root so that the ownership of files copied on to the device can be retained as original.  TIA


B.R.
satimis

---

### Post by mali2297 on 2008-04-28
Hi.

If your uid and gid are 1000, then mount with
```

sudo mount -o uid=1000,gid=1000 /dev/name /mount/point

```
(You can check your id numbers by typing *id* in the terminal.)

---

### Post by coolaj86 on 2008-04-28
What kinds of things are you trying to mount? Most of your usb drives and that sort of thing should be mounted automatically as the logged in user.

However, you can make it so that regular uses can mount things on a regular basis from the command line too.

for example:
# nano -w /etc/fstab
/dev/sdc  	/media/usbdrive  	auto  	rw,noauto,user  	0 0

---

### Post by satimis on 2008-04-28
> **mali2297 said:**
> Hi.

If your uid and gid are 1000, then mount with
```

sudo mount -o uid=1000,gid=1000 /dev/name /mount/point

```
(You can check your id numbers by typing *id* in the terminal.)
Hi Martin,


I got it.  Thanks


B.R.
satimis

---

### Post by satimis on 2008-04-28
> **coolaj86 said:**
> What kinds of things are you trying to mount? Most of your usb drives and that sort of thing should be mounted automatically as the logged in user.

UBS PenDrive.

satimis can't mount it without "sudo"


> 
However, you can make it so that regular uses can mount things on a regular basis from the command line too.

for example:
# nano -w /etc/fstab
/dev/sdc  	/media/usbdrive  	auto  	rw,noauto,user  	0 0
I only allow satimis to mount the device NOT all users.  How to make it on /etc/fstab?  TIA


B.R.
satimis

---

### Post by coolaj86 on 2008-04-28
to the options part of fstab you add 'uid=XXXX,gid=XXXX' in place of 'user' where the uid and gid's match satimis' ID.

---

### Post by satimis on 2008-04-28
> **coolaj86 said:**
> to the options part of fstab you add 'uid=XXXX,gid=XXXX' in place of 'user' where the uid and gid's match satimis' ID.
Sorry, tried following versions.  All failed.

```

/dev/sb1        /media/sb1      auto    rw,uid=1000,gid=1000,noauto    0       0

```


OR```

/dev/sb1        /media/sb1      auto    rw,'uid=1000,gid=1000',noauto    0       0

```


OR```

/dev/sb1        /media/sb1      auto    rw,uid='1000',gid='1000',noauto    0       0

```


OR```

/dev/sb1        /media/sb1      auto    rw,user=satimis,noauto    0       0

```


$ id```

uid=1000(satimis) gid=1000(satimis) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),110(lpadmin),111(admin),1000(satimis),1013(vmgroup)

```


B.R.
satimis

---

### Post by coolaj86 on 2008-04-30
First of all, that should be /dev/sdb1... but I don't think it would work even then.

If you use the 'user' option satimis can mount it. If you don't use the 'user' option, satimis can't mount it. But you can't combine the 'user' option with the 'uid' option.

Hmm...
You could also create a custom command and only give satimis access to it.

as satimis:
```
touch ~/usbmount
nano -w ~/usbmount
#!/bin/bash
mount -o uid=1000,gid=1000 /dev/sdb1 /media/sdb1 
```

as root
```

mkdir -p /media/sdb1
chmod u+xs /home/USER/usbmount
```

then satimis could run ~/usbmount to mount the drive and only satimis would have access to it.

---

### Post by satimis on 2008-04-30
> **coolaj86 said:**
> First of all, that should be /dev/sdb1... but I don't think it would work even then.

If you use the 'user' option satimis can mount it. If you don't use the 'user' option, satimis can't mount it. But you can't combine the 'user' option with the 'uid' option.

Hmm...
You could also create a custom command and only give satimis access to it.

as satimis:
```
touch ~/usbmount
nano -w ~/usbmount
#!/bin/bash
mount -o uid=1000,gid=1000 /dev/sdb1 /media/sdb1 
```

as root
```

mkdir -p /media/sdb1
chmod u+xs /home/USER/usbmount
```

then satimis could run ~/usbmount to mount the drive and only satimis would have access to it.
Thanks for your advice.  I'll test it the later.


I found something strange here which I can't resolve.


I have an USB external enclosure mounted with an old ATA HD.  It is working without problem.  There are 2 partitions on the HD.


$ fdisk -l```

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4769     4883440    c  W95 FAT32 (LBA)
/dev/sdb2            4770        9770     5121024   83  Linux

```

/dev/sdb1 is empty

I'm working on /dev/sdb2 which hold data on it.  I can mount this partition with;

$ sudo mount /dev/sdb2 /media/sdb2

$ cp -p AAA.txt /media/sdb2

$ ls -l /media/sdb2 | grep AAA.txt```

-rw-r--r--  1 satimis satimis  1991 2008-04-27 19:49 AAA.txt

```

Owner and permission preserved.  


However this method can't work on the Flash pendrive.  Owner will be changed as "root root".


But 
$ sudo mount -o uid=1000,gid=1000 /dev/sdb2 /media/sdb2```

mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Doesn't work here.


$ dmesg | tail```

[19083.306397] EXT3 FS on sdb2, internal journal
[19083.306403] EXT3-fs: mounted filesystem with ordered data mode.
[19104.498429] IN=eth0 OUT= MAC=01:00:5e:00:00:01:00:16:b6:c9:8a:a9:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=154 PROTO=2 
[19143.321184] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:16:b6:c9:8a:a9:08:00 SRC=192.168.0.1 DST=192.168.0.255 LEN=173 TOS=0x00 PREC=0x00 TTL=150 ID=3028 PROTO=UDP SPT=3838 DPT=162 LEN=153 
[19149.644430] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:16:b6:c9:8a:a9:08:00 SRC=192.168.0.1 DST=192.168.0.255 LEN=154 TOS=0x00 PREC=0x00 TTL=150 ID=3029 PROTO=UDP SPT=3839 DPT=162 LEN=134 
[19230.387439] IN=eth0 OUT= MAC=01:00:5e:00:00:01:00:16:b6:c9:8a:a9:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=155 PROTO=2 
[19356.276516] IN=eth0 OUT= MAC=01:00:5e:00:00:01:00:16:b6:c9:8a:a9:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=156 PROTO=2 
[19482.165614] IN=eth0 OUT= MAC=01:00:5e:00:00:01:00:16:b6:c9:8a:a9:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=157 PROTO=2 
[19608.054593] IN=eth0 OUT= MAC=01:00:5e:00:00:01:00:16:b6:c9:8a:a9:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=158 PROTO=2 
[19658.322350] EXT3-fs: Unrecognized mount option "uid=1000" or missing value

```


Whether I should run```

$ sudo mkfs.ext3 USB-port

```


Any advice?  TIA


Previously I tried following;

Ubuntu Tutorials : Dapper - Feisty - Gutsy - Hardy
[http://ubuntu-tutorials.com/2006/12/06/how-to-always-mount-removable-drives-in-the-same-place-ubuntu-6061-610/](http://ubuntu-tutorials.com/2006/12/06/how-to-always-mount-removable-drives-in-the-same-place-ubuntu-6061-610/)

without result.


running```

$ udevinfo -a -p $(udevinfo -q path -n /dev/sdx) | grep SYSFS{serial}

```

without output

Tried
/dev/sdx as

/dev/sdb

/dev/sdb1

/dev/sda

all w/o output


B.R.
satimis

---

### Post by mali2297 on 2008-04-30
Which filesystem do you have on the pendrive? The uid,gid method should work for fat and some other filesystems, but not ext2/ext3. If it's the latter, perhaps ownership was set to root when the filesystem was created.

If you want to change filesystem, I think ext2 would be a better choice than ext3.
[QUOTE=Wikipedia]
ext2 is still recommended over journalized file systems for using in bootable USB sticks and likely other solid-state drives. ext2 shows less writing activity than ext3, as it does not need to write the journal. As the major aging factor of a Flash chip is the number of erase cycles, and as those happen frequently on writes, this increases the life span of the USB stick.[citation needed] Another good practice for filesystems on Flash device is the use of the noatime mount option, for the same reason.
[/QUOTE]

---

### Post by satimis on 2008-04-30
> **mali2297 said:**
> Which filesystem do you have on the pendrive? The uid,gid method should work for fat and some other filesystems, but not ext2/ext3. If it's the latter, perhaps ownership was set to root when the filesystem was created.

If you want to change filesystem, I think ext2 would be a better choice than ext3.
This is a brand new pendrive.  I didn't set filesystem on it before testing.  I think it should be FAT16


$ fdisk -l```


Disk /dev/sdb: 260 MB, 260570624 bytes
16 heads, 32 sectors/track, 993 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         994      254447+   6  FAT16

```


The ownership of the directories and files are "satimis satimis".  I copied them on this Ubuntu  7.04 box which is running ext2 OR ext3 filesystem.  I can't remember exactly.


$ sudo fdisk -l```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32       19457   156039345    5  Extended
/dev/sda5              32       19457   156039313+  8e  Linux LVM

```
not showing it?


If mounting the pendrive with;```

$ sudo mount /dev/sdb1 /media/sdb1

```


```

$ sudo cp -p -r /path/to/directory /media/sdb1

```
unable preserving the ownership with warning popup during copying.

On running```

$ ls -l /media/sdb1

```
all directoreis and files shown owned by root


But if umount the pendrive and remount it with```

$ sudo mount -o uid=1,000,gid=1000 /dev/sdb1 /media/sdb1

```

```

$ ls -l /media/sdb1

```
showing all of them owned by "satimis satimis".  This I can't resolve?


B.R.
satimis

---

### Post by mali2297 on 2008-04-30
> **satimis said:**
> 
But if umount the pendrive and remount it with```

$ sudo mount -o uid=1,000m,gid=1000 /dev/sdb1 /media/sdb1

```

```

$ ls -l /media/sdb1

```
showing all of them owned by "satimis satimis".  This I can't resolve?

As far as I understand, fat16 does not have an 'ownership' feature in itself, but Linux sets it upon mount. 

What is the problem that you cannot resolve? What do you want to achieve?

---

### Post by satimis on 2008-04-30
> **mali2297 said:**
> As far as I understand, fat16 does not have an 'ownership' feature in itself, but Linux sets it upon mount. 
It clears my doubt.  Thanks.


> 
What is the problem that you cannot resolve? What do you want to achieve?
No problem now.


B.R.
satimis

---

