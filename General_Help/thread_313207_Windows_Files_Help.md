---
title: "Windows Files Help"
date: 2006-12-05
forum: General Help
---

### Post by notoriouslou1022 on 2006-12-05
Windows crashed and i need to grap some files off windows. I booted up with the uubuntu live cd and i need to know where the windows files at?

Thanks

---

### Post by defishguy on 2006-12-05
I don't want to get flamed for suggesting this, but if you're new to Linux I would suggest that you use knoppix for a file recovery on an ntfs partition.  Knoppix will automagically mount all partitions that it finds.  If it's not reasonable or possible to get and burn another iso then do this in a terminal window.

sudo fdisk -l

You will see something that looks like

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9331    74951226   83  Linux
/dev/sda2            9332        9729     3196935    5  Extended
/dev/sda5            9332        9729     3196903+  82  Linux swap / Solaris

If you have an ide hard drive everything that says sda* will read hda* just change the command below as appropriate.

sudo mkdir /media/windows
sudo mount /dev/sda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222


I do not mean to insult you so if you already know this then please ignore it!  Linux sees everything like it is a file so you won't see anything that looks like a c:\ or D:\

hda or sda is the first hard drive that it sees
hdb or sdb would be the second hard drive

hda1 or sda1 is the first partition on the first hard drive
hda2 or sda2 is the second partition on the first hard drive

hdb1 or sdb2 is the first partition on the second hard drive
hdb2 or sdb2 is the second partition on the second hard drive

You get the picture now :-)

---

### Post by notoriouslou1022 on 2006-12-05
thank you!

---

