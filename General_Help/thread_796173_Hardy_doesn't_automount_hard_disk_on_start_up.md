---
title: "Hardy doesn't automount hard disk on start up"
date: 2008-05-16
forum: General Help
---

### Post by SuperBo on 2008-05-16
Hardy doesn't mount my hard disk on stratup. So I have to go to place and choose disk to mount every startup. How can I  set it to auto.:lolflag::lolflag:

---

### Post by ibutho on 2008-05-16
Hi. You need to give us a bit more info e.g. the filesystem of the partition and the name of the partition e.g. /dev/sda1.

---

### Post by anaconda on 2008-05-16
Hardy doesnt mount fixed disks automatically unless they are mentioned in /etc/fstab -file

Removable diska are supposed to be mounted automatically. So if you mean that your USB-hard disk doesnt mount automagically then that is a different problem..

Which do you have?

Also  the output of this command would help us to help you
```
sudo fdisk -l
```

Type that in terminal and copy/paste the output here..  And you can also tell which is the problem partition if you can

---

### Post by heatblazer on 2008-05-16
Long time ago, I have used a prgram nammed "mountpy" just type:
sudo moutpy
and it automatically mounts all moutable devices :)
(but it`s better to fix the problem so give info)

---

### Post by hyperair on 2008-05-16
You need to get your /etc/fstab configured properly. There's a GUI for that, found in the package "pysdm". Install that, then access it through System->Administration->Storage Device Management.

---

### Post by Joeb454 on 2008-05-16
We do need a little more info.

If it is an NTFS partition (such as a Windows drive) then you may find the link at the bottom of my sig will work for you :)

---

### Post by BlueSkyNIS on 2008-05-16
You may want to check:

[Ubuntu doesn't auto mount my ntfs partition]("http://ubuntuforums.org/showthread.php?t=795719")
[Automount XP in 8.04]("http://ubuntuforums.org/showthread.php?t=766688&highlight=automount+partitions")


Cheers ;)

---

### Post by SuperBo on 2008-05-16
> $ sudo fdisk -l

Disk /dev/sda: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x07410741

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1953    15687441    7  HPFS/NTFS
/dev/sda2            1954        2892     7542517+   f  W95 Ext'd (LBA)
/dev/sda3            2893        3738     6795495   83  Linux
/dev/sda5            1954        2851     7213153+   b  W95 FAT32
/dev/sda6            2852        2892      329301   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?       48437      119493   570754815+  5b  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?       10501      131013   968014120   65  Novell Netware 386
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      116395      236907   968014096   79  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?      179626      179629       27749+   d  Unknown
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

In Kubuntu, we can set it simply.
[http://ubuntusite.com/auto-mount-ntfs-drive-kubuntu-hardy-heron/](http://ubuntusite.com/auto-mount-ntfs-drive-kubuntu-hardy-heron/)

---

### Post by RaverWild on 2008-10-27
Same problem here - fresh Ubuntu installation this sunday with the latest alternate cd. I must click "Places", then each one of my fat32 partitions there and they get mounted. Here is my console output:

~$ sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5ea4f703

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         637     5116671   12  Compaq diagnostics
/dev/hda2   *         638        3935    26491185    c  W95 FAT32 (LBA)
/dev/hda3            3936        5913    15888285    c  W95 FAT32 (LBA)
/dev/hda4            5914        7296    11108947+   5  Extended
/dev/hda5            5914        6044     1052226   82  Linux swap / Solaris
/dev/hda6            6045        6306     2104483+  83  Linux
/dev/hda7            6307        7296     7952143+  83  Linux

---

### Post by alienprdkt on 2008-10-27
#sudo apt-get install pmount
#sudo apt-get install ntfs-3g
reboot

If auto-mount failed you can try to mount your external drive manually with this command:

sudo pmount-hal /dev/sda1
Please replace /dev/sda1 with your external hard drive. You can find out about it by running

sudo fdisk -l | grep NTFS

If the ntfs drive is not mounted automatically open /etc/modules file & add 'fuse' in a new line. This will load the fuse module.

eg:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse

---

### Post by BobMarleyy on 2009-05-11
> **hyperair said:**
> You need to get your /etc/fstab configured properly. There's a GUI for that, found in the package "pysdm". Install that, then access it through System->Administration->Storage Device Management.

Works great!
This program is easy to use and fixes automount problems

---

### Post by sdibaja on 2010-06-07
I guess I made an error and get a mount error on startup, then when I try to unmount I get this>

Error unmounting: umount exited with exit code 1: helper failed with:
[mntent]: line 17 in /etc/fstab is bad
umount: only root can unmount /dev/sdb2 from /media/data+storage

sudo fdisk -l gives me this output>


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1c4e7630

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14503   116490606    7  HPFS/NTFS
/dev/sda2           14503       16431    15484928    7  HPFS/NTFS
/dev/sda3           16431       22267    46874625    5  Extended
/dev/sda4           22267       60802   309532672    7  HPFS/NTFS
/dev/sda5           16431       16796     2928640   82  Linux swap / Solaris
/dev/sda6           16796       18011     9764864   83  Linux
/dev/sda7           18011       22267    34179072   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa2bf227e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29914   240283160    7  HPFS/NTFS
/dev/sdb2           29915       60802   248101024    7  HPFS/NTFS

Disk /dev/mmcblk0: 507 MB, 507379712 bytes
16 heads, 63 sectors/track, 983 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1         983      495313+   6  FAT16

now how do I fix this?

PS: running dual boot windows7 and 10.04 Lucid (both 64bit) and two 500g physical drives
Disk /dev/mmcblk0 is a flash card

---

### Post by Breambutt on 2010-06-07
I like your way of recycling 2 years old threads. Especially since it's a Hardy thread and you're using Lucid.

So how exactly did it come to this? Whatever this is... so you have Windows and Ubuntu on one HDD and you're having difficulties mounting another HDD with NTFS file system? Did you manually edit /etc/fstab or what? Could you paste your fstab file here too, might help more.

At least it looks like you used umount instead of sudo umount.

---

### Post by sdibaja on 2010-06-07
Breambutt:
patience my friend, I am gust a silly old man trying to make things simple :-)
yes, I should have noted the thread was old and not directed to Lucid.  my bad.

I wanted to try "automount" because I keep most data on my NTFS partitions.
I installed "pysdm" and then used System->Administration->Storage Device Management
I got confused and I believe I pointed to the main partition as well as a directory in that same partition.
I did not make any manual changes
after continuing with effing around I get a file mount error during the boot sequence and if I select Skip it runs but both of the partitions on my second data drive are mounted (not a bad thing) and when I try to unmount either I get the unmount error I posted above.

how do I get the fstab file for you inspection?

At this point I would like to just quit using any "automount" features and just get a clean boot back.
thanks!

---

### Post by hyperair on 2010-06-07
You attach it to this thread. It's a text file, found in /etc/fstab. Then we can take a look and see what's wrong. It seems there's some syntax error in line 17, for example.

---

### Post by sdibaja on 2010-06-07
Thanks!


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc                proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda6 during installation
UUID=a299e06a-7367-4abc-b384-22b016c7bc85  /                    ext4  errors=remount-ro    0  1  
# /home was on /dev/sda7 during installation
UUID=b317345c-33cc-46ac-98fa-953e81d32c01  /home                ext4  defaults             0  2  
# swap was on /dev/sda5 during installation
UUID=51c31cf5-4ee9-45fa-a091-6e981f6d718e  none                 swap  sw                   0  0  
/dev/sda2                                  /media/data+storage  ntfs  defaults             0  0  
/dev/sda4                                  /media/Seagate 500 data+storage.bak  ntfs  defaults                    0  0  
/dev/sdb1                                  /media               ntfs  defaults             0  0  
/dev/sda4                                  /media/sda4          ntfs  defaults             0  0

---

### Post by hyperair on 2010-06-08
"/dev/sda4 /media/Seagate 500 data+storage.bak ntfs defaults 0 0 " is the faulty line, as each field has to be separated by spaces. In order to escape spaces in the fstab, replace them with \040, e.g.
"/dev/sda4 /media/Seagate\040500\040data+storage.bak ntfs defaults 0 0 "

---

### Post by sdibaja on 2010-06-12
Thanks!

I understand the syntax error but the fstab is read-only and am unable to modify it.
I copied it and made the changes in Windows but have found the read-only status prevents me from overwriting the existing fstab

do I need to boot from a live CD to make the change?

am I missing some other way to make the change?

Thanks, Peter

PS: this is my edited file >

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda6 during installation
UUID=a299e06a-7367-4abc-b384-22b016c7bc85 / ext4 errors=remount-ro 0 1
# /home was on /dev/sda7 during installation
UUID=b317345c-33cc-46ac-98fa-953e81d32c01 /home ext4 defaults 0 2
# swap was on /dev/sda5 during installation
UUID=51c31cf5-4ee9-45fa-a091-6e981f6d718e none swap sw 0 0
/dev/sda2 /media/data+storage ntfs defaults 0 0
/dev/sda4 /media/Seagate\040500\040data+storage.bak ntfs defaults 0 0 
/dev/sdb1 /media ntfs defaults 0 0
/dev/sda4 /media/sda4 ntfs defaults 0 0

---

### Post by hyperair on 2010-06-12
It shouldn't be read-only. It's just that the file is owned by the user "root", and can only be written by "root" for security purposes. In order to edit the file, you will need to run your text editor as the root user using something like: "gksudo gedit /etc/fstab" and keying in your password when it asks for it.

---

### Post by sdibaja on 2010-06-13
OK, thanks
I get different error on boot, says it can't mount Seagate 500 data+storage.bak


now my fstab contains this:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc                                      proc  nodev,noexec,nosuid               0  0  
# / was on /dev/sda6 during installation
UUID=a299e06a-7367-4abc-b384-22b016c7bc85  /                                          ext4  errors=remount-ro                 0  1  
# /home was on /dev/sda7 during installation
UUID=b317345c-33cc-46ac-98fa-953e81d32c01  /home                                      ext4  defaults                          0  2  
# swap was on /dev/sda5 during installation
UUID=51c31cf5-4ee9-45fa-a091-6e981f6d718e  none                                       swap  sw                                0  0  
/dev/sda2                                  /media/data+storage                        ntfs  defaults                          0  0  
/dev/sda4                                  /media/Seagate\040500\040data+storage.bak  ntfs  defaults                          0  0  
/dev/sdb1                                  /media                                     ntfs  defaults                          0  0  
/dev/sda4                                  /media/sda4                                ntfs  nls=iso8859-1,ro,users,umask=000  0  0  
/dev/sdb2                                  /media/sdb2                                ntfs  defaults                          0  0  



Automount seems to be more trouble that it is worth!

---

### Post by sdibaja on 2010-06-13
thanks for all the help

I did not understand the Storage Device Manager controls, I simply unchecked the "The file system is mounted at boot time" box using the "assistant" button for all drives.

No more Automount but it boots clean every time.

Thanks again, Peter

---

### Post by hyperair on 2010-06-13
There's a nice and graphical way of doing things using "pysdm" (find it in Synaptic, install it, and then run it via System->Administration->Storage Device Manager). I'd recommend you use that instead of editing your fstab file in future cases.

Anyway, what's the error you get when you try "sudo mount /media/sda4" in a terminal? (If it asks you to check dmesg, please post the last 10 lines or so of the output of "dmesg" here please.

---

### Post by sdibaja on 2010-06-13
thanks, all is fixed and working well.
I was using  System->Administration->Storage Device Manager and finally figured out what the various options do...
I no longer get ANY ERRORS!

thanks again for your continued support, I will resist the urge to make system changes in the evening when I am apparently "sundowning" or "under the influence"  :p

---

### Post by hyperair on 2010-06-13
That's great to hear! :-)

---

