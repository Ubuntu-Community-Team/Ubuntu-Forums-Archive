---
title: "using 2 partitions"
date: 2005-09-03
forum: General Help
---

### Post by Eric P. on 2005-09-03
theres how i access XP Partition with Ubuntu 5.04 in other partition?

and i need help with adsl:
[click here for my other thread](http://www.ubuntuforums.org/showthread.php?t=61991)

---

### Post by Wolki on 2005-09-03
for mounting windows partititons, look here:
[https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions](https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions)

---

### Post by Eric P. on 2005-09-03
why dont i have any icons in desktop? not even my computer one or something. :-?

---

### Post by Wolki on 2005-09-03
[QUOTE=Eric P.]why dont i have any icons in desktop? not even my computer one or something. :-?[/QUOTE]

probably because nautilus crashed. Just start it again, using for exaple the run dialog in the gnome menu.

---

### Post by Eric P. on 2005-09-03
i have it booting form hd, not cd and if nautilus (i wonder whats that) crashed, why no error showed up? and when i used ubuntu live cd, i got the cdrom icon on desktop

---

### Post by Irony on 2005-09-03
From my notes:

**Viewing Linux Partitions from Windows**
Download this [http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm#Download](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm#Download) – unzip it and drag into a folder. Click on the executable in the folder and it will run. No messing about with installation.

**Viewing Other Partitions from Ubuntu**
[http://ubuntuguide.org/#automountfat](http://ubuntuguide.org/#automountfat) for mounting a partition. Use the;
sudo fdisk -l
Command for the partition information.
Mounting FAT partitions;
sudo mkdir /media/2nd
sudo mount /dev/hdb1 /media/2nd/ -t vfat -o iocharset=utf8,umask=000
sudo umount /media/2nd/
Mounting NTFS partitions;
sudo mkdir /media/XPb
sudo mount /dev/hda2 /media/XPb/ -t ntfs -o nls=utf8,umask=0222
sudo umount /media/XPb/
Note to remove empty directories;
sudo rmdir /media/XPb
Mounting Other Partitions on Boot-Up
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
This appended to file (note folders must be created first as above);
/dev/hda2       /media/XPb  ntfs    nls=utf8,umask=0222 0       0
/dev/hdb1       /media/2nd  vfat    iocharset=utf8,umask=000   0       0

What these commands mean is that you first make a folder called in my case 2nd and XPb then you mount the partitions for example hda2. To know which partition to mount use the sudo fdisk -l command. Once you've mounted the partition you can if you want unmount it.

You can also mount the partitions on boot up by altering your fstab file.

There are no icons on the desktop in gnome - though you can put them there if you want. You will see a CD icon on the desktop with the LiveCD. Gnome is known for its uncluttered interface.

---

### Post by Eric P. on 2005-09-03
it says i cant sudo because im not a sudoer and when i try to login as root it says i cant login from there... what shall i do????????????????  ](*,)  ](*,)  ](*,)  ](*,)  ](*,)

---

### Post by Eric P. on 2005-09-07
nothing works nothing works nothing works. help me getting a fat32 pratitions be mounted and HELP ME LOGIN AS ROOT i have authorization to access nothing just because the user and root pass are the same? i made a mistake in it. ok, what now? help me or i will need uninstall ubuntu *sniff*

---

