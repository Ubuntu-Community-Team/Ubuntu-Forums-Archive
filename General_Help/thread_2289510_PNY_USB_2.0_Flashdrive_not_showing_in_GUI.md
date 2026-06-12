---
title: "PNY USB 2.0 Flashdrive not showing in GUI"
date: 2015-08-04
forum: General Help
---

### Post by chris382 on 2015-08-04
I have a PNY USB 2.0 Flash Drive and it will not show up in the GUI (Ubuntu 14.04 LTS btw) so i can't access it at all :( It does show up in GParted as File System:unallocated 7.61 GiB.
Also it shows up as Bus 001 Device 006: ID 154b:007a PNY as the output for lsusb. I've tried df command and it will not show up there.

---

### Post by sudodus on 2015-08-04
I think it means that you have not mounted any partition on the pendrive. Maybe you need to mount them with superuser privileges. Please maximize a terminal window and post the output of

```
sudo lsblk -fm
```

Are there valuable data on the pendrive, or would it be OK to overwrite it completely (format it)?

---

### Post by Vladlenin5000 on 2015-08-04
I think it means [this]("https://www.pny.com/mega-commercial/explore-our-products/encrypted-drives") and probably it works in Windows only, with some proprietary software. Either encrypted or really unpartitioned which is what "unallocated" usually means.

---

### Post by sudodus on 2015-08-05
Good catch Vladlenin :-) Probably encrypted.

@ chris382: Can you test the pendrive in Windows?

If you cannot read it with Windows and there are no valuable data on it, I think you can create a new partition table with gparted.

---

### Post by efflandt on 2015-08-05
It sounds like it either has a file system not recognized by Linux or no file system. What did you last use it for (and as mentioned, see if Windows sees anything on it)?

Back some time ago when using Startup Disk Creator, I used to sometimes mistakenly formatted the whole device (like /dev/sdb) instead of a partition on it (like /dev/sdb1), which would not work for that. So I would use gparted to create another msdos partition table and FAT32 partition and try again.

Worst case if for some reason the previous sentence does not work, you may need to use **sudo dd** to write a bunch of /dev/zero to the drive to clear the beginning of it before creating a new partition table and partition. But dd is dangerous (nicknamed disk destructor) because if you are not VERY careful about referencing the correct device, it can erase the wrong device. So I will not get into that now. For example, I had to use that long ago when I accidentally formatted a floppy for a Mac and could not DOS format it until I zeroed out the beginning of the floppy.

---

### Post by sudodus on 2015-08-05
There is an option in [mkusb to wipe (zeroise) the first megabyte](https://help.ubuntu.com/community/mkusb#Wipe_the_first_megabyte_or_the_whole_device) of a drive. mkusb wraps security around dd.

---

### Post by chris382 on 2015-08-21
```
NAME   FSTYPE LABEL MOUNTPOINT NAME     SIZE OWNER GROUP MODE
sda                            sda    465.8G root  disk  brw-rw----
&#9500;&#9472;sda1 vfat         /boot/efi  &#9500;&#9472;sda1   512M root  disk  brw-rw----
&#9500;&#9472;sda2 ext4         /          &#9500;&#9472;sda2 461.4G root  disk  brw-rw----
&#9492;&#9472;sda3 swap         [SWAP]     &#9492;&#9472;sda3   3.9G root  disk  brw-rw----
sdb                            sdb      7.6G root  disk  brw-rw----
sr0                            sr0     1024M root  cdrom brw-rw----
```

There is no valuable date on the pendrive and it would be fine to format it. I'd just like to use it again and see it in the GUI so i can move files over and so on.

---

### Post by chris382 on 2015-08-21
I have tried to create a new partition table with gparted formating it with ms-dos but it still says unallocated space. This flash drive use to work perfect but after i formatted it on a mac computer it suddenly wasn't showing up in the GUI like it would normally do in ubuntu.

---

### Post by sudodus on 2015-08-21
Now it looks wiped - no partitions :-)

Next: Use ***gparted*** to create a partition table.

***Device -- Create a partition table ...***

And after that create one or more partitions. If you want to use it with Windows too, I suggest that you create a FAT32 file system in the first (or only) partition. Windows reads (at least used to read) only the first partition in USB drives.

---

### Post by sudodus on 2015-08-21
> **chris382 said:**
> I have tried to create a new partition table with gparted formating it with ms-dos but it still says unallocated space. This flash drive use to work perfect but after i formatted it on a mac computer it suddenly wasn't showing up in the GUI like it would normally do in ubuntu.

It looks wiped, but maybe it is borked. In the latter case I suggest that you use ***mkusb*** to wipe the first megabyte according to post #6.

And after that ***gparted*** might work.

---

### Post by chris382 on 2015-08-21
Fixed the issue thanks sudodus.

---

### Post by sudodus on 2015-08-21
You are welcome :-)

---

