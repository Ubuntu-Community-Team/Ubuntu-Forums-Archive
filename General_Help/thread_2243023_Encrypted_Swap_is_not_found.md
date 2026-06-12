---
title: "Encrypted Swap is not found"
date: 2014-09-05
forum: General Help
---

### Post by obake2 on 2014-09-05
I was following [this thread]("http://ubuntuforums.org/showthread.php?t=2224129") to make the encrypted-swap work, but it failed. The solution provided in that thread has worked for my one of my laptop, but it didn't work in the other one.

Swapon -s dosn't show swap:

```
cat@Hawaii:~$ swapon -s
Filename                Type        Size    Used    Priority
cat@Hawaiian:~$ 

```

```
cat@Hawaii:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=d290bfb1-d81d-4c0e-a2a8-af1b82b463c1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
#UUID=830682aa-76e0-4d12-97a3-a3bd64b74128 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
cat@Hawaii:~$ 


```

Here it dosn't show the swap's UUID:

```
cat@Hawaii:~$ cat /etc/crypttab
cryptswap1 /dev/sda6 /dev/urandom swap,cipher=aes-cbc-essiv:sha256
cat@Hawaii:~$ 


```

```
cat@Hawaii:~$ sudo fdisk -l
[sudo] password for cat: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x97804ced

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     3074047     1536000   27  Hidden NTFS WinRE
/dev/sda2         3074048   254732287   125829120    7  HPFS/NTFS/exFAT
/dev/sda3       954376192   976773119    11198464   17  Hidden HPFS/NTFS
/dev/sda4       254734334   954376191   349820929    5  Extended
/dev/sda5       254734336   946257773   345761719   83  Linux
/dev/sda6       946259968   954376191     4058112   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/mapper/cryptswap1: 4155 MB, 4155506688 bytes
255 heads, 63 sectors/track, 505 cylinders, total 8116224 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x363a72b8

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table
cat@Hawaii:~$ 


```

```
cat@Hawaii:~$ sudo -s
root@Hawaii:~# umount /dev/sda6
umount: /dev/sda6: not mounted
root@Hawaii:~# mkswap /dev/sda6
/dev/sda6: Device or resource busy
root@Hawaiian:~# echo "RESUME=UUID=830682aa-76e0-4d12-97a3-a3bd64b74128" > /etc/initramfs-tools/conf.d/resume
root@Hawaii:~# echo "cryptswap1 /dev/sda6 /dev/urandom swap,cipher=aes-cbc-essiv:sha256" > /etc/crypttab
root@Hawaii:~# update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.13.0-35-generic
root@Hawaii:~# 

```

I'm attaching a screnshot from Gparted as well.

---

### Post by maglin2 on 2014-09-06
It didn't work for me either (xubuntu 14.04).   I don't know when this will be fixed (or how I would know that it had been), and have gone back to ubuntu 12.04 for now, since swap unencrypted seems to rather defeat the purpose of encrypting.   I guess I could do without swap, but I have seen it used, even running xubuntu with 4gb of RAM.

---

