---
title: "cannot mount flash drive"
date: 2008-06-13
forum: General Help
---

### Post by rbprogrammer on 2008-06-13
ok my problem is i cannot access a flash drive both in ubuntu and windows.  i installed gparted and it says the drive is unallocated.  i know there was files and folders on the drive.  the only thing that i can think of that would do this to a flash drive that was already working was, when my sister was reinstalling windows on her laptop, the flash drive was still in the USB port and she may have "deleted" the partition.  i know the flash drive was not formated b/c i told her to unplug it after i saw what she did.

to try and recover the data, i tried this command:
```

$ sudo mount -t vfat /dev/sdb /media/disk
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
clearly it did not work.  is there any way to recover the data, and then after that i would reformat it.

---

### Post by miss.magenta on 2008-06-13
It is possible that your issue is as simple as specifying the wrong filesystem type in your mount command.  To be sure you're getting the correct fs type, do sudo fdisk /dev/sdb -l.

---

### Post by rbprogrammer on 2008-06-13
:( hmmm this is what i got:
```

$ sudo fdisk /dev/sdb -l
[sudo] password for michael: 

Disk /dev/sdb: 2004 MB, 2004877312 bytes
62 heads, 62 sectors/track, 1018 cylinders
Units = cylinders of 3844 * 512 = 1968128 bytes
Disk identifier: 0x4b8fc128

   Device Boot      Start         End      Blocks   Id  System


```
and thats it, nothing else after that....

---

### Post by miss.magenta on 2008-06-13
Well, this indeed means that the drive was wiped, there is no file system on it anymore unfortunately.  It doesn't even have any partitions defined.  Recovering what was there is probably more difficult and time-consuming than it's worth.  I'd just make a new primary partition and format it.

---

### Post by Zorael on 2008-06-13
You could try to let testdisk restore the partition table; perhaps the partition is still there but the table is empty. Package name **testdisk**, grab it via Synaptic or through a terminal. You need to enable universe repositories in Software Sources.
```
$ sudo aptitude install testdisk
```
The partition table type (it'll ask for it upon start) should be Intel.
```
TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org


Disk /dev/sda - 39 GB / 37 GiB - CHS 4863 255 63

**[ Analyse  ]  Analyse current partition structure and search for lost partitions**
[ Advanced ]  Filesystem Utils
[ Geometry ]  Change disk geometry
[ Options  ]  Modify options
[ MBR Code ]  Write TestDisk MBR code to first sector
[ Delete   ]  Delete all data in the partition table
[ Quit     ]  Return to disk selection






Note: Correct disk geometry is required for a successful recovery. 'Analyse'
process may give some warnings if it thinks the logical geometry is mismatched.
```

---

### Post by rbprogrammer on 2008-06-13
thanks Zorael, so i started using testdisk, and i know the files are on the flash drive because in image 7 i can choose the option to look at the files and they are all there.  but i am weary of trying to create a partition b/c i don't know if it will be reformatted.

i don't know too much about the layout of a filesystem, but is there any way for testdisk to create the partition table and not reformat the drive?  because if all the files are there, i dont know how to access them.

thanks.

---

### Post by Zorael on 2008-06-14
What if you pick the partition type Intel?

---

### Post by rbprogrammer on 2008-06-15
When I do a search under the Intel option, well I attached more screenshots.  In image testdisk03.png, it doesn't matter what option I choose (eg. Y or N) I get the same output (in later screenshots).  Then in the file testdisk04.png, I'm not sure what option I can choose to recover the partition data so that I get get access to my files again.  I would assume the L: option would, but I don't need to fool around with it if I'm not sure what is going to happen.

So I chose the option to Enter, and it lead me to the last image.

---

