---
title: "no automatic disk-mount"
date: 2008-06-23
forum: General Help
---

### Post by dexter.deepak on 2008-06-23
i just installed ubuntu hardy where the disks are not mounted by default.
i would like to have them mounted .....BUT not being shown on the desktop.
can someone help ..

---

### Post by danwood76 on 2008-06-23
Could you provide us with a little more info please?

Like what sort of disks are you trying to automount? (internal/external)

---

### Post by drs305 on 2008-06-23
Please post the results of:
```

cat /etc/fstab
sudo fdisk -l

```
and tell us which partitions you want mounted.

To hide the display of mounted partitions on your desktop, run the following command. To display them, change 'false' to 'true':
```

gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible 'false'

```

---

### Post by lennartack on 2008-06-23
I think you need some command line tweaking for that. So, open a terminal to start.

//EDIT: drs305's fdisk -l works great for this so you can use that command.
To find out what your drives are named like, type:
```
ls /dev | grep sd
```
And:
```
ls /dev/ | grep hd
```
The drives are named like sdxy or hdxy, where x is the hard drive(a,b,c,d) and y the partition number(1,2,3).

To see which drives are already mounted, type:
```
cat /etc/mtab
```
You can use "| grep sd", or "hd" here too to see only the things you need. In the beginning of every line you see the device name (/dev/hdxy) and next to is the mountpoint.

Now, make the directories where you want your drives mounted.
```
sudo mkdir /media/MOUNTPOINT
```
You can also make a folder in you home directory if you want.

Mount the drives manually to see if they work:
```
sudo mount /dev/DEVICENAME /media/MOUNTPOINT
```

When you have mounted all drives, type the /etc/mtab command again to determine which filesystem type your partitions have:
```
cat /etc/mtab | grep sd
```or hd.
First word on every line is device name, second mountpoint and third filesystem type.

Edit your /etc/fstab file to let them automatically be mounted at boot:
```
sudo gedit /etc/fstab
```
Then add at the end a line for every partition you want to be mounted at boot:
```
/dev/DEVICENAME     /media/MOUNTPOINT     FILESYSTEMTYPE    defaults     0     0
```

There certainly are other ways and gui tools, but I don't know any of them :P

---

### Post by vanadium on 2008-06-23
External USB disks should not be included in /etc/fstab. If an external disk does not mount automatically, there is a good reason. A frequent cause of ntfs disks that do not automatically mount is that these disks were not properly disconnected from MS Windows. Anyway, let us await some additional info from the original poster.

---

### Post by lennartack on 2008-06-23
> **vanadium said:**
> External USB disks should not be included in /etc/fstab. If an external disk does not mount automatically, there is a good reason. A frequent cause of ntfs disks that do not automatically mount is that these disks were not properly disconnected from MS Windows. Anyway, let us await some additional info from the original poster.
But I thought disks never automatically mount in ubuntu... I always do it the way I posted above, because if you let ubuntu mount the disks, sometimes it mounts it as /media/disk and the other time /media/disk1.

---

### Post by dexter.deepak on 2008-06-23
sorry i am late..
i just migrated from gutsy to hardy (and have even used feisty), where all my internal as well as external harddisk partitions were mounted on startup, and whenever i used an external usb drive, it also amounted automatically on /media/disk,disk1 and so on.
here in hardy, i have to right click all the partitions and mount them on startup (except my reiserfs parttion which is automatically mounted on /future, which i created duriing installation).
since i CAN mount the ntfs partition , this means i had a CLEAN windows shutdown.
the o/ps of are :

```
dpak@dpak-server:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe3c9e3c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   c  W95 FAT32 (LBA)
/dev/sda2            2551       19457   135805477+   f  W95 Ext'd (LBA)
/dev/sda5            5101        8924    30716248+   b  W95 FAT32
/dev/sda6            8925       14023    40957686    7  HPFS/NTFS
/dev/sda7            2551        2672      979902   82  Linux swap / Solaris
/dev/sda8            2673        5100    19502878+  83  Linux
/dev/sda9           14024       16455    19535008+  83  Linux
/dev/sda10          16456       19457    24113533+  83  Linux

```

```
dpak@dpak-server:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda10
UUID=9b12e7ad-8970-40f5-a3cc-14dd5066f2ca /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=728747e3-564a-4207-9e6a-1cee4f3ad926 /future         reiserfs relatime        0       2
# /dev/sda7
UUID=a845a7d0-2a83-4816-9dad-398b686e97c8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```


```
dpak@dpak-server:~$ cat /etc/mtab
/dev/sda10 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-16-generic/volatile tmpfs rw 0 0
/dev/sda9 /future reiserfs rw,relatime 0 0
securityfs /sys/kernel/security securityfs rw 0 0
gvfs-fuse-daemon /home/dpak/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=dpak 0 0

```

---

### Post by kriemer on 2008-06-23
If it is inappropriate to post my problem in someone else's thread please let me know. 

I have the same issue.  

4 external drives (NTFS and EXT3) that auto mount.  
3 internal drives that do not.

I would like the internal drives to automount.

```
kriemer@kriemer-linux:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=7feb49fc-bb14-49aa-9eb4-14d92be2a6a0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=301117d7-76bd-4010-8329-5309020f7fee none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
kriemer@kriemer-linux:~$ sudo fdisk -l
[sudo] password for kriemer: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb43eb43e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19313   155131641    7  HPFS/NTFS
/dev/sda2           19314       38913   157437000    5  Extended
/dev/sda5           19314       38112   151002936   83  Linux
/dev/sda6           38113       38913     6434001   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc04bc04b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc04bc04c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
1 heads, 63 sectors/track, 4961616 cylinders
Units = cylinders of 63 * 512 = 32256 bytes
Disk identifier: 0x00002f9a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           2     4961536   156288352+  83  Linux

Disk /dev/sde: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1fb09e49

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdf: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb022b022

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdg: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb0aae095

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1       60801   488384001    7  HPFS/NTFS
kriemer@kriemer-linux:~$ 

```

Many thanks in advance.

k

---

### Post by vanadium on 2008-06-23
@dexter.deepak: I was under the assumption that you were referring to external drives: you did not specify in your original post.

Since Hardy, it is normal for an internal ntfs partition not to automount by default. The partition is only mounted "on demand" using the new gvfs system.

If you want these partitions to be permanently available under ubuntu, you are free to mount them the "traditional" way yourself, i.e. by including them in /etc/fstab. The way to do this was described by lennartack in this thread.

---

### Post by dexter.deepak on 2008-06-24
i am yet confused over what to do...:confused:
actually i cant understand how to fill the entries in /etc/fstab...what is this UUID ?? can i continue without knowing ALL the options in that file ..like UUID,options,dump,pass ...or someone can explain these terms to me ..

heres my /etc/mtab after mounting all my drives..rest of the details are there in my previous posts ..
```
dpak@dpak-server:~$ sudo cat /etc/mtab
[sudo] password for dpak: 
/dev/sda10 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-16-generic/volatile tmpfs rw 0 0
/dev/sda9 /future reiserfs rw,relatime 0 0
securityfs /sys/kernel/security securityfs rw 0 0
gvfs-fuse-daemon /home/dpak/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=dpak 0 0
/dev/sda1 /media/disk vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0
/dev/sda5 /media/MISC vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0
/dev/sda6 /media/New\040Volume fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
/dev/sda8 /media/disk-1 ext3 rw,nosuid,nodev,uhelper=hal 0 0

```

---

### Post by danwood76 on 2008-06-24
UUID is like a volume serial number, its useful when your block device IDs change regularly which happens with some motherboards.

The options are the mount options, you can specify filesystem dependant options and also mount options in this section.

Dump, something to do with archiving, not really sure always set it to 0.

Pass if the order in which fsck checks the disk on bootup.

So for example above to mount your ntfs volume you would enter the following line at the end of your fstab:
```

/dev/sda6 /media/NTFS ntfs-3g defaults 0 0

```
This will mount your ntfs volume with default options to /media/NTFS, you will also need to create the mountpoint else it wont mount.

---

### Post by dexter.deepak on 2008-06-24
you mean to say that it is optional to use UUID , i can simply use the device name ?

---

### Post by danwood76 on 2008-06-24
Yes UUID is completely optional, if you want to use UUID's you can get them with the blkid command.
Like so:
```

sudo blkid

```
That will dump all the UUIDs of the drives plugged in.

---

### Post by dexter.deepak on 2008-06-24
well this method worked..but partially.
heres my new /etc/fstab:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda10
UUID=9b12e7ad-8970-40f5-a3cc-14dd5066f2ca /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=728747e3-564a-4207-9e6a-1cee4f3ad926 /future         reiserfs relatime        0       2
# /dev/sda7
UUID=a845a7d0-2a83-4816-9dad-398b686e97c8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#dev/sda1
UUID=0C46-5052	/media/sda1	vfat	defaults	0	0
#/dev/sda5
UUID=7823-A63C	/media/sda5	vfat	defaults	0	0
#/dev/sda6
UUID=84E88DE0E88DD13A	/media/sda6	ntfs-3g		defaults	0	0
#/dev/sda8
UUID=bd419a62-180e-472a-9c1e-3297e5102729	/media/gutsy	ext3	defaults	0	0
```

i can only mount the /dev/sda8 on /media/gutsy...may be because this is ext3.
but other ones are not mounted...and i cant even mount them manually...it says "permission denied".

---

### Post by danwood76 on 2008-06-24
Remove the UUID's and use the block device ID.
Save the fstab and to make it mount all the volumes in the fstab use the following command:
```

sudo mount -a

```

---

### Post by PeterBBB on 2008-06-24
> **vanadium said:**
> @dexter.deepak: 

...
Since Hardy, it is normal for an internal ntfs partition not to automount by default. The partition is only mounted "on demand" using the new gvfs system.
...



They can be setup to automount with the "NTFS Configuration Tool". Mount on demand is rather a pain for disks used on every session.


PB

---

### Post by dexter.deepak on 2008-06-24
thanks.. finally it worked !!
even using the uuid also works..just i have to "sudo mount" once .

---

### Post by dexter.deepak on 2008-06-26
problems continue...
the mounted disks are not given the write option this way ...so i cant save any web pages to my other partitions !
i want to give my partitions appropriate permissions..it would be better if someone can point me to a link to read more about /etc/fstab and its configuration.
thank you

---

### Post by dexter.deepak on 2008-06-27
help !!:(

---

### Post by drs305 on 2008-06-27
> **dexter.deepak said:**
> i want to give my partitions appropriate permissions..it would be better if someone can point me to a link to read more about /etc/fstab and its configuration.
thank you

Here are two good links:
[Understanding fstab]("http://ubuntuforums.org/showthread.php?&t=283131")
[mount ( 8 ) - Linux man pag]("http://linux.die.net/man/8/mount")

If these are NTFS drives, did you try the ntfs-config tool mentioned earlier?
```

sudo aptitude install ntfs-config

```

To run:
```

sudo ntfs-config

```

---

### Post by dexter.deepak on 2008-06-27
thanks for the links :)
in the meantime i read some manuals, but it didnt help..
the strange thing here is that i am able to write on only ntfs (and my ext3 /), and not on my 2 fat32 drives and even not on my other ext3 drive...
i cant even write on the the reiserfs drive i created during installation with a mountpoint of /future. (you can see my /etc/fstab in previous posts)

when i see the mount options by right-clicking the drives, i see a 'rw' option on all drives...so i am confused:confused:

---

### Post by danwood76 on 2008-06-27
If you open up nautilus as root are you able to write to the drives then?

To open nautilus as root run this in terminal:
```

sudo nautilus

```

---

### Post by dexter.deepak on 2008-06-27
as root , yes i can write to the drives.

---

### Post by drs305 on 2008-06-27
For the vfat files, in fstab try:
```
#dev/sda1
UUID=0C46-5052	/media/sda1	vfat iocharset=utf8,uid=1000,umask=000 0 0
#/dev/sda5
UUID=7823-A63C	/media/sda5	vfat iocharset=utf8,uid=1000,umask=000 0 0
```

---

### Post by dexter.deepak on 2008-06-28
thanks ..this helped, but i have some doubts and more problems.
1. why are you using uid in /media/sda5 and not in /media/sda1
2. what is the  option utf-8 meant for ? before trying your code, i had the iocharset of /media/sda5 to be something like iso9660 (i dont remember exactly).
3. i did the same for the /media/gutsy drive which is ext3, but it even fails to mount now.
4. i still have no permissions on /future.

---

### Post by danwood76 on 2008-06-28
Can you post your /etc/fstab file again, it will be nice to see where you are now at.

---

### Post by drs305 on 2008-06-28
> **dexter.deepak said:**
> thanks ..this helped, but i have some doubts and more problems.
1. why are you using uid in /media/sda5 and not in /media/sda1

Simply cut and paste buffoonery on my part - I forgot to copy it twice. They should both be the same and I'll edit the previous entry.
> 
2. what is the  option utf-8 meant for ? before trying your code, i had the iocharset of /media/sda5 to be something like iso9660 (i dont remember exactly).
utf-8 has become the standard and should not effect things but I will do some checking to be sure.

> 
3. i did the same for the /media/gutsy drive which is ext3, but it even fails to mount now.

You don't want to do that. The /media/gutsy file is in ext3 format. Change it back to the way it was. "/media/gutsy  ext3	defaults  0 0 "

> 4. i still have no permissions on /future.
We'll have to work on that one, I've never used reiserfs  ;-)

---

