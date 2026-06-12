---
title: "[SOLVED] Partition problem, it kind of disappeared"
date: 2007-12-17
forum: General Help
---

### Post by merkin on 2007-12-17
I am running a dual boot laptop with Feisty/XP. I partitioned my hard drive 27gb NTFS, 15gb ext3, 12gb FAT32 for shared files and 1gb for swap. I was in the process of making the FAT32 partition mount when the system starts when one of my coworkers saw me working in linux, asked what I was doing, said he knew how to do it and that I didn't need to read the forums (I'm still rather new to linux). He did a few things, but I couldn't follow them all to undo them. He added a line to fstab that I will paste below. Before, the partition showed up in Places>Computer. I mounted it from there and was able to use it. Now, it has disappeared from there and I can't find it. cdrom0 also appeared and I don't think it was there before. I checked, it's empty.

There isn't too much on the partition, nothing that would be irreplaceable. I could delete the partition and remake it, but I'm afraid of any links to it in other files. Any ideas?

hda4 is the partition in question

I've read possibly related posts and they asked for this information, so....

/etc/fstab :
  GNU nano 2.0.2                          File: fstab                                                            

#  /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=3259087d-7773-4fa0-895e-a4cb1b5c06e3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=B258A6E858A6AB15 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=2b8b729b-3c67-44b1-8b76-2105461e6a01 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
#/dev/hda4      /media/fat      vfat    defaults,rw     0       1



jason@jason-laptop:/etc$ sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3633    29182041    7  HPFS/NTFS
/dev/hda2            5230        7164    15542887+  83  Linux
/dev/hda3            7165        7296     1060290    5  Extended
/dev/hda4            3634        5229    12819870    b  W95 FAT32
/dev/hda5            7166        7296     1052257+  82  Linux swap / Solaris



jason@jason-laptop:/etc$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              15G  4.4G  9.7G  32% /
varrun                252M  104K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb            252M  108K  252M   1% /proc/bus/usb
udev                  252M  108K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   33M  219M  14% /lib/modules/2.6.20-16-generic/volatile

Partition table entries are not in disk order


jason@jason-laptop:/etc$ ls -la /media
total 20
drwxr-xr-x  5 root root 4096 2007-12-17 18:02 .
drwxr-xr-x 23 root root 4096 2007-12-17 16:37 ..
lrwxrwxrwx  1 root root    6 2007-06-24 19:56 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2007-06-24 19:56 cdrom0
lrwxrwxrwx  1 root root   45 2007-06-25 09:58 .directory -> /etc/kubuntu-default-settings/directory-media
drwxr-xr-x  2 root root 4096 2007-12-17 17:03 fat
-rw-r--r--  1 root root    0 2007-12-17 18:02 .hal-mtab
---xr-x---  1 root root    0 2007-03-22 03:27 .hal-mtab-lock
drwxr-xr-x  2 root root 4096 2007-06-24 19:56 hda1
lrwxrwxrwx  1 root root   42 2007-06-25 09:58 .hidden -> /etc/kubuntu-default-settings/hidden-media


Again, I'm rather new to linux, but I'm picking it up quickly. Thoughts would be greatly appreciated.

---

### Post by Dryw Paulic on 2007-12-17
Hi Merkin,

As a troubleshooting step, try mounting the drive manually. In this case you would follow the following steps to do so:

```

sudo mkdir /media/testfatmount

sudo mount -t vfat /dev/hda4 /media/testfatmount 

```After running the mount command successfully you should be able to see all the files on the drive under /media/testfatmount . If that works just fine you could add an entry to your fstab to make it permanent:

```
/dev/hda4   /media/testfatmount   vfat   user,fmask=0111,dmask=0000   0   0
```This will give all users access to the partition, which will be mounted at  /media/testfatmount . One word of caution is to ensure that you do not erase any lines in your fstab file, you should just append the line above to the end of the file.

Cheers,

-Dryw

---

### Post by merkin on 2007-12-17
Hey, thanks for the reply.

It mounted, but it was read only. I have my firefox and thunderbird profiles in there (backed up elsewhere). When I try to open either from linux, it says that they're already running and not responding. It's also still in /media rather than with the other drives like it was.

The profiles are all that are in there right now. Is it worth it even to jump through hoops to undo this all? Should I just delete the folder in /media and the line for it in fstab (he added it), remake the partition, and take the lesson learned not to let strange men do things to my laptop?

---

### Post by merkin on 2007-12-17
So I solved it. Most of it was my dilletante knowledge of linux, but it was a problem with my fstab file. I decided to delete and remake the partition using gparted (probably unnecessary). Using rmdir, I removed all the extra directories the other guy made. I made a new one in / to mount it to and added  the following line to fstab

/dev/hda4 /(folder made) (file system) user,fmask=0111,dmask=0000 0 0

hda4 is the partition on the drive.

I mounted with sudo mount /dev/hda4 /(folder)

this is accessible by everyone on the computer, so be careful.

From what I'm reading now, this seems to be fairly standard fare and I was just searching for the wrong terms.

---

