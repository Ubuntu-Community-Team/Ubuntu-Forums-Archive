---
title: "Can't mount or read SDHC card"
date: 2014-07-29
forum: General Help
---

### Post by SgtHubcap on 2014-07-29
I have a micro sd card in a sd card reader slot on my laptop 


```
 /dev/mmcblk0p1: UUID="3439-6265" TYPE="exfat 
```
cant mount it or read it, also when inserted i get this error




```
 
Error mounting /dev/mmcblk0p1 at /media/killswitch/3439-6265: Command-line `mount -t "exfat" -o
"uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,namecase=0,errors=remount-ro,umask=0077" "/dev/mmcblk0p1" "/media/killswitch/3439-6265"'
exited with non-zero exit status 1:
stdout: `FUSE exfat 1.0.1
'
stderr: `WARN: volume was not unmounted cleanly.
ERROR: fsync failed.
' 
```


any suggestions, ive also installed support for the file system utility for gparted and it wont format
its not locked either on the toggle switch for the sdcard reader


Thank you


KS

---

### Post by M._Gruber on 2014-07-29
What's the output of 'lsblk -f' and what happens when you do an fsck on the card?

---

### Post by SgtHubcap on 2014-07-30
```
~ $ lsblk -f
NAME        FSTYPE LABEL MOUNTPOINT
sda                      
&#9500;&#9472;sda1                   
&#9500;&#9472;sda2                   
&#9500;&#9472;sda3                   /
&#9500;&#9472;sda4                   
&#9500;&#9472;sda5                   [SWAP]
&#9500;&#9472;sda6                   /boot
&#9492;&#9472;sda7                   /home
mmcblk0                  
&#9492;&#9472;mmcblk0p1

```

```

sudo fsck /dev/mmcblk0
fsck from util-linux 2.20.1
e2fsck 1.42.9 (4-Feb-2014)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/mmcblk0


The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>



```

```

sudo e2fsck -b 8193 /dev/mmcblk0
e2fsck 1.42.9 (4-Feb-2014)
e2fsck: Bad magic number in super-block while trying to open /dev/mmcblk0


The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

```


```

sudo e2fsck -b 32768 /dev/mmcblk0
e2fsck 1.42.9 (4-Feb-2014)
e2fsck: Bad magic number in super-block while trying to open /dev/mmcblk0


The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>





```

```
sudo blkid
/dev/sda1: LABEL="System Reserved" UUID="8C0C18FF0C18E5CC" TYPE="ntfs" 
/dev/sda2: UUID="B8B61C1EB61BDC26" TYPE="ntfs" 
/dev/sda3: UUID="51c16f56-6a5f-4b00-9519-bbbaa57c3347" TYPE="ext4" 
/dev/sda5: UUID="3b3491d7-d0c2-486f-adf6-c3ec8305ebbc" TYPE="swap" 
/dev/sda6: UUID="dae96720-b375-4e16-80a9-2cbe96bd7999" TYPE="ext4" 
/dev/sda7: UUID="b4e04783-87e4-4e77-894f-e5bd352c2d63" TYPE="ext4" 
/dev/mmcblk0p1: UUID="3439-6265" TYPE="exfat"
```

---

### Post by christer.holmer on 2014-12-06
I got a similar problem (ERROR: fsync failed.) while mounting. 

fsck shows no errors.

```
$ sudo fsck.exfat /dev/mmcblk0p1 
exfatfsck 1.0.1
Checking file system on /dev/mmcblk0p1.
File system version           1.0
Sector size                 512 bytes
Cluster size                128 KB
Volume size                  59 GB
Used space                   17 GB
Available space              43 GB
Totally 824 directories and 5429 files.
File system checking finished. No errors found.

```

I can mount the file read-only like this:

sudo mount -o "ro,uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,namecase=0,errors=remount-ro,umask=0077" "/dev/mmcblk0p1" mnt/

Trying to format it in Windows (vmware guest), but problem prevents it.

---

### Post by llamabr on 2014-12-06
Best to start a new thread if you have a new problem.  This one is 6 months old.

---

