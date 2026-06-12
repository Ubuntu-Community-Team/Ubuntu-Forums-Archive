---
title: "external hard drive - Error while copying to &quot;/media/disk&quot;"
date: 2008-03-14
forum: General Help
---

### Post by kronictokr on 2008-03-14
my external drive has been formated in 2 partitions

after i formated the drive these "lost+found" folder apears and i dont have permision to access or delete them??

ext3  and fat32  its seems i can only access one drive at a time, and i have no real control of which i can use.  exept if i unmount the active partion, i think the other (active without permision) takes its place and allows permision. at that point the oposite drives looses it permission??

i need to allow simultaneous access to both partitions on the external drive, i think

kronictokr@kronictokr-laptop:~$ sudo fdisk -l
[sudo] password for kronictokr:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa315a315

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12022    96566683+  83  Linux
/dev/sda2           12023       12161     1116517+   5  Extended
/dev/sda5           12023       12161     1116486   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00085167

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19301   155035251   83  Linux
/dev/sdb2           19302       38913   157533390    b  W95 FAT32
kronictokr@kronictokr-laptop:~$ 




kronictokr@kronictokr-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e9dc89e9-da78-4783-a3b6-c8d5722be454 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=17aafaf8-35ba-40b0-b743-a346c83c77c1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
kronictokr@kronictokr-laptop:~$ 


let me know if you need anymore info, tx for any help

---

### Post by taurus on 2008-03-14
Do

```
sudo umount /dev/sdb1 /dev/sdb2
sudo mkdir /media/sdb1 /media/sdb2
sudo mount -t ext3 /dev/sdb1 /media/sdb1
sudo mount -t vfat /dev/sdb2 /media/sdb2 -o umask=000
sudo chown -R **kronic**:**kronic** /media/sdb1
ls -la /media
```
_Assuming_ **kronic** is your login name.

---

### Post by kronictokr on 2008-03-14
do i have to enter the commands individually or copy paste into terminal?

my third day on linux :)

also i tried pluging the external into my xbox 360 to play a movie in a format the was streaming off xp just fine. it read my drive but not the movie file.
when i plugged the external hard drive back into my cpu, the fat32 partition that had previously contained a movie file contains thes three errors

<b>Could not open the file <i>/media/sdb2/&#x1;?</i>.</b>

<b>Could not open the file <i>/media/sdb2/&#x2;q</i>.</b>

<b>Could not open the file <i>/media/sdb2/&#x1;w</i>.</b>

just incase ill give you these again, and since my 360 reads fat32, should the first partion be fat32 and ext3 the second?

kronictokr@kronictokr-laptop:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa315a315

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12022    96566683+  83  Linux
/dev/sda2           12023       12161     1116517+   5  Extended
/dev/sda5           12023       12161     1116486   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00085167

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19301   155035251   83  Linux
/dev/sdb2           19302       38913   157533390    b  W95 FAT32




kronictokr@kronictokr-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e9dc89e9-da78-4783-a3b6-c8d5722be454 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=17aafaf8-35ba-40b0-b743-a346c83c77c1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by taurus on 2008-03-14
If you don't feel like typing, just cut 'n paste each command into a terminal and hit Return.  Remember, run one command at a time.

---

### Post by kronictokr on 2008-03-14
ok heres the results of the commands you gave me

kronictokr@kronictokr-laptop:~$ sudo mkdir /media/sdb1 /media/sdb2
mkdir: cannot create directory `/media/sdb1': File exists
mkdir: cannot create directory `/media/sdb2': File exists
kronictokr@kronictokr-laptop:~$ sudo mount -t ext3 /dev/sdb1 /media/sdb1
kronictokr@kronictokr-laptop:~$ sudo mount -t vfat /dev/sdb2 /media/sdb2 -o umask=000
kronictokr@kronictokr-laptop:~$ sudo chown -R kronictokr:kronictokr /media/sdb1
kronictokr@kronictokr-laptop:~$ ls -la /media
total 32
drwxr-xr-x  5 root       root        4096 2008-03-14 04:18 .
drwxr-xr-x 21 root       root        4096 2008-03-13 10:20 ..
lrwxrwxrwx  1 root       root           6 2008-03-13 09:50 cdrom -> cdrom0
drwxr-xr-x  2 root       root        4096 2008-03-13 09:50 cdrom0
-rw-r--r--  1 root       root           0 2008-03-14 04:18 .hal-mtab
-rw-------  1 root       root           0 2008-03-14 04:11 .hal-mtab-lock
drwxr-xr-x  3 kronictokr kronictokr  4096 2008-03-13 18:24 sdb1
drwxrwxrwx  2 root       root       16384 1969-12-31 17:00 sdb2



btw thanks, looks like it did something going to check now :)

---

### Post by kronictokr on 2008-03-14
the codes you gave me above worked, tx so much. on to another thread for the rest, will post this as solved.  feel free to help on my new threads to be posted :)

in a few minutes :)

tx sooooooo much

how do i make it solved ?

---

### Post by kronictokr on 2008-03-14
the above solution worked, however gparted does not after applying it.  when i try to start gparted it just keeps searching and eventually shuts my laptop down


this is the code that was used, to to enable me to access my external hard drive
it worked but due to another issue i wanted to reformat my external hd, and cant

sudo umount /dev/sdb1 /dev/sdb2
sudo mkdir /media/sdb1 /media/sdb2
sudo mount -t ext3 /dev/sdb1 /media/sdb1
sudo mount -t vfat /dev/sdb2 /media/sdb2 -o umask=000
sudo chown -R kronic:kronic /media/sdb1
ls -la /media

please help :)

---

### Post by taurus on 2008-03-14
You cannot format a partition or drive when it's mounted or in used.  You first need to unmount it before you can format it.  And if it is / filesystem, then you need to run gparted from the LiveCD or GParted LiveCD.

---

### Post by kronictokr on 2008-03-15
got the external hardrive formated, just a note if anyone else is having problems formating using parttition editor.   with my system i could not format the whole drive at one time(300gb) .  i had to do it half at a time.


completely formated the drive to fat32 and my xbox360 reads it no problem 

thanks for all your help :)

---

