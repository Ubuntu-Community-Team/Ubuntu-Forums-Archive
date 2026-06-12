---
title: "I lost capability to write to my second internal hard drive"
date: 2013-01-27
forum: General Help
---

### Post by artificialname on 2013-01-27
hi

I've been playing around with SAMBA and fstab and I've broken something

I have a desktop box with 2 internal hard drives. My smaller drive is the one my system boots from and i can read and write to it

my larger drive I can no longer write to. I can read from it. it is called sdb1 or "datadrive". how do i restore the ability to write to it?

---

### Post by The Cog on 2013-01-27
To start off with, please can you open a terminal, run these commands and post the output here. It shoud help work out what's going on.
```
sudo fdisk -l
cat /etc/fstab
mount
```

---

### Post by artificialname on 2013-01-27
> **The Cog said:**
> To start off with, please can you open a terminal, run these commands and post the output here. It shoud help work out what's going on.
```
sudo fdisk -l
cat /etc/fstab
mount
```




THANK YOU SO MUCH FOR YOUR HELP!!!!!! I love the Ubuntu community!!

(BTW I am 99% sure sdb1 is the name of the drive I am having problems with. I derived it from "disk utility". I am 100% sure that "datadrive" is the drive with the problem) 

Here are the results:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000104b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9d015d38

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    c  W95 FAT32 (LBA)
yweiner@yweiner-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# / was on /dev/sda1 during installation
UUID=47d96fe6-d05c-4045-90be-0e3d91e05f00  /               ext3         relatime,errors=remount-ro  0  1  
# swap was on /dev/sda5 during installation
UUID=2b49b6be-5022-479b-a995-2fb0711b2706  none            swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8    0  0  
/dev/sdb1                                  /media/sdb1     vfat         defaults                    0  0  
yweiner@yweiner-desktop:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sdb1 on /media/sdb1 type vfat (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/yweiner/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=yweiner)

---

### Post by prodigy_ on 2013-01-27
What kind of error message do you get?

I see that your sdb1 is FAT32 formatted. A poor choice for a system that doesn't even have Windows installed but it should still work. One caveat here is that you can't place any file larger than 4GB on FAT32.

---

### Post by artificialname on 2013-01-27
Errors:

"create folder" in the file menu is greyed out

"paste" is greyed out (after i click "copy)

when i try to save as an open office word file to the "DATADRIVE" (which I think is sdb1) I get the error message "Error saving the document Untitled1: /media/sdb1/untitled1.odt does not exist"

when i try to save a gedit file there i get the error "could not save...you do not have the permission necessary to save the file. please check that you typed the location correctly and try again"

I can play .avi files on that drive

---

### Post by prodigy_ on 2013-01-27
You probably need to change the ```
/dev/sdb1 /media/sdb1 vfat defaults 0 0 
``` line in your **/etc/fstab** to something like this: ```
/dev/sdb1 /media/sdb1 vfat defaults,uid=1000,gid=1000 0 0
``` Note that your **uid** and **gid** can be different (1000 is the default). You can find out using the following commands: ```
id -u # Your UID
id -g # Your GID
```

---

### Post by artificialname on 2013-01-27
thanks. i will change 
/dev/sdb1 /media/sdb1 vfat defaults 0 0

to
/dev/sdb1 /media/sdb1 vfat defaults,uid=1000,gid=1000 0 0


i dont understand what to do with the output of these commands:
id -u
id -g

---

### Post by prodigy_ on 2013-01-27
They tell you your actual user ID (uid) and primary group ID (gid). Example:
```
$id -u
1002
$id -g
1005
```
In this case your need to change the values in the fstab line to uid=1002,gid=1005.

---

### Post by artificialname on 2013-01-27
> **prodigy_ said:**
> You probably need to change the ```
/dev/sdb1 /media/sdb1 vfat defaults 0 0 
``` line in your **/etc/fstab** to something like this: ```
/dev/sdb1 /media/sdb1 vfat defaults,uid=1000,gid=1000 0 0
``` Note that your **uid** and **gid** can be different (1000 is the default). You can find out using the following commands: ```
id -u # Your UID
id -g # Your GID
```
It worked! thanks for all your help!

---

### Post by rnerwein on 2013-01-27
> **artificialname said:**
> thanks. i will change 
/dev/sdb1 /media/sdb1 vfat defaults 0 0

to
/dev/sdb1 /media/sdb1 vfat defaults,uid=1000,gid=1000 0 0


i dont understand what to do with the output of these commands:
id -u
id -g
hi
the "id" command in the terminal just show you your "user, group ....."  membership.
this is importent to access the files on your system "user-groub-outer" 
send an output of: mount, ls -d /your_mont_point and ls -l /your_mount_piont.
id -a "would be nice too"
chears
just an explaniton. to see the "really mount options" is to use the mount command to see it.  the only way to see it - it the system sees it.
dosen't matter what's in your fstab.
cheers again

---

