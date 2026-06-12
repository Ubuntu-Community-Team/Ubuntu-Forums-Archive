---
title: "mount/unmount disagrees with the fstab?"
date: 2007-06-12
forum: General Help
---

### Post by traxk on 2007-06-12
I have severals volumes on the desktop and can`t move or remove them. I am running Ubuntu Feisty Fawn and since last kernel update it starts (boot) only in recovery-mode. A copy of the results after running this code: "df -h cat /etc/fstab sudo fdisk -l" included with this post.


jacob@jacob:~$ df -h
Filesystem Size Used Avail Use% Mounted on
/dev/sda13 43G 3,2G 37G 8% /
varrun 506M 104K 505M 1% /var/run
varlock 506M 0 506M 0% /var/lock
procbususb 506M 136K 505M 1% /proc/bus/usb
udev 506M 136K 505M 1% /dev
devshm 506M 0 506M 0% /dev/shm
lrm 506M 33M 473M 7% /lib/modules/2.6.20-16-generic/volatile
/dev/sda1 43G 15G 29G 33% /media/sda1
/dev/sda10 1,1G 35M 1006M 4% /media/sda10
/dev/sda5 3,9G 240M 3,5G 7% /media/sda5
/dev/sda6 17G 52K 16G 1% /media/sda6
/dev/sda8 2,2G 1,8G 262M 88% /media/sda8
/dev/sda9 1,6G 124M 1,4G 9% /media/sda9
jacob@jacob:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda13
UUID=8f529fd5-1b0f-4156-93fe-c4a5195d9942 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda1
UUID=FE48F8F748F8B00F /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda10
UUID=5e30a92f-5021-45ad-ba35-905050fb9e3f /media/sda10 ext3 defaults 0 2
# /dev/sda4
UUID=5CFC797AFC794F70 /media/sda4 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda5
UUID=42d1e855-9209-4999-b688-f93d293e2ad2 /media/sda5 ext3 defaults 0 2
# /dev/sda6
UUID=a1a2ac05-af41-4d9b-9397-0dacee9e2685 /media/sda6 ext2 defaults 0 2
# /dev/sda8
UUID=1573f174-6b9d-431b-8082-321e5f9d624c /media/sda8 ext3 defaults 0 2
# /dev/sda9
UUID=8c1ff1c1-c043-4040-9b47-7b8ff76dd7fd /media/sda9 ext3 defaults 0 2
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
jacob@jacob:~$ sudo fdisk -l
Password:

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 * 1 5609 45054261 7 HPFS/NTFS
/dev/sda2 5610 16942 91032322+ 5 Extended
/dev/sda3 16943 19452 20161575 83 Linux
/dev/sda5 5610 6118 4088511 83 Linux
/dev/sda6 6119 8286 17414428+ 83 Linux
/dev/sda7 10455 10584 1044193+ 82 Linux swap / Solaris
/dev/sda8 10585 10867 2273166 83 Linux
/dev/sda9 10868 11076 1678761 83 Linux
/dev/sda10 11077 11218 1140583+ 83 Linux
/dev/sda11 8287 9370 8707198+ 83 Linux
/dev/sda12 9371 10454 8707198+ 83 Linux
/dev/sda13 11219 16827 45054261 83 Linux
/dev/sda14 16828 16942 923706 82 Linux swap / Solaris

Partition table entries are not in disk order
jacob@jacob:~$ df -h
Filesystem Size Used Avail Use% Mounted on
/dev/sda13 43G 3,2G 37G 8% /
varrun 506M 104K 505M 1% /var/run
varlock 506M 0 506M 0% /var/lock
procbususb 506M 136K 505M 1% /proc/bus/usb
udev 506M 136K 505M 1% /dev
devshm 506M 0 506M 0% /dev/shm
lrm 506M 33M 473M 7% /lib/modules/2.6.20-16-generic/volatile
/dev/sda1 43G 15G 29G 33% /media/sda1
/dev/sda10 1,1G 35M 1006M 4% /media/sda10
/dev/sda5 3,9G 240M 3,5G 7% /media/sda5
/dev/sda6 17G 52K 16G 1% /media/sda6
/dev/sda8 2,2G 1,8G 262M 88% /media/sda8
/dev/sda9 1,6G 124M 1,4G 9% /media/sda9
jacob@jacob:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda13
UUID=8f529fd5-1b0f-4156-93fe-c4a5195d9942 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda1
UUID=FE48F8F748F8B00F /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda10
UUID=5e30a92f-5021-45ad-ba35-905050fb9e3f /media/sda10 ext3 defaults 0 2
# /dev/sda4
UUID=5CFC797AFC794F70 /media/sda4 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda5
UUID=42d1e855-9209-4999-b688-f93d293e2ad2 /media/sda5 ext3 defaults 0 2
# /dev/sda6
UUID=a1a2ac05-af41-4d9b-9397-0dacee9e2685 /media/sda6 ext2 defaults 0 2
# /dev/sda8
UUID=1573f174-6b9d-431b-8082-321e5f9d624c /media/sda8 ext3 defaults 0 2
# /dev/sda9
UUID=8c1ff1c1-c043-4040-9b47-7b8ff76dd7fd /media/sda9 ext3 defaults 0 2
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
jacob@jacob:~$ sudo fdisk -l

Can someone help, thanks
Jacob

---

