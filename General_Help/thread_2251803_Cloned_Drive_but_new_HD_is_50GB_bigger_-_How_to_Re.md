---
title: "Cloned Drive but new HD is 50GB bigger - How to Recover Xtra Space"
date: 2014-11-06
forum: General Help
---

### Post by Rick St. George on 2014-11-06
Went from a 250 GB to a 320GB HD. But by cloning, there is 70 GB unallocated now.

How can I expand the partition to include the extra space without losing data?

Thanks!
Rick

---

### Post by TheFu on 2014-11-06
Probably, but it depends on the file system used and whether encryption and/or LVM are part of the current setup. If a "different" file system is used, then is may not be possible or may use different commands.

**resize2fs** is the simple answer for ext3/ext4 on normal partitions (no LVM or encryption).

Regardless - whenever modifying partition tables, before starting, having a 100% know-you-can-restore backup is just smart.

---

### Post by Rick St. George on 2014-11-07
Thanks but what is resize2fs? Is that a terminal command using sudo?

Perhaps I can just format it, and use it as a Logical drive. But don't know how to do that in Ubuntu. Any ideas? I believe it is Ext4, not encrypted, as it is an Ubuntu install.

And Yes, the drive I cloned from is not wiped yet. 

Thanks
Rick

---

### Post by Mark Phelps on 2014-11-07
If the partition you want to resize is in use, you will have to boot from CD/DVD/or USB to do the partition resizing -- there is no way around that.

The Ubuntu install media already contains GParted -- which you can use to resize partitions, and that is a GUI app, not a command line app.

---

### Post by tgalati4 on 2014-11-07
*gparted* has worked for me.  When it loads, you will get an error message (something to the effect) "Partition size does not match physical size of this disk.  Would you like to fix?"

Select "Yes" and be happy.  Otherwise, say no, examine the partitions, and if you have no conditions as TheFu suggests, then you can simply drag the last (rightmost) partition to occupy the entire disk.  Shut down and reboot and check that your files are still intact.  It's generally a safe procedure.

Back up your important files!

---

### Post by oldfred on 2014-11-07
You should just be able to use gparted from live installer or a gparted liveCD to either resize or create partitions. You cannot use gparted in your install as you cannot edit mounted partitions. Even with live installer you usually have to swap-off or unmount swap to be able to fully edit partitions.

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by TheFu on 2014-11-07
Actually, it is possible to resize (larger) a running system.  I've done it a few times .. think they were ext4, but I don't recall for sure. Lots of caveats, of course. It may have been under LVM too - I just don't remember. Always have to google for this when I need it.

From the resize2fs manpage:
>        The resize2fs program will resize ext2, ext3, or ext4 file systems.  It can be used to enlarge
       or shrink an unmounted file system located on device.  If the filesystem is mounted, it can be
       used to expand the size of the mounted filesystem, assuming the kernel supports on-line resiz&#8208;
       ing.  (As of this writing, the Linux  2.6  kernel  supports  on-line  resize  for  filesystems
       mounted using ext3 and ext4.).


Booting off a liveCD does make it easier, since every partition changing need CAN be performed that way.

---

### Post by Rick St. George on 2014-11-07
Just a thought ... Can I simply format the unallocated partition from inside Ubuntu? 
If so, How?  Else I will get my SystemRescue CD and perform the function from there.
Its just that I am working and would hate to wait till this evening to do it.

Thanks,
Rick

---

### Post by oldfred on 2014-11-07
If not bumping against the 4 primary limit you should just be able to create a new partition and format it. If ext4 then you will need to set ownership & permissions and modify fstab to permanently mount it.

If you already have 4 primary partitions, is the un-allocated next to the extended partition? If so expand extended first to include unallocated and create new logical partition.

---

### Post by Rick St. George on 2014-11-07
Don't know,  here is what fdisk -l shows;

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xddde85fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   486303743   243150848   83  Linux
/dev/sda2       486303744   625142447    69419352    5  Extended
/dev/sda5       486305792   488396799     1045504   82  Linux swap / Solaris

************************************************

It does not show the unallocated partition, after CLONING with Acronis. The Cloning simple made these partitions to be exactly like was on the "old" drive.
Looks like I will have to use some other method to see the whole disk, find the unallocated portion, and format it .... so that Ubuntu will see it and be able to use it.

Right?

---

### Post by oldfred on 2014-11-07
Is not the sectors from 488..  after swap but inside extended to 62.. the end of the drive, not unallocated space? So you can just create a logical partition inside the extended. You will have to swap off and use live installer.

---

### Post by Rick St. George on 2014-11-07
Did just that with Gparted, but can't write to it - "Permission Denied".
Confused !!! Perhaps I should try to expand the extended partition, Aahhh

Notice the Swap file is as big as the Extended partition.  Could this be part of the problem? Note above, sda2 and sda5.

This is how it looks now, after formatting the rest of the drive as ext4.

Device Boot         Start           End            Blocks      Id  System
/dev/sda1   *        2048       486303743   243150848   83  Linux
/dev/sda2       486303744   625142447    69419352      5  Extended
/dev/sda5       486305792   488396799      1045504    82  Linux swap / Solaris
/dev/sda6       488398848   625141759    68371456    83  Linux

***********************************************************
Notice also sda6 is included with swap in sda2 (because extd?)

Maybe I should delete sda5 and sda6, expand sda2 to end of drive, leaving a small space for Swap.
Sound logical?
How much space should be allowed for Swap?

Thanks for all help and patience.
Rick

---

### Post by oldfred on 2014-11-07
You can delete the new partition and move swap all the way to the end of the extended. The shrink extended from left, so unallocated is outside extended. The you can expand sda1.

But I tend to prefer having smaller system partitions (20 or 25GB) and larger data partitions or separate /home.  You have permission denied as you have not given yourself permission to use the partition. We often suggest when installing using the separate /home as then you automatically have it mounted with you as the owner and with permissions to use it.
Data partition is just a bit more advance. You can give yourself ownership and then set permissions. You also have to create a mount point for it. Some use /mnt/data, others like /media/data or even /media/$USER/data which is typical auto mount but it will auto mount with size, UUID or if you label partition then as that label. I do suggest labelling all partitions.

       chmod -R a+rwX,go-w /path/to/folder
sudo chmod -R a+rwX,o-w /folder
All directories will be 775.
All files will be 664 except those that were set as executable to begin with.
Seems like a better way as you have more control over what is executable. Isee post #8 & 10 by morbius1.
[http://ubuntuforums.org/showthread.php?t=1795369](http://ubuntuforums.org/showthread.php?t=1795369)

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Then if you want it remounted every time you reboot, add the entry to fstab.
Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)

[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

---

### Post by gordintoronto on 2014-11-08
You could use Gparted to create a partition and format it. Launch it with the command: gksudo gparted

Then you could edit fstab so the partition is automatically mounted at logon.

Another approach would be to boot from the installation media, run Gparted, delete the swap and extended partitions, expand sda1 to all but 4 GB of the hard drive, then create a new swap partition.

Please be sure you have good backup before you modify partitions!

---

### Post by Rick St. George on 2014-11-08
Thanks everyone for your valuable input and precious time. With all the talk of needing a backup and the destructive pursuit of resizing a partition, I decided that the best course for me was to;

1. Install Ubuntu on the newer (actually older but biggger) drive thereby utilizing the entire drive.
2. Remove that drive, and re-insert older drive and copy all folders under home/name (incl. .mozilla and .thunderbird) to a backup via USB.
3. Re-insert the newer drive, and copy all folders from old drive.

This enabled me to avoid the Encrypted Home directory as I could not copy from one drive to another. I had to boot with the old drive and copy them off to a BU drive.
Case solved and case closed.

Thanks to all in the forum in helping me to grow and love linux again with Ubuntu (using ubuntu studio).

Rick

---

