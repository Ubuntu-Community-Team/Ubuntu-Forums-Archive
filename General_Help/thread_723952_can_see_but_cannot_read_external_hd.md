---
title: "can see but cannot read external hd"
date: 2008-03-14
forum: General Help
---

### Post by kronictokr on 2008-03-14
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
/dev/sdb1               1       38913   312568641    b  W95 FAT32








kronictokr@kronictokr-laptop:~$  cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e9dc89e9-da78-4783-a3b6-c8d5722be454 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=17aafaf8-35ba-40b0-b743-a346c83c77c1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0







kronictokr@kronictokr-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              91G   32G   56G  37% /
varrun                187M   92K  187M   1% /var/run
varlock               187M     0  187M   0% /var/lock
udev                  187M   80K  187M   1% /dev
devshm                187M     0  187M   0% /dev/shm
lrm                   187M   38M  149M  21% /lib/modules/2.6.22-14-generic/volatile




willing to format the drive but gparted wont read it, was actually trying to format when i lost it. clicked at the wrong time....
please help. its my second day with linux

---

### Post by Rocket2DMn on 2008-03-14
In GParted you should be able to select the drive from the top right, right click the sdb1 partition and select to unmount it, then format it with your choice of file systems.  If it still doesn't work, try the GParted LiveCD - [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by kronictokr on 2008-03-14
ok, that worked. thank you :)

i formated my in two parts 

first part ext3 almost half

second small part it the middle (was thinking of formating to swap)just i new, and just wanted to make sure if i needed to copy my file to swap before fat 32 for readability. but i dont really know.;p
 
third almost half
fat32

im new, and just wanted to make sure if i needed to copy my file to swap before fat 32 for readability. but i dont really know.;p
 

however

ext3 mounts fine , can use it so far no problem

fat 32 detects fine, but i cant add files to it though(says i dont have permision).  the reason for the fat32 is because thats the format that works with my xbox 360

-can you help me be able to access my fat32 partition

-should i put a swap partition in the middle of the two, or something else?

Also on another topic, i just installed this program two days ago. i really like it , but a couple bugs i gotta fix. kinda fun though hehe. 
oh yeah , my cd/dvd burner is not working. since my drive is problematic the drive typa and model are posted in the following screenshot. tx again in advance

---

### Post by Rocket2DMn on 2008-03-14
You don't need a second swap partition - you already have swap on sda5.  In order to help you mount I need some more information, please post the outputs of:
```
sudo fdisk -l
cat /etc/fstab
```
(fstab will probably be the same as above, but fdisk will have changed).  If you have a preferred mount point for each of the new partitions under /media/[something], say so, otherewise I'll make something up for you.

---

### Post by kronictokr on 2008-03-14
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
 


here you go sir, sorry i noticed my topic is a little off, i believe its mounted, says i dont have permission though?

---

### Post by Rocket2DMn on 2008-03-14
There is no /dev/sdb drive - is it plugged in? It needs to be before you run the fdisk command.
Also I just remembered your drive is external, so we won't be adding an fstab entry for it.  We will mount it from the terminal.  Please post the fdisk command again with the drive plugged in.

---

### Post by kronictokr on 2008-03-14
here we go


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





Error while copying to "/media/disk"
it seems i am only permiting one partition of the drive at a time. now i can copy into the fat32 partition, but am getting the "you do not have permission to write to this folder"   for the other partition

---

### Post by Rocket2DMn on 2008-03-14
I changed my mind about using fstab, it will be easier to use fstab since you have these problems.  First we will unmount the partitions, make mount points for them, add fstab entries for them, then mount them.  Where I say /media/usb1 or 2, you may change that do the mount point of your preference, like /media/[something_else] - the mount point just has to exist before you attempt to mount.
```
sudo umount /dev/sdb1
sudo umount /dev/sdb2
sudo mkdir /media/usb1
sudo mkdir /media/usb2
gksudo gedit /etc/fstab
```

Now editing fstab, add the following lines, then save and close:
```
/dev/sdb1 /media/usb1 ext3 defaults 0 0
/dev/sdb2 /media/usb2 vfat defaults,users,exec,uid=1000,gid=100,umask=007 0 0
```

Then let's mount the partitions, and have it set you as the owner of the ext3 partition:
```
sudo mount -a
sudo chown -R /media/usb1
```

From now on, if the drive doesn't automount when you plug it in, you just need to run
```
sudo mount -a
``` and then the partitions will get mounted.

If you still have problems, post the output here and we'll tweak the settings.  If you want to fiddle with fstab yourself, here's a useful guide: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by kronictokr on 2008-03-14
hi thank you for your response. i had to refind this post.  

another forum member "taurus" helped me out, im new and its a little easier my me, for now anyway :)  tx you both


this worked

sudo umount /dev/sdb1 /dev/sdb2
sudo mkdir /media/sdb1 /media/sdb2
sudo mount -t ext3 /dev/sdb1 /media/sdb1
sudo mount -t vfat /dev/sdb2 /media/sdb2 -o umask=000
sudo chown -R kronic:kronic /media/sdb1
ls -la /media

---

