---
title: "[SOLVED] Can't access RAID partition in Hardy"
date: 2008-05-18
forum: General Help
---

### Post by Porpoise on 2008-05-18
OK, I give up! Having spent endless hours going round in circles following all the howtos for dmraid, I still can't access the data on my existing Raid striped volume.

Pretty much all the howtos I've managed to find seem to assume you want a raid partition to boot. I use a RAID striped volume for video capture and rendering which was previously set up from windows - and still working fine there - but I want to be able to use it from Ubuntu too.

The weird thing is, it appears in dmraid:
```
root@SUPER-ROCK:/home/steve# dmraid -s -s
*** Active Set
name   : nvidia_eahdeeab
size   : 1250284800
stride : 128
type   : stripe
status : ok
subsets: 0
devs   : 2
spares : 0

root@SUPER-ROCK:/home/steve# dmraid -r
/dev/sdd: nvidia, "nvidia_eahdeeab", stripe, ok, 625142446 sectors, data@ 0
/dev/sdc: nvidia, "nvidia_eahdeeab", stripe, ok, 625142446 sectors, data@ 0

root@SUPER-ROCK:/home/steve# dmraid -ay
RAID set "nvidia_eahdeeab" already active
RAID set "nvidia_eahdeeab1" already active

```

but try as i will, I just don't seem to be able to get the system to allow me to actually read/write anything on the volume.

I'd really like to get this working so I can start doing some editing in Ubuntu (and compare the ease of use of what's available in Ubuntu/Linux compared to Windows) possibly bringing me closer to actually being able to dump windows - although I still have to get TV/PVR working as well!

Any help greatly appreciated!

---

### Post by mahuyar on 2008-05-18
Can you post the results of
```
 sudo fdisk -l 
```

---

### Post by Porpoise on 2008-05-18
> **mahuyar said:**
> Can you post the results of
```
 sudo fdisk -l 
```


Here it is:
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe05ae05a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6375    51207156    7  HPFS/NTFS
/dev/sda2   *        6376        9444    24651742+  83  Linux
/dev/sda3            9445       11356    15358140   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7e909b40

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12749   102400000    7  HPFS/NTFS
/dev/sdb2           12750       21867    73240335   83  Linux
/dev/sdb3           21868       21989      979965   82  Linux swap / Solaris
/dev/sdb4           21990       30401    67569390   83  Linux

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6e8e191f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       77827   625139712    7  HPFS/NTFS

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/sde: 400.0 GB, 400086360064 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa086c7fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       25497   204804621    7  HPFS/NTFS
/dev/sde2           25498       48641   185904180    7  HPFS/NTFS

Disk /dev/sdj: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00019064

   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sdj2            7650       24792   137701147+   7  HPFS/NTFS

Disk /dev/sdk: 2013 MB, 2013265920 bytes
129 heads, 32 sectors/track, 952 cylinders
Units = cylinders of 4128 * 512 = 2113536 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdk1   *           1         953     1966064    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(960, 128, 32) logical=(952, 71, 32)

Disk /dev/dm-0: 640.1 GB, 640145817600 bytes
255 heads, 63 sectors/track, 77826 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6e8e191f

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1               1       77827   625139712    7  HPFS/NTFS

Disk /dev/dm-1: 640.1 GB, 640143065088 bytes
255 heads, 63 sectors/track, 77826 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-1p1   ?         410      119791   958924038+  70  DiskSecure Multi-Boot
Partition 1 does not end on cylinder boundary.
/dev/dm-1p2   ?      121585      234786   909287957+  43  Unknown
Partition 2 does not end on cylinder boundary.
/dev/dm-1p3   ?       14052       14052           5   72  Unknown
Partition 3 does not end on cylinder boundary.
/dev/dm-1p4          164483      164486       25945    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```Sorry there are so many discs in the list! :(

That last entry looks like the system has picked up some partition data from a different discs!?!

---

### Post by mahuyar on 2008-05-18
Sorry.  I forgot to mention a few more things:

Can you also post the output of:
```
 ls -l /dev/mapper/ 
```

And also,
```
 sudo fdisk /dev/mapper/nvidia_eahdeeab 
```

Press 'p' and [ENTER] to print the table (Post this output also).  Then, press 'q' and [ENTER] to quit.

---

### Post by Porpoise on 2008-05-18
> **mahuyar said:**
> Sorry.  I forgot to mention a few more things:

Can you also post the output of:
```
 ls -l /dev/mapper/ 
```

Here goes:
```

crw-rw---- 1 root root  10, 63 2008-05-18 16:02 control
brw-rw---- 1 root disk 254,  0 2008-05-18 16:02 nvidia_eahdeeab
brw-rw---- 1 root disk 254,  1 2008-05-18 16:02 nvidia_eahdeeab1

```

And also,
```
 sudo fdisk /dev/mapper/nvidia_eahdeeab 
```Press 'p' and [ENTER] to print the table (Post this output also).  Then, press 'q' and [ENTER] to quit.

and here:
```

The number of cylinders for this disk is set to 77826.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/mapper/nvidia_eahdeeab: 640.1 GB, 640145817600 bytes
255 heads, 63 sectors/track, 77826 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6e8e191f

                      Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_eahdeeab1               1       77827   625139712    7  HPFS/NTFS

```

Thanks for your help on this :KS

---

### Post by mahuyar on 2008-05-18
I guess everything's there.  It's just needed to be mounted properly.  If it's not done so properly, try (assuming you're using GNOME desktop):
```
 sudo gnome-mount --device /dev/mapper/nvidia_eahdeeab1 
```

See if that brings up a drive icon on your desktop or in your "Computer" under the menu, Places.

Could you also post the output of the command ```
 mount 
```

---

### Post by Porpoise on 2008-05-18
> **mahuyar said:**
> I guess everything's there.  It's just needed to be mounted properly.  If it's not done so properly, try (assuming you're using GNOME desktop):
```
 sudo gnome-mount --device /dev/mapper/nvidia_eahdeeab1 
```

Hmm... seems to be a slight issue here - it doesn't complete:
```

root@SUPER-ROCK:/home/steve# sudo gnome-mount --device /dev/mapper/nvidia_eahdeeab1
sudo: unable to resolve host SUPER-ROCK

```
> See if that brings up a drive icon on your desktop or in your "Computer" under the menu, Places.

Could you also post the output of the command ```
 mount 
```

Here's the output of mount
```

/dev/sdb2 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
/dev/sdb4 on /home type ext3 (rw,relatime,errors=remount-ro)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/steve/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=steve)
/dev/sde2 on /media/BACKUP_freecom_network type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdj2 on /media/LaCie VIDEO type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sde1 on /media/DATA_freecom_network type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdj1 on /media/LaCie BACKUP type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdk1 on /media/STEVE_FLASH type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sda2 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda1 on /media/Win2K_SP4 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdb1 on /media/Vista Ultimate type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

```

---

### Post by mahuyar on 2008-05-18
Not sure what the error means, but let's try mounting it directly to a folder.  Since you're already *root*, I'll omit the 'sudo' in front of the commands :D

```
 mkdir /home/steve/Desktop/raid-partition 
```
```
 mount /dev/mapper/nvidia_eahdeeab1 /home/steve/Desktop/raid-partition/ 
```

Does it work?

---

### Post by Porpoise on 2008-05-18
> **mahuyar said:**
> Not sure what the error means, but let's try mounting it directly to a folder.  Since you're already *root*, I'll omit the 'sudo' in front of the commands :D

```
 mkdir /home/steve/Desktop/raid-partition 
``````
 mount /dev/mapper/nvidia_eahdeeab1 /home/steve/Desktop/raid-partition/ 
```Does it work?


You're my man!  That did it!:guitar::KS

Will it now remember that each time the system boots? Or is there something else I need to do to ensure that happens?

---

### Post by mahuyar on 2008-05-18
Awesome.  I have a solution ready for you.  :D Was just trying it out.  Now, this is not very sophisticated as current Ubuntu does it now -- I think they're using udev to auto mount partitions, and I'm still learning about it.

But, this will just do what you want:

1) Make a backup copy of your /etc/fstab file.
2) ```
 gksu gedit /etc/fstab 
```
3) Append the following line at the end of the file (copy and paste):
/dev/mapper/nvidia_eahdeeab1     /home/steve/Desktop/raid-partition     auto     nosuid,nodev,noatime,uid=1000,gid=1000     0   0

NOTE:
Inside the terminal:
Type 'exit' to go back to regular 'steve'.
Find out if your userid is 1000: ```
 id -u 
```
If it shows otherwise, change the uid=####.  The same goes for groupid also.  ```
 id -g 
``` would give you your group ID.

You can change the folder's place as well.  Just make sure it's created ahead of time.

4) Save and quit Gedit
5) Reboot and see if works!  :KS

---

### Post by Porpoise on 2008-05-18
> **mahuyar said:**
> Awesome.  I have a solution ready for you.  :D Was just trying it out.  Now, this is not very sophisticated as current Ubuntu does it now -- I think they're using udev to auto mount partitions, and I'm still learning about it.

But, this will just do what you want:

1) Make a backup copy of your /etc/fstab file.
2) ```
 gksu gedit /etc/fstab 
```3) Append the following line at the end of the file (copy and paste):
/dev/mapper/nvidia_eahdeeab1     /home/steve/Desktop/raid-partition     auto     nosuid,nodev,noatime,uid=1000,gid=1000     0   0

NOTE:
Inside the terminal:
Type 'exit' to go back to regular 'steve'.
Find out if your userid is 1000: ```
 id -u 
```If it shows otherwise, change the uid=####.  The same goes for groupid also.  ```
 id -g 
``` would give you your group ID.

You can change the folder's place as well.  Just make sure it's created ahead of time.

4) Save and quit Gedit
5) Reboot and see if works!  :KS

OMG! IT WORKED! IT WORKED!  If you're ever in my neck of the woods, I definitely owe you at least several beers!:KS\\:D/

Where do you get to learn this stuff?

---

### Post by mahuyar on 2008-05-18
> **Porpoise said:**
> OMG! IT WORKED! IT WORKED!  If you're ever in my neck of the woods, I definitely owe you at least several beers!:KS\\:D/

Where do you get to learn this stuff?

From this [wiki]("https://help.ubuntu.com/community/FakeRaidHowto").  It used to be a pain when Ubuntu didn't let you install it on a RAID partition.  :mad:

Glad that it worked out.  Now, you gotta tell everyone that your video editing experience has become much more productive in Linux than using Windows...  :lolflag:

---

### Post by Porpoise on 2008-05-18
> **mahuyar said:**
> From this [wiki]("https://help.ubuntu.com/community/FakeRaidHowto").  It used to be a pain when Ubuntu didn't let you install it on a RAID partition.  :mad:

Glad that it worked out.  Now, you gotta tell everyone that your video editing experience has become much more productive in Linux than using Windows...  :lolflag:

:lolflag:   That's my next phase - along with getting mythTV working correctly!

Thanks again.

---

### Post by Porpoise on 2008-06-26
> **Porpoise said:**
> 
 	Quote:
 	 	 		 			 				 					Originally Posted by **mahuyar** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=4990174#post4990174") 				
 				[I]From this [wiki]("https://help.ubuntu.com/community/FakeRaidHowto").  It used to be a pain when Ubuntu didn't let you install it on a RAID partition.  :mad:

Glad that it worked out. Now, you gotta tell everyone that your video editing experience has become much more productive in Linux than using Windows... :lolflag:[/I]
 			 		 	 	 
:lolflag:   That's my next phase - along with getting mythTV working correctly!


Thanks again.

Given up on Myth for the time being (don't have the time to mess about with it) and am using TV-Viewer instead. A nice simple interface to allow you to watch TV - it just works! Probably because it is not massive overkill like myth. If all you want to be able to do is watch TV and change channels, this is the one to go for IMHO.

As far as Video Editing being more productive in Linux than windows, well, I'd say it has a long way to go yet. In windows, I can do the whole job in one programme. In Linux, it seems I have to use several seperate programmes to get from capturing the clips, to burning the final DVD. Some of the methods are very clunky too. It wouldn't be quite so bad if you could at least do the whole lot from within Cinelerra (it's the best so far I think) and it would be streets better if you didn't have to revert to the command line at any stage - especially when trying to build up menus

---

