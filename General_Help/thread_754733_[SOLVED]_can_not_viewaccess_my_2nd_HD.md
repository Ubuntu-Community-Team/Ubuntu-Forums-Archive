---
title: "[SOLVED] can not view/access my 2nd HD"
date: 2008-04-14
forum: General Help
---

### Post by seefor on 2008-04-14
Hello just want to say Ubuntu is a great OS. I'm new to Linux. :lolflag:
I have 2 HD one is a 40GB where Ubuntu 8.04 Beta is installed.
The 2nd HD is all data files: Movies, Music, Pictures..etc.

I can't figure out how to mount the HD, any help would greatly be appreciated.:)

> Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc7ccc7cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x424e4198

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001   42  SFS
abaksh@abaksh-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=77f426f8-7b8e-4d72-ba77-6755ddd810f4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=83a6a31d-3457-46f3-902b-faf24d6b495a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
abaksh@abaksh-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              36G  4.5G   29G  14% /
varrun               1010M  100K 1010M   1% /var/run
varlock              1010M     0 1010M   0% /var/lock
udev                 1010M   52K 1010M   1% /dev
devshm               1010M   12K 1010M   1% /dev/shm
lrm                  1010M   38M  973M   4% /lib/modules/2.6.24-16-generic/volatile

](*,)

---

### Post by schnittchen on 2008-04-14
Hi seefor,

if your second disk is static, you will definitely want to put an appropriate line into /etc/fstab.
According to your partition table, you have only one partition of type SFS, and I have never seen that before. Could you please do a

sudo file -f /dev/sdb1

to ensure you can configure for the right thing? This should tell you both the filesystem type and, if present, the UUID.
Where does this filesystem come from, a previous linux system or some flavour of windows?

---

### Post by seefor on 2008-04-14
The Drive was previously in my XP box which is now Ubuntu :)
It was partition with NTFS.
When I run the command sudo file -f /dev/sdb1 it just sits there nothing happen after 20 minutes.

Please advise.

Thanks for you help schnittchen :)

---

### Post by seefor on 2008-04-14
I found something that fixed mine connecting to the HD: 
I was doing the same in Ubuntu, I knew I'd formatted the drive in Windows 2000 so I guessed it would work as NTFS, despite fdisk saying SFS... I mounted mine like so (using [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy) as a guide):

sudo mkdir /media/windows
sudo mount /dev/sdb1 /media/windows/ -t ntfs -o nls=utf8,umask=0222 -o force

I had to use"-o force" to mount the HD.

mounted okay, browsed the system fine.

I got it from this link [http://forum.linux-ntfs.org/viewtopic.php?t=555]("http://forum.linux-ntfs.org/viewtopic.php?t=555")

It's up and running and I can RW to the drive now.

Thanks :) :lolflag: :lolflag:

---

### Post by schnittchen on 2008-04-15
For the future, you might want to change the partition type of your ntfs partition to something like 86 or 87 (hex code, don't know which is better) so that you see from the partition table what you expect there.

You can do so with fdisk (press "t" for that function), but BE CAREFUL!
I recommend making a backup of your partition table if you are unsure of what you are doing.

Pressing "m" for help might be useful as well ;-)

---

