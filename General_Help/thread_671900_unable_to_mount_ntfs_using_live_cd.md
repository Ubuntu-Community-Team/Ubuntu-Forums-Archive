---
title: "unable to mount ntfs using live cd"
date: 2008-01-19
forum: General Help
---

### Post by pro967 on 2008-01-19
Hello,
I have this company laptop Thinkpad T40 with Win XP. While trying to share some files with my home computer I changed the domain name to workgroup. It prompted me to restart which I did. Now it does not let me log back in. Now I have resigned from my job and need to give back the laptop within 3-4 days. I am afraid that if I tell this to our admin he would keep the laptop and I will loose my personal data (which I sould not be having on a company laptop in the first place). This is why I do not want to use admin's help.

To retrieve the data, I used live ubuntu cd and here is what happens:

============================================================================

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
240 heads, 63 sectors/track, 5168 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xa0c4a0c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2032    15361888+   7  HPFS/NTFS
/dev/sda2            2033        5168    23708160    f  W95 Ext'd (LBA)
/dev/sda5            2033        5168    23708128+   7  HPFS/NTFS

ubuntu@ubuntu:~$ sudo mkdir /mnt/windows
ubuntu@ubuntu:~$ sudo mount -t ntfs-3g /dev/sda1 /mnt/windows/
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

Same if I use ntfs instead of ntfs-3g. Same if I use ro or force options

ubuntu@ubuntu:~$ sudo mount -t vfat /dev/sda1 /mnt/windows/
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Here is what I am using:

ubuntu@ubuntu:~$ uname -a
Linux ubuntu 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

============================================================================

Also, if I use gparted to see the partitions it lists sda1 and sda5 partitions as "unknown".

I have googled extensively. Many people with this issue were using incorrect parameters or had corrouped partitions. I think I am using the correct command line parameters. I am sufficiently sure that partitions are not corroupted because I still can boot with XP but cannot login.

Thanks for any help.

---

### Post by pro967 on 2008-01-19
Here is a screen capture from gpareted:

---

### Post by confused57 on 2008-01-19
You could try:
```
sudo mkdir /media/windows
sudo mount /dev/sda1 /media/windows/  -t ntfs -o nls=utf8,umask=0222
```

I don't know why gparted shows the filesystem as unknown...if the above works, your Windows partition is mounted readonly and you should be able to drag & drop files.

---

### Post by pro967 on 2008-01-19
Thank you for your help confused57. It still gives the same output as with my initial command with ntfs-3g.

---

