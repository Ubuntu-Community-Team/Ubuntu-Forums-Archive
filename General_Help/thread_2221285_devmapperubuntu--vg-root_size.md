---
title: "/dev/mapper/ubuntu--vg-root size"
date: 2014-05-01
forum: General Help
---

### Post by n07ba012 on 2014-05-01
I had removed automatically created (by the installer) swap partition (12G of RAM, I don't need it) and changed the size of /dev/ubuntu-vg/root.

Here is my question:

1) sudo parted -l
Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size   File system  Name                  Flags
 1      1049kB  538MB  537MB  fat32        EFI System Partition  boot
 2      538MB   794MB  256MB  ext2
 3      794MB   128GB  127GB                                     lvm


Model: ATA SanDisk SSD i100 (scsi)
Disk /dev/sdb: 24,0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  24,0GB  24,0GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 127GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0,00B  127GB  127GB  ext4

2) sudo lvscan
  ACTIVE            '/dev/ubuntu-vg/root' [118,50 GiB] inherit

3) sudo df -h
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  105G  9,3G   91G  10% /
none                         4,0K     0  4,0K   0% /sys/fs/cgroup
udev                         5,8G   12K  5,8G   1% /dev
tmpfs                        1,2G  1,1M  1,2G   1% /run
none                         5,0M     0  5,0M   0% /run/lock
none                         5,8G  812K  5,8G   1% /run/shm
none                         100M   96K  100M   1% /run/user 
/dev/sda2                    237M   53M  172M  24% /boot
/dev/sda1                    511M  3,4M  508M   1% /boot/efi

I have to admit that I'm newbie to LVM. I wonder why the size of /dev/mapper/ubuntu--vg-root (3 - df-h) is different from the size of the /dev/ubuntu-vg/root (2 - lvscan)? Is that supposed to be? Hope not. I wanted to retrieve space occupied by the swap partition, and I have the impression that it has not succeeded. In a nutshell - where is my 13.5 GB? How to make / partition to be 118,5G, not 105G?

---

