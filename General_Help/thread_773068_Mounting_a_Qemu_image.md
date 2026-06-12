---
title: "Mounting a Qemu image"
date: 2008-04-28
forum: General Help
---

### Post by AustinMarton on 2008-04-28
Hi there, I am trying to mount a qemu image in feisty but having no luck. It has Win95b installed and so I guess the filesystem is fat?

The command I have found everywhere on the net is:
```
mount -o loopback,offset=32256 /path/to/image.img /mnt/mountpoint
```
- [http://en.wikibooks.org/wiki/QEMU/Images](http://en.wikibooks.org/wiki/QEMU/Images)

Here are my attempts
```
root@austin-laptop:/media# mount -o loop,offset=32256 /home/austin/Win95b /media/win95
mount: you must specify the filesystem type
root@austin-laptop:/media# mount -t vfat -o loop,offset=32256 /home/austin/Win95b /media/win95
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@austin-laptop:/media# dmesg | tail
[ 3039.228000] VFS: Can't find ext3 filesystem on dev loop0.
[ 3039.232000] FAT: bogus number of reserved sectors
[ 3039.232000] VFS: Can't find a valid FAT filesystem on dev loop0.
[ 3039.232000] NTFS-fs warning (device loop0): is_boot_sector_ntfs(): Invalid boot sector checksum.
[ 3039.232000] NTFS-fs error (device loop0): read_ntfs_boot_sector(): Primary boot sector is invalid.
[ 3039.232000] NTFS-fs error (device loop0): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[ 3039.232000] NTFS-fs error (device loop0): ntfs_fill_super(): Not an NTFS volume.
[ 3039.236000] VFS: Can't find an ext2 filesystem on dev loop0.
[ 3043.784000] FAT: bogus number of reserved sectors
[ 3043.784000] VFS: Can't find a valid FAT filesystem on dev loop0.

```

If I run "qemu /home/austin/Win95b" it runs nicely so I know the image is okay.

Any suggestions? 

Many thanks,
'Stan.

---

