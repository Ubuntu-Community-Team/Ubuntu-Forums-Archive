---
title: "Mounting partitions"
date: 2008-06-08
forum: General Help
---

### Post by awilki01 on 2008-06-08
I've searched quite a bit here and elsewhere and found many upon many threads on this, but none seem to work for me.

I have two NTFS partitions that I cannot seem to mount.

Here is my fstab config:

```

adam@adam-ubuntu:~$ more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=4e9c07bb-c6c5-4ee1-910f-f1bb41273f78 /               ext3    defaults,error
s=remount-ro 0       1
# /dev/sda1
UUID=F89C30389C2FEFB4 /media/sda1     ntfs    defaults,umask=007,gid=46 0       
1
# /dev/sda5
UUID=B6D412BED4128133 /media/sda5     ntfs    defaults,umask=007,gid=46 0       
1
# /dev/sdb1
UUID=2E8E95880E43FA71 /media/sdb1     ntfs    defaults,umask=007,gid=46 0       
1
# /dev/sdb3
UUID=0733bd47-2ec1-456e-995c-357616648f7a none            swap    sw            
  0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

When I do a 'mount -a', I get the following:
```

adam@adam-ubuntu:~$ sudo mount -a
Failed to access '/dev/disk/by-uuid/F89C30389C2FEFB4': No such file or directory
Failed to access '/dev/disk/by-uuid/B6D412BED4128133': No such file or directory

```

I've also done the "sudo mount /dev/sda1 /media/sda1 -t ntfs -o nls=utf8,umask=0222".  However, when I change directory to the /media/sda1, it is the same partition as my sdb1 - as listed in my Places on the computer file browser.

Any suggestions?

---

### Post by fenian on 2008-06-08
Do the mount points /media/sda1 and /media/sda5 exist if not create them with the commands...

> sudo mkdir /media/sda1
sudo mkdir /media/sda5

---

### Post by awilki01 on 2008-06-08
> **fenian said:**
> Do the mount points /media/sda1 and /media/sda5 exist if not create them with the commands...

They already exist:
```

adam@adam-ubuntu:/media$ ls -la
total 32
drwxr-xr-x  6 root root    4096 2008-06-08 01:44 .
drwxr-xr-x 22 root root    4096 2007-12-31 21:45 ..
lrwxrwxrwx  1 root root       6 2007-12-31 19:24 cdrom -> cdrom0
drwxr-xr-x  2 root root    4096 2007-12-31 19:24 cdrom0
drwxrwx---  1 root plugdev 8192 2008-06-08 01:37 sda1
drwxr-xr-x  2 root root    4096 2007-12-31 19:24 sda5
drwxrwx---  1 root plugdev 8192 2008-06-08 01:37 sdb1

```

Any other suggestions on how to fix this?  Do the rwx properties or user assignments on the directories have any significance?

Is there some way to get Ubuntu to try and rediscover all the drives in a system?

Again, what is really odd is that I can mount sda1, but when I do, it is the EXACT same drive as my sdb1 as indicated in the GUI file browser in Ubuntu.

---

### Post by ibutho on 2008-06-08
You could do do things the old way
```
# /dev/sda1
/dev/sda1    /media/sda1     ntfs    defaults,umask=007,gid=46 0    1
# /dev/sda5
/dev/sda5    /media/sda5     ntfs    defaults,umask=007,gid=46 0    1

```

---

### Post by awilki01 on 2008-06-08
> **ibutho said:**
> You could do do things the old way
```
# /dev/sda1
/dev/sda1    /media/sda1     ntfs    defaults,umask=007,gid=46 0    1
# /dev/sda5
/dev/sda5    /media/sda5     ntfs    defaults,umask=007,gid=46 0    1

```

I tried editing the entry for sda5 exclusively since I didn't want to mess with sda1 - still confused why its showing up as sdb1 in Gnome file browser.

When doing a 'sudo mount -a', I get this now:
```

adam@adam-ubuntu:/media$ sudo mount -a
Failed to access '/dev/disk/by-uuid/F89C30389C2FEFB4': No such file or directory
Failed to access '/dev/sda5': No such file or directory

```


Now, I'm really confused.  Check this out:

```

adam@adam-ubuntu:/media/disk1$ sudo blkid
/dev/sda1: UUID="2E8E95880E43FA71" TYPE="ntfs" 
/dev/sda3: TYPE="swap" UUID="0733bd47-2ec1-456e-995c-357616648f7a" 
/dev/sda2: UUID="4e9c07bb-c6c5-4ee1-910f-f1bb41273f78" SEC_TYPE="ext2" TYPE="ext3" 


```

Where are my other two partitions listed in fstab?  And, why is sda1 showing up in the Gnome file browser as sdb1?


Edit:
I read on another thread about 'ntfs-config' (thread here: [http://ubuntuforums.org/showthread.php?p=5142253#post5142253](http://ubuntuforums.org/showthread.php?p=5142253#post5142253).

I get the following errors:
```

adam@adam-ubuntu:/media$ sudo ntfs-config

** (ntfs-config:32592): WARNING **: Can't find device with uuid = F89C30389C2FEFB4


** (ntfs-config:32592): WARNING **: Can't find device with uuid = B6D412BED4128133

```

Is there somehow a way to re-find my other two partitions?

---

### Post by ibutho on 2008-06-08
Whats the output of running
```
sudo fdisk -l
```

---

### Post by awilki01 on 2008-06-08
> **ibutho said:**
> Whats the output of running
```
sudo fdisk -l
```

Here you go:
```

adam@adam-ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3a923a91

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9485    76188231    7  HPFS/NTFS
/dev/sda2            9486       14462    39977752+  83  Linux
/dev/sda3           14463       14593     1052257+  82  Linux swap / Solaris

```

I know I have other partitions because I'm dual booting with Win XP on a 400 GB drive.  I have a 400 GB SATA drive with two partitions that is not showing up here.

Here is how Win XP sees my drives and partitions.  It's as if my SATA drive (Disk 0) is not even recognized in Ubuntu:

[IMG]http://www.davidadamsmusic.com/images/disks.jpg[/IMG]

---

### Post by awilki01 on 2008-06-17
Anyone have any ideas here?

---

### Post by rzrgenesys187 on 2008-06-17
```

Failed to access '/dev/disk/by-uuid/F89C30389C2FEFB4': No such file or directory
Failed to access '/dev/sda5': No such file or directory
```

When i was working to get my fat32 partition to mount this error seemed to signify that the folder you are trying to mount to (/media/foo) doesn't exist.  if you are trying to mount /dev/sda5 to /media/sda5 try creating a folder called sda5 in /media

```
mkdir /media/sda5
```

then run your mount -a code

---

### Post by awilki01 on 2008-06-17
I have the /media/sda5 directory already created.

I get this:
```

adam@adam-ubuntu:/media/sda5$ sudo mount -a
Failed to access '/dev/disk/by-uuid/F89C30389C2FEFB4': No such file or directory
Failed to access '/dev/disk/by-uuid/B6D412BED4128133': No such file or directory

```

Here is my latest fstab:
```

adam@adam-ubuntu:/dev$ more /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=4e9c07bb-c6c5-4ee1-910f-f1bb41273f78 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=F89C30389C2FEFB4 /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=B6D412BED4128133 /media/sda5 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda1 :
UUID=2E8E95880E43FA71 /media/sdb1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda3 :
UUID=0733bd47-2ec1-456e-995c-357616648f7a none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

```

---

### Post by bodhi.zazen on 2008-06-17
Can you post the output of :

```
sudo blkid
```

and 

```
ls -l /dev/disk/by-uuid/
```

---

### Post by awilki01 on 2008-06-17
Sure, here you go....and thanks!

```

adam@adam-ubuntu:/dev$ sudo blkid
/dev/sda1: UUID="2E8E95880E43FA71" TYPE="ntfs" LABEL="Local Disk" 
/dev/sda3: TYPE="swap" UUID="0733bd47-2ec1-456e-995c-357616648f7a" 
/dev/sda2: UUID="4e9c07bb-c6c5-4ee1-910f-f1bb41273f78" SEC_TYPE="ext2" TYPE="ext3" 

```

```

adam@adam-ubuntu:/dev$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2008-06-17 14:47 0733bd47-2ec1-456e-995c-357616648f7a -> ../../sda3
lrwxrwxrwx 1 root root 10 2008-06-17 14:47 2E8E95880E43FA71 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-06-17 14:47 4e9c07bb-c6c5-4ee1-910f-f1bb41273f78 -> ../../sda2

```

It's as if Linux is not recognizing my SATA drive at all.  Look a few posts up, and you will see what my WinXP sees.  "Disk 0" (in WinXP) is what I'm trying to get recognized in Linux.  There's 400 GB of space there I could really use.

---

### Post by bodhi.zazen on 2008-06-17
Your listing of partitions (sudo fdisk and blkid) is incomplete.

My guess is your partition table is somehow corrupted. How did you make the partitions ?

You might want to try testdisk to see if you can recover the partition table.

---

### Post by awilki01 on 2008-06-17
Thanks for the help.  I installed testdisk.  It doesn't have the missing hard drive in the available options to choose from.

Any other suggestions?  Why is there not a way to rescan all my hardware like the setup program does to begin with?

---

### Post by bodhi.zazen on 2008-06-17
Try running testdisk after booting from the live CD ...

---

### Post by awilki01 on 2008-06-18
Excuse my ignorance, but the Live CD is just the install CD, correct?  Also, if my partitions were corrupted, wouldn't that affect Windows XP as well?  My Windows XP is on that partition and boots from there.  It has no problems with it.

Perhaps I need a special SATA driver or something?  I will do what you recommend, but I do not feel my partitions are the problem - its the whole SATA hard drive that is not being recognized by Ubuntu.

---

### Post by bodhi.zazen on 2008-06-18
No, the desktop CD will run as a live CD or desktop. You can install testdisk when running the live CD.

Your partitions are *likely* , or they seem to be "OK", but for some reason they are not being read. Testdisk is designed to help, but must be run from a live CD. Make sure you unmount any swap partition first (sudo swapoff /dev/sdxy where /dev/sdxy is your swap partition).

---

### Post by awilki01 on 2008-06-19
Ok, get this....  I just rebooted earlier and noticed that I now see my 400GB hard drive within Ubuntu!!!  I didn't do ANYTHING!!! 

Here are all my outputs.  I'll reboot and re-edit this message to let you know if it recognizes it again.

```

adam@adam-ubuntu:~$ sudo blkid
/dev/sda1: UUID="F89C30389C2FEFB4" TYPE="ntfs" LABEL="Local Disk" 
/dev/sda5: UUID="B6D412BED4128133" LABEL="Z_Drive" TYPE="ntfs" 
/dev/sdb1: UUID="2E8E95880E43FA71" LABEL="Local Disk" TYPE="ntfs" 
/dev/sdb2: UUID="4e9c07bb-c6c5-4ee1-910f-f1bb41273f78" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb3: TYPE="swap" UUID="0733bd47-2ec1-456e-995c-357616648f7a" 

```


```

adam@adam-ubuntu:~$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2008-06-19 12:06 0733bd47-2ec1-456e-995c-357616648f7a -> ../../sdb3
lrwxrwxrwx 1 root root 10 2008-06-19 12:06 2E8E95880E43FA71 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2008-06-19 12:06 4e9c07bb-c6c5-4ee1-910f-f1bb41273f78 -> ../../sdb2
lrwxrwxrwx 1 root root 10 2008-06-19 12:06 B6D412BED4128133 -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-06-19 12:06 F89C30389C2FEFB4 -> ../../sda1

```

```

adam@adam-ubuntu:~$ more /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=4e9c07bb-c6c5-4ee1-910f-f1bb41273f78 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=F89C30389C2FEFB4 /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=B6D412BED4128133 /media/sda5 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda1 :
UUID=2E8E95880E43FA71 /media/sdb1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda3 :
UUID=0733bd47-2ec1-456e-995c-357616648f7a none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

```

```

adam@adam-ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 400.0 GB, 400088457216 bytes
240 heads, 63 sectors/track, 51681 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17752   134205088+   7  HPFS/NTFS
/dev/sda2           17753       51681   256503240    f  W95 Ext'd (LBA)
/dev/sda5           17753       51681   256503208+   7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3a923a91

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9485    76188231    7  HPFS/NTFS
/dev/sdb2            9486       14462    39977752+  83  Linux
/dev/sdb3           14463       14593     1052257+  82  Linux swap / Solaris
adam@adam-ubuntu:~$ 

```

-----------------------------------------------------------------------------------------------

**Edit**:
Figures.  I reboot and my 400GB hard drive is no longer seen.  I do notice in my startup screen it waits forever for "Waiting for root filesystem".  After about 60 seconds it continues and scrolls real quick, but I get a failure on mounting a file system or something - it scrolls too fast to see it exactly.

This is all I see now after this last reboot:

```

adam@adam-ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3a923a91

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9485    76188231    7  HPFS/NTFS
/dev/sda2            9486       14462    39977752+  83  Linux
/dev/sda3           14463       14593     1052257+  82  Linux swap / Solaris

```

---

### Post by bodhi.zazen on 2008-06-19
nice :)

My best guess is a hardware problem, not sure.

IMO test disk is your best option.

---

### Post by awilki01 on 2008-06-20
Ok, I will try it this weekend when I get some more time.  I don't think its hardware because Windows XP never has any issues with my 400 GB hard drive.

---

