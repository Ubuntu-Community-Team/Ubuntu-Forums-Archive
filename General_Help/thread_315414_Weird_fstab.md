---
title: "Weird fstab"
date: 2006-12-09
forum: General Help
---

### Post by mgarcia-val on 2006-12-09
Hi everyone,

I think I've got a kind of weird fstab file. I've two ntfs partitions, a swap partition and a ext3 partition where Ubuntu is installed. Now, my question is this. Typically, as I understand USB drives are 'sda' drives, whatever that means. But here I've got my 4 partitions mounted as sda drives from 1 to 4, whereas my cd-rom as hda. Everything works well, but does this make sense? Should I revert the names? How can I find my USB drive and format it given that it doesn't seem to be a sda drive?

Here's my fstab file: 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=73228207-26c6-42a7-aa63-1113aa68d530 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=7ED82CAAD82C631F /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=10A0504D86190F61 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=dd371b0f-aedd-4434-bcf2-849c50c3d363 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
```
Thanks,
mgarcia-val

---

### Post by bernied on 2006-12-09
It does make sense. My hard disk is also an sda. You can get a list of partitions like this:
```
sudo fdisk -l
```
and compare with your fstab.

The use of those incomprehensible UUIDs for naming partitions seems to be new to Edgy, but seems to work. 

Is something not working?

---

### Post by bernied on 2006-12-09
To find your usb drive, try this.
- unplug drive
- get list of drives/partitions
```
sudo fdisk -l
```
- plug in drive
- get list of drives/partitions again
```
sudo fdisk -l
```

Generally ubuntu will mount the drive for you. Get a list of mounted filesystems like this:
```
mount
```

---

### Post by mgarcia-val on 2006-12-09
All right. I finally found out that my USB drive is sdb1.

Now, I'm trying to format it. Here's the problem I get:

```
Disk /dev/sdb: 512 MB, 512753664 bytes
255 heads, 63 sectors/track, 62 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          62      497983+   b  W95 FAT32
miguel@miguel-desktop:~$ fdisk /dev/sdb1

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): d
No partition is defined yet!

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-61, default 1): 
Using default value 1
Last cylinder or +size or +sizeM or +sizeK (1-61, default 61): 
Using default value 61

Command (m for help): v
16064 unallocated sectors

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 22: Invalid argument.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.
```

Why that error? Isn't a previous step to mkfs -t vfat /dev/sda1? 
I'm sorry for this newbies questions.

---

### Post by PapaNerd on 2006-12-09
You would want to use "fdisk /dev/sdb" (the whole drive), not "fdisk /dev/sdb1" (the first partition on the drive) when initiating the fdisk command.

---

### Post by bernied on 2006-12-09
That error is not necessarily a problem. In my experience usb drives don't behave like others - probably because they're very different (hmmm?). Try unplugging and replugging the device, but beware it may change its name when you do that.

If you are trying to rebuild a usb drive, try using the FAT16 id, then formatting as FAT16. So in fdisk, hit t, then I think 06. This is easier using cfdisk instead of fdisk, if you have it. Then format with:
```
mkfs.vfat -F 16 /dev/sdb1
```

---

### Post by wgscott on 2006-12-09
The UUID changes when you reformat a device.  It makes little sense to have the UUIDs in /etc/fstab if people frequently reformat.  The idea is that if your device name changes, your disks will still mount.  But I can't think of why this would be, unless you like to rearrange your disks and move that little pin thing in the back around, whereas reformatting a disk is quite common.  

This change took me by surprise, and in my case at least it was quite glitchy and I had to revert to the old fstab (which, fortunately, it saves as /etc/fstab-pre-edgy or something similar).

So in short some Ubuntu developer pulled a Microsoft on me, wasting about 4 hours of my life.

---

### Post by mgarcia-val on 2006-12-09
Thanks very much, it worked out with cfdisk, which I found more intuitive to use than fdisk. For some reason, doing what Bernied suggested, that is, choosing the t command in fdisk, and then w, I get the same error message. 

But it has worked out with cfdisk, as I say. Thanks very much to everyone.

---

