---
title: "Mounting NTFS and FAT32 on start-up"
date: 2008-05-17
forum: General Help
---

### Post by japtar10101 on 2008-05-17
I want to be able to mount NTFS and FAT32 partitions I have in my laptop automatically at startup.  

I know I have to write some command-line function in the sessions menu, and add it in there, but I don't know the command to mount these partitions.  Google search isn't particularly friendly in this either...

Any suggestion will help.  Thanks in advance!

---

### Post by the8thstar on 2008-05-17
Hello,

before you edit /etc/fstab (which is ultimately where the configuration occurs), have you tried to install the NTFS tool? It is in the repos (ntfs-utils I believe) and you can activate and configure it in the Gnome Menu under Applications > System once it's installed.

I would favor this because it's GUI based and very simple to use.

---

### Post by japtar10101 on 2008-05-18
> **the8thstar said:**
> Hello,

before you edit /etc/fstab (which is ultimately where the configuration occurs), have you tried to install the NTFS tool? It is in the repos (ntfs-utils I believe) and you can activate and configure it in the Gnome Menu under Applications > System once it's installed.

I would favor this because it's GUI based and very simple to use.

I thought the Gutsy Gibbons distribution and up already have a read/write ability in NTFS partitions.  But I'll check that out anyway.

Also, what about the FAT32 partition?  How do I get that mounted first, instead of constantly clicking on the icon before it mounts?  I have a few programming programs that share the same FAT32 partition with my Windows NTFS partition programs.

---

### Post by cdtech on 2008-05-18
> I thought the Gutsy Gibbons distribution and up already have a read/write ability in NTFS partitions. But I'll check that out anyway.

It does, no need to install a third party program anymore.

/etc/fstab:
/dev/hdb1 /mnt/share ntfs-3g defaults,locale=en_US.utf8 0 0

you can replace the ntfs-3g with ntfs or vfat. (I already had the 3g program installed)

Once you edit your fstab file just type on the command line "mount -a". Be sure to create a directory for the mount point.

---

### Post by japtar10101 on 2008-05-20
> **cdtech said:**
> It does, no need to install a third party program anymore.

/etc/fstab:
/dev/hdb1 /mnt/share ntfs-3g defaults,locale=en_US.utf8 0 0

you can replace the ntfs-3g with ntfs or vfat. (I already had the 3g program installed)

Once you edit your fstab file just type on the command line "mount -a". Be sure to create a directory for the mount point.

Sorry, can you clarify a little more?  This is what my fstab looks like:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=636a8aea-9c1f-4a1a-8ecf-9fcf494a014c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=4d8c0905-1413-46ed-87e3-3533b6b359e2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
Apparently, I have a mount for ext3 (Ubuntu), swap, and cdrom, so I take it I need to add in a line for fat32 (mounted as /media/SHARE_, /dev/sda3 in partition) and NTFS (mounted as /media/System, /dev/sda1 in partition)?

Thanks for your directions, though, it's giving me a start!

---

### Post by cdtech on 2008-05-20
First off you need to see what Ubunut see's as your partitions, so do:
sudo fdisk -l

This will give a listing such as:

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000116f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         638     5124703+  83  Linux
/dev/sdb2             639        8750    65159640    5  Extended
/dev/sdb3            8751       30401   173911657+   7  HPFS/NTFS
/dev/sdb5             639        1307     5373711   82  Linux swap / Solaris
/dev/sdb6            1308        6413    41013913+  83  Linux
/dev/sdb7            6414        8750    18771921   83  Linux

Then you could just add a line in the fstab file using the system type:

/dev/sdb3 /mnt/share ntfs defaults,locale=en_US.utf8 0 0

That would mount my ntfs partition.

If you want to use your block ID such as you have listed in your fstab file, you could issue the command:
blkid
which will list the block id's of your devices.

Hope this helps.....

---

### Post by northyj0e on 2008-05-20
when i put
```
/dev/sdc1 /mnt/share vfat defaults,locale=en_US.utf8 0 0
```
on the end of my fstab i get this when i run sudo mount -a 

```
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Also when i try and mount the drive using the GUI i get the message 'You do not have the privaliges to mount this partition'

any ideas?

---

### Post by cdtech on 2008-05-21
Is the file type vfat or ntfs?

Run "sudo fdisk -l" to see the system type, probably an ntfs in place of the vfat.

You do have the right setup though, just the wrong file system...

---

### Post by japtar10101 on 2008-05-23
> **cdtech said:**
> First off you need to see what Ubunut see's as your partitions, so do:
sudo fdisk -l

This will give a listing such as:

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000116f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         638     5124703+  83  Linux
/dev/sdb2             639        8750    65159640    5  Extended
/dev/sdb3            8751       30401   173911657+   7  HPFS/NTFS
/dev/sdb5             639        1307     5373711   82  Linux swap / Solaris
/dev/sdb6            1308        6413    41013913+  83  Linux
/dev/sdb7            6414        8750    18771921   83  Linux

Then you could just add a line in the fstab file using the system type:

/dev/sdb3 /mnt/share ntfs defaults,locale=en_US.utf8 0 0

That would mount my ntfs partition.

If you want to use your block ID such as you have listed in your fstab file, you could issue the command:
blkid
which will list the block id's of your devices.

Hope this helps.....

It worked until I tried to add the fat32 partition.  what am I doing wrong?

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=636a8aea-9c1f-4a1a-8ecf-9fcf494a014c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=4d8c0905-1413-46ed-87e3-3533b6b359e2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#I typed everything under here.
/dev/sda1       /media/System   ntfs    defaults,locale=en_US.utf8 0       0
/dev/sda3       /media/SHARE    fat32   defaults,locale=en_US.utf8 0       0
```

---

### Post by cdtech on 2008-05-23
Use vfat instead....

---

### Post by japtar10101 on 2008-05-25
> **cdtech said:**
> Use vfat instead....

I had to play around with other options besides that, but I finally managed to get it working.  Thanks!

---

### Post by Arles on 2008-05-25
can you help me? I get this info :

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcb94cb94

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6246    50170963+   7  HPFS/NTFS
/dev/sda2            8185        9462    10265535   83  Linux
/dev/sda3            9463        9724     2104515    f  W95 Ext'd (LBA)
/dev/sda4            6247        8184    15566985    c  W95 FAT32 (LBA)
/dev/sda5            9463        9724     2104483+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

Now I want my FAT32 15 Gb partition to mount when I boot, but also the NTFS part. the big one so that I can read (if possible write) files

---

### Post by sisco311 on 2008-05-25
@Arles

Add this lines to the fstab:
> /dev/sda1 /media/**ntfs** ntfs defaults,umask=007,gid=46 0 1
/dev/sda4 /media/**fat32** vfat defaults,umask=007,gid=46 0 1To edit the file run this command from a terminal:
```
gksu gedit /etc/fstab
```Create the mount points:
```
sudo mkdir /media/**ntfs**
sudo mkdir /media/**fat32**
```Mount the partitions:
```
sudo mount -a
```Note: You can change the mount points(/media/ntfs, /media/fat32) to whatever you want.

---

### Post by cdtech on 2008-05-25
> **Arles said:**
> can you help me? I get this info :

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcb94cb94

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6246    50170963+   7  HPFS/NTFS
/dev/sda2            8185        9462    10265535   83  Linux
/dev/sda3            9463        9724     2104515    f  W95 Ext'd (LBA)
/dev/sda4            6247        8184    15566985    c  W95 FAT32 (LBA)
/dev/sda5            9463        9724     2104483+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

Now I want my FAT32 15 Gb partition to mount when I boot, but also the NTFS part. the big one so that I can read (if possible write) files

Just add your partitions to the /etc/fstab file.

/dev/sda1       /media/yourdir   ntfs    defaults,locale=en_US.utf8 0       0
/dev/sda4       /media/yourdir    fat32   defaults,locale=en_US.utf8 0       0

Be sure to create a mount point, such as /mnt/yourdir

Then just type mount -a to mount them without reboot

Hope this helps......

---

### Post by Arles on 2008-05-28
sorry for not replying sooner I had problems with my laptop. Anyway I did as yoiu said anf it works like a charm .Thank you

---

### Post by Arles on 2008-06-04
Could you give me another "copy/paste solution" for this?

```
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xef63ef63

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3384    27181948+   7  HPFS/NTFS
/dev/sda2            5705       10011    34595977+   7  HPFS/NTFS
/dev/sda3            3385        5439    16506787+  83  Linux
/dev/sda4            5440        5704     2128612+   f  W95 Ext'd (LBA)
/dev/sda5            5440        5704     2128581   82  Linux swap / Solaris

```

for mounting NTFS partitions offcourse

---

### Post by japtar10101 on 2008-06-05
Hmm...This is quite problematic.  The option "default" sets up a read-only access to the partition.  While this is fine for Windows NTFS partition, it heavily defeats the purpose of the SHARE Fat32 partition.  With that said and done, what do I have to do to change the options of Fast32 so that I own the FaT32 drive?

I did a little homework, but out of 3 options ("user=omiyat", "owner=omiyat", "umask=000"), only "umask=000" seemed to work (though the root still owns it).  Why is that?  I prefer "owner=omiyat" option over others....

---

### Post by geo909 on 2008-06-05
Maybe you want to take a look in pysdm (PYthon Storage Device Manager).
You can find it in synaptic.

It's a tool with a GUI that actually writes lines in fstab for all your storage devices. You only have to tick boxes, I've found it very useful when I didn't want to mess up with configuration files. It's very easy to use.
You can also learn about fstab: You tick your boxes and then check your fstab file to see what was changed/added.

---

### Post by sisco311 on 2008-06-05
> **japtar10101 said:**
> Hmm...This is quite problematic.  The option "default" sets up a read-only access to the partition.  While this is fine for Windows NTFS partition, it heavily defeats the purpose of the SHARE Fat32 partition.  With that said and done, what do I have to do to change the options of Fast32 so that I own the FaT32 drive?

I did a little homework, but out of 3 options ("user=omiyat", "owner=omiyat", "umask=000"), only "umask=000" seemed to work (though the root still owns it).  Why is that?  I prefer "owner=omiyat" option over others....

You can use the uid(user id) and gid(group id) options to set the owner and group:
uid=1000,gid=1000 (by default 1000 is the id of the first user created on the system)

to get your user id and group id:
```
id
```or
```
id ***username***
```

EDIT: You can use the user name: uid=username,gid=groupname

---

