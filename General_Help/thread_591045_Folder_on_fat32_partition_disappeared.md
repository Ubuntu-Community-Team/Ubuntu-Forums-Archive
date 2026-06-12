---
title: "Folder on fat32 partition disappeared"
date: 2007-10-25
forum: General Help
---

### Post by merike on 2007-10-25
I have my hda5 partition mounted as Meedia. Under that I had a folder with my study materials. Folder was created several weeks ago and had some files in it.
Yesterday I saved one new .odt document in that folder and one document directly in /media/Meedia. Today morning when I logged in my folder was gone. hda5 is mounted, I can open the document saved outside that folder, but my folder doesn't show up at all. I can't do cd /media/Meedia/myfolder, because it isn't there. I haven't got any errors recently so I have no idea, what happened to it. I haven't issued any delete command either.
I remember the exact filename I was using so I tried locate but it only got me /home/merike/.kde/shareapps/RecentDocuments/filename.desktop.desktop and /home/merike/.kde/shareapps/RecentDocuments/filename.desktop.desktop.desktop. For the other file I also have filename.odt.desktop but for this one I don't.
How could I recover the file assuming it is written to the disk which I think is the case, but not shown anywhere?

---

### Post by -Zeus- on 2007-10-25
When you wrote the data to it, did you pull the drive out right afterwards (without a "unmount"")

---

### Post by merike on 2007-10-25
No. hda5 is just a partition on my one and only hard drive.

---

### Post by taurus on 2007-10-25
Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
df -h
ls -la /media
```

---

### Post by merike on 2007-10-25
```

sudo fdisk -l
Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = silindrit of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20cbd119

    Seade Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1567    12586896    7  HPFS/NTFS
/dev/hda2            1568        3366    14450467+   5  Extended
/dev/hda3            3367        4864    12032685   83  Linux
/dev/hda5            1568        2872    10482381    b  W95 FAT32
/dev/hda6            2873        3297     3413781    b  W95 FAT32
/dev/hda7            3298        3366      554211   82  Linux swap / Solaris

cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=baf046e7-adaf-45e8-baa6-74d92771e698 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda7
UUID=fb038742-5b03-497f-a6ee-a41da87d68f6 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
#Meedia
/dev/hda5       /media/Meedia   vfat    umask=0,iocharset=utf8  0       0

df -h
Failisüsteem            Maht Kasut  Vaba Kas% Haagitud
/dev/hda3              12G  2,6G  8,2G  24% /
varrun                 94M  144K   94M   1% /var/run
varlock                94M     0   94M   0% /var/lock
udev                   94M   72K   94M   1% /dev
devshm                 94M     0   94M   0% /dev/shm
lrm                    94M   34M   60M  37% /lib/modules/2.6.22-14-generic/volatile
/dev/hda5              10G  1,2G  8,9G  12% /media/Meedia

ls -la /media
kokku 20
drwxr-xr-x  4 root root 4096 2007-10-25 14:47 .
drwxr-xr-x 21 root root 4096 2007-10-21 23:38 ..
lrwxrwxrwx  1 root root    6 2007-10-21 23:06 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2007-10-21 23:06 cdrom0
lrwxrwxrwx  1 root root   45 2007-10-21 23:47 .directory -> /etc/kubuntu-default-settings/directory-media
-rw-r--r--  1 root root    0 2007-10-25 14:47 .hal-mtab
lrwxrwxrwx  1 root root   42 2007-10-21 23:47 .hidden -> /etc/kubuntu-default-settings/hidden-media
drwxrwxrwx  9 root root 8192 2007-10-25 17:12 Meedia

ls -la /media/Meedia
kokku 843188
drwxrwxrwx 11 root root      8192 2007-10-25 18:16 .
drwxr-xr-x  4 root root      4096 2007-10-25 14:47 ..
drwxrwxrwx  2 root root      8192 2007-10-25 18:14 c
-rwxrwxrwx  1 root root 134541312 2007-10-21 11:20 core.7966
-rwxrwxrwx  1 root root        78 2007-03-02 10:23 Desktop.ini
-rwxrwxrwx  1 root root     30386 2007-10-25 00:11 encoding.odt
-rwxrwxrwx  1 root root       426 2007-10-17 12:06 erialatutvustus.txt
-rwxrwxrwx  1 root root    100352 2007-03-08 21:53 example.doc
-rwxrwxrwx  1 root root     45568 2006-12-20 06:00 fetnd5bv.sys
-rwxrwxrwx  1 root root      4614 2007-10-18 09:38 hydrogen_energy.txt
-rwxrwxrwx  1 root root      4034 2007-10-17 23:07 hydrogen_energy.txt~
drwxrwxrwx  2 root root      8192 2007-10-25 17:11 java
-rwxrwxrwx  1 root root 727867392 2007-10-16 15:15 kubuntu-7.04-desktop-i386.iso
drwxrwxrwx  2 root root      8192 2007-10-25 18:15 linux
-rwxrwxrwx  1 root root        25 2007-03-24 11:06 mac_address.txt
-rwxrwxrwx  1 root root        63 2007-10-16 14:36 md5-kubuntu.txt
-rwxrwxrwx  1 root root       178 2007-10-21 11:20 Meedia
-rwxrwxrwx  1 root root      5752 2007-05-27 22:41 My Favorite Theme.theme
dr-xr-xr-x  4 root root      8192 2007-05-21 14:51 My Music
-rwxrwxrwx  1 root root         0 2007-03-10 13:16 network.txt
-rwxrwxrwx  1 root root    133538 2007-10-21 11:20 octave-core
-rwxrwxrwx  1 root root        29 2007-03-01 22:09 office_trial.txt
drwxrwxrwx  2 root root      8192 2007-10-25 17:12 php
drwxrwxrwx  2 root root      8192 2007-06-07 08:33 Recycled
-rwxrwxrwx  1 root root       811 2007-10-21 11:20 search.txt
-rwxrwxrwx  1 root root    488992 2006-03-22 16:27 shp5211.sys
drwxrwxrwx  2 root root      8192 2007-10-25 17:12 side
drwxrwxrwx  2 root root      8192 2007-10-15 10:07 sis
drwxrwxrwx  3 root root      8192 2007-04-30 22:18 System Volume Information
-rwxrwxrwx  1 root root         0 2007-10-25 18:16 text.txt
-rwxrwxrwx  1 root root      5770 2007-10-21 11:21 tulemused.txt
-rwxrwxrwx  1 root root       853 2007-10-14 22:33 tulemus.txt
-rwxrwxrwx  1 root root        13 2007-03-03 12:05 x-win32.txt

```
encoding.odt is the file saved right after the first one. The missing folder was named English and my saved file dustbin.odt Now there's neither English folder nor dustbin.odt in it.

---

