---
title: "Copying Partition"
date: 2007-09-09
forum: General Help
---

### Post by SteveF on 2007-09-09
I have a working Feisty partition.  Prior to upgrading to Gutsy, I want to copy the partition to another partition and have that new partition bootable in case I have problems with Gutsy.  I cleared off the new partition and booted from a CD.  I mounted both partitions and I then ran 
cp -a old_partition/* new_partition

Everything looks like it copied Ok.  I modified the fstab on the new partition to point to the correct drives.  I also modified menu.lst to add the new partition's entry.

When I boot to that partition, the system just hangs.  Sometimes I can ctrl-alt-del and another time I had to do a hard reboot.

Is this not the way to do this?  What should I be doing or did I just miss something that needs to be changed.

Thanks,

Steve

---

### Post by logos34 on 2007-09-10
For a system partition you need to use the **dd** command or **Partimage**:

[http://www.brunolinux.com/02-The_Terminal/The_dd_command.html](http://www.brunolinux.com/02-The_Terminal/The_dd_command.html)
[http://www.partimage.org/Partimage-manual_Usage](http://www.partimage.org/Partimage-manual_Usage)

If you are saving it as an image, Partimage is better in that it copies only the used sectors of a partition.  Be careful with gzip compression, though: in my experience you have use the default 'image split mode' settings:

> ( ) Automatic split (when no space is left)
(X) Into files whose size is:........ **2037 MiB**'
( ) Wait after each volume change

otherwise you get a 'invalid compression level' error when you try to restore the .gz image.

Hope that helps.

---

### Post by SteveF on 2007-09-10
> **logos34 said:**
> For a system partition you need to use the **dd** command or **Partimage**:

[http://www.brunolinux.com/02-The_Terminal/The_dd_command.html](http://www.brunolinux.com/02-The_Terminal/The_dd_command.html)
[http://www.partimage.org/Partimage-manual_Usage](http://www.partimage.org/Partimage-manual_Usage)

If you are saving it as an image, Partimage is better in that it copies only the used sectors of a partition.  Be careful with gzip compression, though: in my experience you have use the default 'image split mode' settings:



otherwise you get a 'invalid compression level' error when you try to restore the .gz image.

Hope that helps.

Thanks.  I tried using dd.  Everything went OK (a lot faster too).  I rebooted to my normal partition.  The UUID of the copied to partition was no longer in /dev/disk/by-uuid.  Thinking the dd caused that and thinking the id was no longer valid, I ran uuidgen and tunefs to assign a new id to the copied to partition.  I modified by fstab and menu.lst.  I rebooted and the new UUID is there.  I mounted the partition and modified the fstab for that partition to load the correct root using uuid.

I restarted and selected the new partition from grub.  It starts to load (I get Ubuntu splash screen) and then it freezes.  The caps lock and scroll lock lights on my keyboard start flashing.  The only way to recover is to power switch the computer off.

So I'm missing something.  The partition information is not stored anywhere else in a file that needs to be updated, is it?

Thanks,

Steve

---

### Post by logos34 on 2007-09-10
Try it without the UUIDs (don't get me started on uuids)...Just take 'em out of fstab and menu.lst.  Use this format:

/dev/hdax / ext3 defaults,errors=remount-ro 0 1

...root=/dev/hdax...

When you image/copy a partition, the uuid goes with it, so the new location/partition ends up with the same uuid as the original (which obviosuly causes problems if one is trying to mount both)...but you changed it so not sure what the issue is.

Feel free to post your edited files, plus fdisk:

sudo fdisk -l

---

### Post by SteveF on 2007-09-10
I tried using the device name instead and when I select from grub, I get the same very initial partial load (splash screen) and then nothing.  The one difference is my keyboard does not freeze so I can ctrl-alt-del to reboot.

Instead of posting entire files, here's relevant lines (let me know if you need to see more in the file).

sudo fdisk -l:
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4865    39078081    7  HPFS/NTFS

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1216     9767488+   c  W95 FAT32 (LBA)
/dev/sdb2            1217       30515   235344217+   f  W95 Ext'd (LBA)
/dev/sdb5            1217       17020   126945598+   7  HPFS/NTFS
/dev/sdb6           17021       18236     9767488+  83  Linux
/dev/sdb7   *       18237       19452     9767488+  83  Linux
/dev/sdb8           30334       30515     1461883+  82  Linux swap / Solaris
/dev/sdb9           19453       30333    87401601   83  Linux

sbd7 is the Feisty partition
sdb6 is the one I copied to

grub entries:
main Feisty entry that works fine:
title		Ubuntu, kernel 2.6.22-10-generic
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.22-10-generic root=UUID=6c922170-f900-4f0f-9b2a-8a8068bffc7e ro quiet splash
initrd		/boot/initrd.img-2.6.22-10-generic
quiet
savedefault

attempted entry using uuid for partition failing:
title		Ubuntu Grumpy, kernel 2.6.22-10-generic
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.22-10-generic root=f418b584-e0c8-42fb-96c6-d887e884ceb5 ro quiet splash
initrd		/boot/initrd.img-2.6.22-10-generic
quiet
savedefault
boot

modified entry using device name - failed:
title		Ubuntu Grumpy, kernel 2.6.22-10-generic
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.22-10-generic root=/dev/hdb6 ro quiet splash
initrd		/boot/initrd.img-2.6.22-10-generic
quiet
savedefault
boot


fstab entries on the failed partition:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb7
#UUID=f418b584-e0c8-42fb-96c6-d887e884ceb5 /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=86A8FC8AA8FC7A4F /windows     ntfs    ro,noauto,exec,auto,nouser,async,gid=1001,umask=0222   0       0
# /dev/sdb1
UUID=AC9D-63E9 /staging vfat rw,exec,auto,nouser,async,gid=1001,uid=1000,umask=0002 0 0
# /dev/sdb5
UUID=844C19FD4C19EB26 /winmedia     ntfs    ro,noauto,exec,auto,nouser,async,gid=1001,umask=0222	0       0
# /dev/sdb6
UUID=6c922170-f900-4f0f-9b2a-8a8068bffc7e     /goofy        ext3    defaults,noauto	0       0
# /dev/sdb9
UUID=dfd853ed-1ad9-4291-b4c0-7aff344ccd66 /data ext3    defaults        0       2
# /dev/sdb8
#UUID=10f86d47-2adc-4ae7-a1ff-3a49631c348a none            swap    sw              0       0
UUID=e28f97d7-031b-46b0-bed9-15e01fe7d946 none            swap    sw              0       0
#/dev/scd0       /media/cdrom0   udf,iso9660 rw,user,noauto     0       0
#/dev/hdc       /media/cdrom0   udf,iso9660 rw,user,noauto     0       0
/dev/cdrom      /media/cdrom0   iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

ignore the comment about sdb7, I never changed it.  I tried the /dev/sdb6 and the commented line above using UUID (for /).  All of the rest are the same as I have for the good partition except for the entry for /goofy (which is not auto-mounted).

Thanks,
Steve

---

### Post by logos34 on 2007-09-10
> **SteveF said:**
> 
ignore the comment about sdb7, I never changed it.  I tried the /dev/sdb6 and the commented line above using UUID (for /).  All of the rest are the same as I have for the good partition except for the entry for /goofy (which is not auto-mounted).

sorry, I don't follow you. 

> # /dev/sdb6
UUID=6c922170-f900-4f0f-9b2a-8a8068bffc7e /goofy ext3 defaults,noauto 0 0

That's the problem right there. Try:

> **/dev/sdb6 / ext3 defaults,errors=remount-ro 0 1**

or 

> #/dev/sdb6
UUID=6c922170-f900-4f0f-9b2a-8a8068bffc7e / ext3 defaults,errors=remount-ro 0 1

Just delete the sdb7 entry.

---

### Post by SteveF on 2007-09-10
That's what I was not explaining well.  I modified the fstab, but did not update the comments.  That's what I get for responding quickly instead of clearly.  So here is the new list with the correct comments:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb6
#UUID=f418b584-e0c8-42fb-96c6-d887e884ceb5 /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=86A8FC8AA8FC7A4F /windows     ntfs    ro,noauto,exec,auto,nouser,async,gid=1001,umask=0222   0       0
# /dev/sdb1
UUID=AC9D-63E9 /staging vfat rw,exec,auto,nouser,async,gid=1001,uid=1000,umask=0002 0 0
# /dev/sdb5
UUID=844C19FD4C19EB26 /winmedia     ntfs    ro,noauto,exec,auto,nouser,async,gid=1001,umask=0222	0       0
# /dev/sdb7
UUID=6c922170-f900-4f0f-9b2a-8a8068bffc7e     /goofy        ext3    defaults,noauto	0       0
# /dev/sdb9
UUID=dfd853ed-1ad9-4291-b4c0-7aff344ccd66 /data ext3    defaults        0       2
# /dev/sdb8
#UUID=10f86d47-2adc-4ae7-a1ff-3a49631c348a none            swap    sw              0       0
UUID=e28f97d7-031b-46b0-bed9-15e01fe7d946 none            swap    sw              0       0
#/dev/scd0       /media/cdrom0   udf,iso9660 rw,user,noauto     0       0
#/dev/hdc       /media/cdrom0   udf,iso9660 rw,user,noauto     0       0
/dev/cdrom      /media/cdrom0   iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by logos34 on 2007-09-10
So, if that's the fstab on sdb6 and you can't get past the ubuntu loading bar screen then I'm not sure what it is.  You really shouldn't even have sdb7 in there (or at least without the uuid), but I see it's got the noautomount option so it shouldn't be factor. 

Have you done a filesystem check on sdb6?
[B]
sudo e2fsck -f -y -v /dev/sdb6[/B]

---

### Post by SteveF on 2007-09-10
The reason sdb7 is in the fstab is so I can work on the drive if I have a problem.  Just easier than writing the full mount statement.

I'm not familar with e2fsck.  Here's the output:

e2fsck 1.40-WIP (14-Nov-2006)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  194034 inodes used (15.88%)
    4155 non-contiguous inodes (2.1%)
         # of inodes with ind/dind/tind blocks: 10291/160/0
 1685994 blocks used (69.05%)
       0 bad blocks
       1 large file

  155824 regular files
   19950 directories
     133 character device files
      26 block device files
       2 fifos
     371 links
   18088 symbolic links (16119 fast symbolic links)
       2 sockets
--------
  194396 files

Does anything look incorrect?

Steve

---

### Post by logos34 on 2007-09-10
It looks fine. (my fragmentation/non-contig. files are 3.2%).  

Wish I knew what the problem was.

---

### Post by SteveF on 2007-09-10
I don't know if this will help at all, but I removed quiet and tried booting using the UUID and the device.

When booting using device name (/dev/sdb6), it took a while to get past the message about mounting the root and then the last thing is does (when switching to console via ALT-F1) is:
[66.462201] Attached scsi generic sg7 type 0

then it just stops.  I ctrl-alt-del to reboot, keyboard is active.

When booting by UUID:
It says mounting root partition and then my keyboard freezes so I can't switch to console and I have to hard boot to recover.

Steve

---

