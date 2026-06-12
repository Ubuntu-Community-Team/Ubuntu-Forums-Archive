---
title: "TimeShift BTRFS, unsupported subvolume layout @ and @home"
date: 2024-08-30
forum: General Help
---

### Post by webmanoffesto on 2024-08-30
I'm on a new clean install of Ubuntu 24. I like the BTRFS because I can use TimeShift.
But I'm getting error messages.
First TimeShift said there wasn't a "root subvolume (@)".
I tried to create it.

sudo btrfs subvolume create /@

$ sudo btrfs subvolume list /
[sudo] password for tom: 
ID 256 gen 101 top level 5 path @


df -h
Filesystem      Size  Used Avail Use% Mounted on
tmpfs           3.2G  2.8M  3.1G   1% /run
/dev/nvme0n1p2   75G   11G   63G  15% /
tmpfs            16G  4.0K   16G   1% /dev/shm
tmpfs           5.0M   12K  5.0M   1% /run/lock
efivarfs        192K  117K   71K  63% /sys/firmware/efi/efivars
/dev/nvme0n1p3  857G  1.1G  854G   1% /home
/dev/nvme0n1p1  300M  6.2M  294M   3% /boot/efi
tmpfs           3.2G  2.6M  3.1G   1% /run/user/1000

I thought I was making progress but now I get 
"Not Supported
The system partition has an unsupported subvolume layout. Only ubuntu type layouts with @ and @home are currently supported. Application with exit.

How do I fix this?

I'm already getting settled in on my new install. I'd like to do this without having to reformat partitions.

cat /etc/fstab  
# /etc/fstab: static file system information.
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
[FONT=courier new]# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p2 during curtin installation
/dev/disk/by-uuid/f1e62f59-6c04-43f6-89fb-04657f63b39e / btrfs defaults 0 1
# /boot/efi was on /dev/nvme0n1p1 during curtin installation
/dev/disk/by-uuid/7003-CFCF /boot/efi vfat defaults 0 1
# /home was on /dev/nvme0n1p3 during curtin installation
/dev/disk/by-uuid/6f935854-fa76-4791-85c0-20857f686a2d /home btrfs defaults 0 1
[/FONT]

---

