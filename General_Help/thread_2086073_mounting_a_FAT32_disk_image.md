---
title: "mounting a FAT32 disk image?"
date: 2012-11-19
forum: General Help
---

### Post by gandalf3 on 2012-11-19
i created a disk image of an SD card which  i moved a file off, but seemingly got corrupted during the move..

looking at the disk in a hex editor indicated the files still existed, replaced the first characters in the deleted files names (to "undelete" them), and saved as a disk image. however, windows seemingly can't mount a file as a drive, for browsing and reading of the files in it..

how do i go about mounting this on ubuntu?

running 12.04.

---

### Post by searchfgold6789 on 2012-11-19
You could do it with the terminal, if you're into that...
```
sudo mount -t iso9660 /location/of/iso /mount/point
```
Or you could follow the instructions here to do it graphically or some other way: [https://help.ubuntu.com/community/MountIso](https://help.ubuntu.com/community/MountIso)

I thought there was an option to mount when you right clicked on it? I dunno, I use KDE. But good luck.
Sincerely,
 - R.R. G.

---

### Post by gandalf3 on 2012-11-19
```
sudo mount -t iso9660 /media/New\ Volume/Q3HD_SD\ (E) /home/user/Zoom
bash: syntax error near unexpected token `('
```
not sure what it could be.. 

i'll try one of the graphical methods..

---

### Post by searchfgold6789 on 2012-11-19
It looks like the location of the .iso that you specified is not actually an .iso file. It looks like it's probably a folder or another type of file. Try clicking and dragging the .iso file directly into the terminal.

---

### Post by efflandt on 2012-11-20
Is the image just a "partition" on the SD, or the entire SD?  You can **sudo mount** an image of a CD/DVD or partition or filesystem in a file, using **-o loop** option, but I do not know if that works for an image of an entire drive.  In a terminal see [COLOR=DarkRed]**man mount**[/COLOR] then type [COLOR=DarkRed]**/loop** [/COLOR]and keep hitting [COLOR=DarkRed]**n**[/COLOR] until you get to [COLOR=DarkRed]**THE LOOP DEVICE**[/COLOR].

But unless you reformatted an SD card or dd'd a CD image to it, the default filesystem type would usually be **-t vfat**, not **-t iso9660**.

The most common place to mount something in Ubuntu is to sudo mkdir a mount point in /media (or you could create the mount point in /mnt).  I added /media/vdisk as a mount point for manually loop mounted image files.

Example of loop mounting the persistent data file (casper-rw) of bootable live/install iso on USB stick:

```
efflandt@XPS8100-1204:~$ **ls /media**
SONY8GB  vdisk

efflandt@XPS8100-1204:~$ **ls -a /media/vdisk**
.  ..

efflandt@XPS8100-1204:~$ **ls /media/SONY8GB**
autorun.inf  casper     dists  install      md5sum.txt  pool     README.diskdefines  wubi.exe
boot         casper-rw  efi    ldlinux.sys  pics        preseed  syslinux

efflandt@XPS8100-1204:~$ **sudo mount -t ext3 /media/SONY8GB/casper-rw /media/vdisk -o loop**

efflandt@XPS8100-1204:~$ **ls /media/vdisk**
boot  cdrom  etc  home  lib  lost+found  media  mnt  rofs  target  tmp  usr  var

```I was not sure how to mount an **entire boot drive image** (a slim lxde Debian ARM image to boot a Raspberry Pi from SD, containing /boot and / partitions).  But I set up a similar Debian system with lxde in VirtualBox and used VirtualBox to add the Raspian image as another hard drive.  Then I used /etc/fstab in the VBox Debian to mount the /boot and / partitions of the image to see what was on them.

---

### Post by gandalf3 on 2012-11-27
thanks.. haven't tried anything yet, but it should work now.. (that make sense about the  -vfat, instead of the iso thing..)

Thanks again :)

---

