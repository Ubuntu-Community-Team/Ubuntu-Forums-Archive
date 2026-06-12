---
title: "Boot Device Not Found"
date: 2020-11-11
forum: General Help
---

### Post by dbee on 2020-11-11
> 
Boot Device Not Found

Pls install an operating system on your harddisk


Ouch.

Formatted. Partitioned and mounted a MicroSD card to a folder in home. After mounting to a specific folder it seemed to wipe all the data in that folder. No big deal. Couldn't find any tutorial online on how to do this procedure with xubuntu or even vanilla ubuntu properly.
 
Gave it a go myself. 

Now when i turn on my system i get the preceding message ie. Boot Device Not Found. Running a system diagnostic doesn't seem to help much. I've tried ejecting the micro sd card and booting again but no luck.

Am I going to have do an xubuntu reinstall then? Does anyone have a link to a proper tutorial on formattting, partitioning and mounting a micro sd card for (x)ubuntu? 

I run alot of docker containers through  wp-env, and I only have 32 GB hd on that system. So i want all my docker containers to run on the microSD.

Any advice on how to keep the docker containers to a minimum ? Besides running a ...

```

docker rm $(docker ps -aq)

```

---

### Post by ajgreeny on 2020-11-11
I do not use nor know docker so can not answer that question, but as a general point about mounting a device, any data in the folder to which you mount that device will become invisible to you and the filesystem.

It should still be there but simply invisible as the mount has replaced it for the time being; unmount the SD card and all the previous data should appear again as if by magic. You seem to suggest that is not happening so I am a bit uncertain what to say to help you more.

Is the card mounted at boot with fstab?
What specific folder in your home is it mounted to?
What data did that folder contain? If it was one of the user hidden folders that are essential for your user to open a session, that could be your problem but we need much more detail to give you further help.

---

### Post by dbee on 2020-11-11
> **ajgreeny said:**
> I do not use nor know docker so can not answer that question, but as a general point about mounting a device, any data in the folder to which you mount that device will become invisible to you and the filesystem.

It should still be there but simply invisible as the mount has replaced it for the time being; unmount the SD card and all the previous data should appear again as if by magic. You seem to suggest that is not happening so I am a bit uncertain what to say to help you more.

Is the card mounted at boot with fstab?
What specific folder in your home is it mounted to?
What data did that folder contain? If it was one of the user hidden folders that are essential for your user to open a session, that could be your problem but we need much more detail to give you further help.

So basically, when i boot up with a live xubuntu cd. I can access the harddrive no problem. 

I thought perhaps it was an /etc/fstab issue. So i commented out the microsd card mount  and did a restart but it didn't make any difference...
> 
xubuntu@xubuntu:/media/xubuntu/76e2b547-702d-4386-a868-9fedbc97bb53/etc$ cat fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/mmcblk0p2 during installation
UUID=76e2b547-702d-4386-a868-9fedbc97bb53 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/mmcblk0p1 during installation
UUID=3EE9-AA13  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
#UUID=0e36cfc3-c8fe-4c2a-b85b-4267fb9b8f7f /mnt/microsd/	  ext4	  discard,noatime,errors=remount-ro	  0	  1


Then i did a *mount -a* and everything seemed fine.

Then i looked at * fdisk -l* and noticed that the 1.6 GB boot drive is empty.

> xubuntu@xubuntu:/media/xubuntu/76e2b547-702d-4386-a868-9fedbc97bb53/etc$ sudo fdisk -l
Disk /dev/loop0: 1.45 GiB, 1545601024 bytes, 3018752 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mmcblk0: 29.12 GiB, 31268536320 bytes, 61071360 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 52C3523D-707F-4F3D-9321-0D620C9526C4

Device           Start      End  Sectors  Size Type
/dev/mmcblk0p1    2048  1050623  1048576  512M EFI System
/dev/mmcblk0p2 1050624 61069311 60018688 28.6G Linux filesystem


Disk /dev/sda: 14.93 GiB, 16005464064 bytes, 31260672 sectors
Disk model: Cruzer Blade    
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x5ee6f53f

Device     Boot   Start      End  Sectors  Size Id Type
/dev/sda1  *          0  3319487  3319488  1.6G  0 Empty
/dev/sda2         13228    21163     7936  3.9M ef EFI (FAT-12/16/32)
/dev/sda3       3321856 31260671 27938816 13.3G 83 Linux


Disk /dev/mmcblk1: 116.9 GiB, 125493575680 bytes, 245104640 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


To answer your questions ajgreeny. 

The micro sd card device was mounted and included in /etc/fstab.

It was mounted to 

[HTML]
/mnt/microsd/
[/HTML]

Then I did a soft link to home I believe (sorry got that bit wrong). Can't remember what the exact command was, but it was a softlink like this ...

> 
ln -s /mnt/microsd 


or might have made a mistake with *ln -s* and done something like this

> 
ln -s /mnt/microsd /home/dara/Desktop/myworkdir


Most of my session and boot info up info is in /home/dara and the boot partition I believe no ? This folder that i mounted to contains some work files and a load of docker containers....

I really don't want to do a reinstall and have to set up the computer again. Also lose all my work files.

---

### Post by HermanAB on 2020-11-11
Just delete the link.  (Deleting a link will not delete what it is pointing to.)

---

### Post by dbee on 2020-11-12
> **HermanAB said:**
> Just delete the link.  (Deleting a link will not delete what it is pointing to.)

Thanks HermanAB.

Thing is though, I can't seem to find the symbolic link anywhere ...

```

xubuntu@xubuntu:/mnt$ sudo find . -type l -ls

```

Gives me nothing. As does ...

```

xubuntu@xubuntu:/media/xubuntu/76e2b547-702d-4386-a868-9fedbc97bb53/home/dara/Desktop/myworkdir$ sudo find . -type l -ls


```

Also i can't find my */mnt/microsd/* anywhere ...

```

xubuntu@xubuntu:/mnt$ stat /mnt/microsd
stat: cannot stat '/mnt/microsd': No such file or directory
xubuntu@xubuntu:/mnt$ ls -a /mnt
.  ..


```

So basically, I can't find the symbolic link. I can't find the */mnt/microsd/* directory and I can traverse my hard drive no problem with a live usb ubuntu. But it reads as *unbootable* by the BIOS. Is the *boot* partition supposed to be empty ? Should i run a Boot Repair iso or maybe see if running GRUB from my xubuntu ISO can sort it out?

Any suggestions welcome...

---

### Post by dbee on 2020-11-12
Solved. It turns out the harddrive was full from all the WordPress wp-env docker containers that were on it.

My system only has 32GB total storage. The wp-env folder was nearly 2GB. After running a boot-repair with no results. I finally copped on and ran a 

> 
df -h


and noticed my harddrive was full. I deleted the contents of */home/dara/wp-env/* and all is good again. My */mnt/microsd* directory is back.

Still not sure exactly what to do about mounting and symbolic linking to my microsd card though?

I appear to have formatted and mounted my microsd. 

Should i just do a ...

> 
mkdir /mnt/microsd/wp-env/
cd /home/dara/wp-env/
ln -s /mnt/microsd


and a...

> 
mkdir /mnt/microsd/myworkdir/
cd /home/dara/Desktop/myworkdir/
ln -s /mnt/microsd/


Also, what's the best way of keeping the docker containers folder size from becoming unwieldy?

I did a 

> 
docker rm $(docker ps -aq)


But that didn't seem to make much difference ... It never deleted the */home/dara/wp-env/* docker containers...

---

### Post by HermanAB on 2020-11-12
If you give a removable storage device a* volume name*, then the system will always mount it the same way.  So, just give it a name and let the system do its thing with it.

---

