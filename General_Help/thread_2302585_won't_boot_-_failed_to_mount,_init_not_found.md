---
title: "won't boot - failed to mount, init not found"
date: 2015-11-11
forum: General Help
---

### Post by michalsniezko on 2015-11-11
i have windows 8.1installed alongside ubuntu.
i wanted to upgrade from 14.04lts to 15.04. 
after reboot i got this:
[IMG]http://x3.cdn03.imgwykop.pl/c3201142/comment_Roq8fTVKCbfqXCFrnriNmjDtYRgOvEB9.jpg[/IMG]

I am currently on livecd 15.04 - I wanted to reinstall, but got this:
[IMG]http://x3.cdn03.imgwykop.pl/c3201142/comment_5Dr2MDIqJHHMfTwvmtuuVBRMK9fCqHaE.jpg[/IMG]




** ubuntu@ubuntu:~$ lsblk**
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 931.5G  0 disk 
&#9500;&#9472;sda1   8:1    0   600M  0 part 
&#9500;&#9472;sda2   8:2    0   300M  0 part 
&#9500;&#9472;sda3   8:3    0   128M  0 part 
&#9500;&#9472;sda4   8:4    0 816.6G  0 part 
&#9500;&#9472;sda5   8:5    0  16.2G  0 part 
&#9500;&#9472;sda6   8:6    0  89.8G  0 part /mnt
&#9492;&#9472;sda7   8:7    0   7.9G  0 part [SWAP]
sdb      8:16   1   7.5G  0 disk 
&#9492;&#9472;sdb1   8:17   1   7.5G  0 part /cdrom
sr0     11:0    1  1024M  0 rom

sr1     11:1    1    96M  0 rom  /media/ubuntu/U3 System
loop0    7:0    0     1G  1 loop /rofs

**ubuntu@ubuntu:~$ sudo fdisk -l**

Disk /dev/loop0: 1 GiB, 1101672448 bytes, 2151704 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: BE600C5E-9E7A-4918-A11D-E1696EAC19E2

Device          Start        End    Sectors   Size Type
/dev/sda1        2048    1230847    1228800   600M Windows recovery environment
/dev/sda2     1230848    1845247     614400   300M EFI System
/dev/sda3     1845248    2107391     262144   128M Microsoft reserved
/dev/sda4     2107392 1714659327 1712551936 816.6G Microsoft basic data
/dev/sda5  1919459328 1953523711   34064384  16.2G Windows recovery environment
/dev/sda6  1714659328 1902905343  188246016  89.8G Linux filesystem
/dev/sda7  1902905344 1919459327   16553984   7.9G Linux swap

Partition table entries are not in disk order.
Disk /dev/sdb: 7.5 GiB, 8036285952 bytes, 15695871 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *     2048 15693823 15691776  7.5G  b W95 FAT32


please help

---

### Post by yancek on 2015-11-11
Why would you want to upgrade to 15.04 when support for it ends in January, 2016 and 14.04 will be supported until April, 2019?  What exactly doesn't work?  You have windows installed UEFI so you must install Ubuntu UEFI and if you are doing a complete install I beleive you need to select the Something Else option.  Don't use UEFI so someone else may have mroe specific advice.

---

