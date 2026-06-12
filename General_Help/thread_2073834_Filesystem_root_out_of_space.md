---
title: "Filesystem root out of space"
date: 2012-10-20
forum: General Help
---

### Post by DominikCZE on 2012-10-20
Hi,
sorry if this is the wrong section to post this in.

Today I started getting warning messages about the filesystem root running out of space. Now it says this:


Low disk space
The filesystem root has only 76.9MB disk space remaining.


When I got ubuntu a month ago, I assigned the root partition 4GB, because someone said that it would be enough and I only got ubuntu, because programs made in dev c++ under windows weren't compatible with the automatic marking system we have to hand them into at our school.

The problem is that I started using ubuntu almost as much as windows and installed a whole bunch of crap, such as music player plugins and java. Is there a way I can expand the partition?

Also, Ubuntu and Windows are on a 128GB SSD, windows uses a 700GB HDD for all downloads and such, is there a way I can make ubuntu use that NTFS 700GB partition, instead of throwing everything onto the SSD?

Many thanks. I'm a complete noob when it comes to ubuntu and  partitioning it. :]

---

### Post by drmrgd on 2012-10-20
You can use the partition manager to reallocate the space on the drive.  Of course, the drive needs to be unmounted in order to alter the partition table.  So, you'll want to boot to a live CD / USB and run the partition manager from there.  

The first thing that you'll want to do is to make sure that you've adequately backed up anything you don't want to lose.  Repartitioning a drive is not always perfect, and in the event of a problem where you'll have to reinstall / rebuild your OS, you want to have a failsafe.  

Depending on how you use your system, 4GB is definitely a bit on the lean side.  If you want to add several packages and other utilities, then I would say at least 15GB would be better.  I think some people recommend less.  But, having to reallocate space is a pain and takes a while.  So, if you have the space to give, I would say plan ahead now.  

The process will be a matter of booting to a live CD as I said, shrinking the Windows partition, and reallocating that space to your Ubuntu partition.  Partition manager should handle the moving of files and re-creating the partition table with minimal hassle, although it could take a while to do it, depending on how much data is to be moved.

With regard to mounting /home to a different partition (or drive in this case), it's certainly possible and many do this.  The caveat will be that you'll need to create a linux filesystem partition on the drive that you want to move /home to.  You'll need to do this in the same way as increasing the / partition on your 128GB drive.  Just load it up in Partition manager (unmounted of course....although you can unmount it for editing once in Partition Manager), shrink the Windows Data partition (I'm guessing it's NTFS or FAT), and make a new data partition that is a Linux filesystem type.  Then, you'll need to edit your fstab entry to reflect this change.  Here's some nice instructions for step-by-step how to move your home partition:

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Hope that helps!

---

### Post by ajgreeny on 2012-10-20
4GB is not enough for ubuntu root partition as you have found; 10GB is more normally the minimum these days, and many users make sure it is even bigger than that.

Without knowing the exact layout of your partitions it is difficult to give further advice so can you please post the output of ```
sudo fdisk -l
``` and then mount the ntfs partitions on the machine using nautilus's left hand pane, and show the output of ```
df -hT
```

If you can manage it, it would also be useful to see two screenshots of a gparted window, one for each disk.

---

### Post by DominikCZE on 2012-10-20
Thanks for the help guys.
I was hoping that I could move home without having to partition the HDD, although I already found out that linux permissions are incompatible with NTFS.
Shrinking the SSD further shouldn't be a problem, Windows is already taking up 50GB without the whole user folder, which I find ridiculous, but there are still 60GB available. It's nice too know that repartioning shouldn't be too much of a problem. :)


here is the layout:

Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcfc64b32

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   225490943   112642048    7  HPFS/NTFS/exFAT
/dev/sda3       225492990   250068991    12288001    5  Extended
/dev/sda5       225492992   233304063     3905536   83  Linux
/dev/sda6       233306112   241117183     3905536   83  Linux
/dev/sda7       241119232   250068991     4474880   83  Linux

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x208a5af8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1465145343   732571648    7  HPFS/NTFS/exFAT


hopefully everything is mounted:

Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcfc64b32

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   225490943   112642048    7  HPFS/NTFS/exFAT
/dev/sda3       225492990   250068991    12288001    5  Extended
/dev/sda5       225492992   233304063     3905536   83  Linux
/dev/sda6       233306112   241117183     3905536   83  Linux
/dev/sda7       241119232   250068991     4474880   83  Linux

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x208a5af8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1465145343   732571648    7  HPFS/NTFS/exFAT


I'm currently home for the weekend and my external ODD and usb sticks are in my dorm, so I can't get into gparted. I'll try to find a usb stick around here somewhere...

---

### Post by DominikCZE on 2012-10-20
OK, found a really old usb drive.
I didn't manage to copy screenshots from gparted to my pictures folder using cp, so I took photos.

[ATTACH]225801[/ATTACH]



[ATTACH]225802[/ATTACH]

---

### Post by spjackson on 2012-10-20
You haven't shown output of
```

df -hT

```

I can see 3 Linux partitions of approx 4GB each. Your gparted screenshot shows sda7 as almost full and sda5 and sda6 as both empty. So I guess that sda7 is your root partition. I don't see any swap.

You could shrink sda2 (using the Windows tool to do it), but I don't think you can move/grow an extended partition without destroying the partitions it contains.

You could shrink sdb1 (using the Windows tool to do it), and create a /home partition as sdb2, but this still leaves you with / being too small.

Assuming that you don't want any swap, you could probably delete sda5 and sda6, and increase sda7 so that it fills the extended partition. However, I'm not too sure about this. I think it's OK because I think the partition numbers will be preserved. However, if they aren't preserved, you would need to use "boot repair" to fix grub.

But this all assumes that sda5 and sda6 are not currently used.

---

### Post by DominikCZE on 2012-10-20
Whoops, sorry, I didn't read over my answer, I posted the same thing twice.

Filesystem             Type      Size  Used Avail Use% Mounted on
/dev/sda7              ext4      4.3G  4.0G   88M  98% /
udev                   devtmpfs  3.9G  4.0K  3.9G   1% /dev
tmpfs                  tmpfs     1.6G  912K  1.6G   1% /run
none                   tmpfs     5.0M     0  5.0M   0% /run/lock
none                   tmpfs     3.9G  852K  3.9G   1% /run/shm
/dev/sda5              ext4      3.7G  159M  3.4G   5% /boot
/dev/sda6              ext4      3.7G  348M  3.2G  10% /home
/home/dominik/.Private ecryptfs  3.7G  348M  3.2G  10% /home/dominik
/dev/sdb1              fuseblk   699G   49G  650G   7% /media/Storage
/dev/sda1              fuseblk   100M   25M   76M  25% /media/System Reserved
/dev/sda2              fuseblk   108G   48G   61G  44% /media/D466B75D66B73F54

sda5 and 6 are my home and boot partitions. I couldn't find the swap partition shortcut when installing ubuntu so I just didn't make it. Yeah, I wasn't planning on  really using the system that much :/

---

### Post by DominikCZE on 2012-10-21
Ok, I shrank my windows partition by 18GB, I then moved the unallocated space inside
the extended partition sda3.
 
Now, to be able to resize root, I had to move boot and home to the beginning of the unallocated space.
 
I wonder if this will screw up my system boot, but there seems to be no other way of getting the unallocated space next to root.:(
 
 
 
Current setup:
 
[ATTACH]225847[/ATTACH]

---

### Post by spjackson on 2012-10-21
> **DominikCZE said:**
> Ok, I shrank my windows partition by 18GB, I then moved the unallocated space inside
the extended partition sda3.
 
Now, to be able to resize root, I had to move boot and home to the beginning of the unallocated space.
 
I wonder if this will screw up my system boot, but there seems to be no other way of getting the unallocated space next to root.:(

That all makes sense. So long as you are moving partitions like this, and not doing any reordering, I am pretty confident that your existing grub installation will still boot correctly. For this reason, if creating swap, I'd be inclined to create it after the root partition, not before it. However, there is some advice against swapping on a SSD, so you might be better swapping on the HDD. (See for example [http://ubuntuforums.org/showthread.php?t=1937251]("http://ubuntuforums.org/showthread.php?t=1937251") and other references.)

---

### Post by DominikCZE on 2012-10-21
> **spjackson said:**
> That all makes sense. So long as you are moving partitions like this, and not doing any reordering, I am pretty confident that your existing grub installation will still boot correctly. For this reason, if creating swap, I'd be inclined to create it after the root partition, not before it. However, there is some advice against swapping on a SSD, so you might be better swapping on the HDD. (See for example [http://ubuntuforums.org/showthread.php?t=1937251]("http://ubuntuforums.org/showthread.php?t=1937251") and other references.)

Thanks for the answer. I just booted up ubuntu and everything seems to be fine, except an error popping up in the top bar.

> An error occurred, please run Package manager from the right click menu or apt-get to see what's wrong. The error message was:'Error:BrokenCount>0' This usually means that your installed packages have unmet dependencies.

apt-get shows no errors, just a menu of functions, I can't seem to be able to download updates though.

I'll take your advise on swap, I guess I don't even need it at all with 8GB of RAM.

---

### Post by spjackson on 2012-10-21
> **DominikCZE said:**
> 
apt-get shows no errors, just a menu of functions, I can't seem to be able to download updates though.

I don't think this is anything to do with adjusting the partitions. I suspect that an update failed because the partition was full. I don't know much about repairing the apt system, but there are a lot of threads on the topic, or perhaps someone else can help you with that.

---

### Post by DominikCZE on 2012-10-22
> **spjackson said:**
> I don't think this is anything to do with adjusting the partitions. I suspect that an update failed because the partition was full. I don't know much about repairing the apt system, but there are a lot of threads on the topic, or perhaps someone else can help you with that.

Yap, it was an easy fix. I just followed a simple guide and entered 2 commands into the terminal and the error is gone.

Thanks for walking me through the partitioning process, hopefully I won't run out of space anytime soon now :)

---

### Post by spjackson on 2012-10-22
> **DominikCZE said:**
> Yap, it was an easy fix. I just followed a simple guide and entered 2 commands into the terminal and the error is gone.

Great, I'm glad it's fixed.

> 
Thanks for walking me through the partitioning process, hopefully I won't run out of space anytime soon now
You're welcome.

---

### Post by YannBuntu on 2012-10-23
you can mark yourself "affected" by [https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/610358](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/610358)

---

