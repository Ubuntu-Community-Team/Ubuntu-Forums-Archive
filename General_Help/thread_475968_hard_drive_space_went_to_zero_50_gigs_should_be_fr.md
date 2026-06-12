---
title: "hard drive space went to zero?? 50 gigs should be free."
date: 2007-06-16
forum: General Help
---

### Post by sdowney717 on 2007-06-16
Somehow I had the os crash on me. I came to the computer and the harddrive was madly working, the screen was not responding, so I turned it off. 

Then when I turned it back on, I had lost almost all my free space on the ubuntu partition.
I have a 200 gig drive

From windows disk management it shows.

Disk 0 NTFS 116.90 GB for windows

Disk 0 unknown healthy (EXT3 linux ubunutu partition) 70 GB 

428 mb swap partition.

Now when I goto ubuntu places computer and view the file system it shows 393mb free
It can not be true. 

What can I do to expose the space and find why it saya I only have 393mb free space?

---

### Post by sdowney717 on 2007-06-16
here is a snapshot saying it only has 393mb free. 

It really thinks this because I tried to download an iso image and I ran out of space.
Could there be some massive amount of files written to the partition somewhere?

---

### Post by langi280179 on 2007-06-16
I appreciated the program filelight to reveal, where disk space has gone.
I would look in /tmp and /var/cache/apt/archives for freeing diskspace.

---

### Post by OzzyFrank on 2007-06-16
I won't give you an answer like clean out your temp folder or get rid of downloaded packages, as that isn't going to help, and certainly doesn't address what has happened here. I have no idea what happened to all those free gigs, but quite possible there could be this huge 40Gb temporary file that never got deleted when you shut down during hard disk activity. And on that note I REALLY REALLY must stress:

NEVER - EVER- turn off a computer during hard drive activity... ESPECIALLY when you note that the disk is madly working away... no matter how much alcohol you've had! Seriously, you can lose MUCH more than your free space (try a drive that doesn't work any more full stop). You have to remember that it doesn't matter if the screen goes black, if the hard drive is visibly and audibly working away, it means the PC is hard at work, and the LAST thing it needs is to be turned off right then.

So go look for a huge file on your hard drive you might be able to delete, and thank your lucky stars you not only have an Ubuntu system to boot into, but a hard drive that hasn't been forced to crash beyond repair.

---

### Post by sdowney717 on 2007-06-19
ok,

But how do i look for a large file.
What program should I run?

I have a free space problem on this partition.
I know now because I just did a full partition backup and restore using Norton Ghost ver 9.
I booted win XP, backed up my ubuntu partition. Deleted the ubuntu partition using XP.
Restored the ubuntu partition telling Norton Ghost to expand the partition to use all the space.
And none of that helped at all.

My history with this set of ubuntu files is I had Ubuntu running on a 12gb secondary drive.
I backed it up using ghost.
I restored the ubuntu partition to a gparted created partition of the main 200gb windows drive.
And for some reason, it seems to have remembered the original size.
EVEN THOUGH, when I first did this a couple of months ago, I seem to remember it saying 50gb free space.

The crash I noted seemed to redirect it to the old ubuntu secondary drive. I had to reinstall grub to boot the root on the primary drive. And I yanked out the old 12gb drive to make sure it could not use it ever again.

I deleted some stuff and got it to 1.1gb free.

But I have looked thru the file system and I cant find where the space has gone. When I manually add up the space in the folders (right click properties gives size), I get about 9gb.
The entire partition is 70gb.
And I am stuck. 
Any one know what to do?

---

### Post by sdowney717 on 2007-06-19
Here is what is in tmp folder.

---

### Post by Crafty Kisses on 2007-06-19
> **sdowney717 said:**
> Somehow I had the os crash on me. I came to the computer and the harddrive was madly working, the screen was not responding, so I turned it off. 

Then when I turned it back on, I had lost almost all my free space on the ubuntu partition.
I have a 200 gig drive

From windows disk management it shows.

Disk 0 NTFS 116.90 GB for windows

Disk 0 unknown healthy (EXT3 linux ubunutu partition) 70 GB 

428 mb swap partition.

Now when I goto ubuntu places computer and view the file system it shows 393mb free
It can not be true. 

What can I do to expose the space and find why it saya I only have 393mb free space?

You might want to check out your logs, there are sometimes massive log files that take up so much space.

---

### Post by sdowney717 on 2007-06-19
I installed kdirstat and none of the folders look to be too big
kdirstat is a nice program

so where is the space, do I need to delete ubuntu and reinstall from scratch??
Why is the partition not being used to capacity.
What can I run to make it use ALL of the partition.

---

### Post by Mr. C. on 2007-06-19
The partition map on a disk will show the size of the disk block allocated to the file system.  I does not manage the file system itself.

Your file system is an ext3 file system. You need to run fsck on the root file system.  It is possible that the free block list is corrupted.

Run 

```
shutdown -F
```

and let the system check the disk up on reboot.

MrC

---

### Post by sdowney717 on 2007-06-20
[http://www.howforge.com/how-force-fsck-ubuntu](http://www.howforge.com/how-force-fsck-ubuntu)

thanks, 
yet even following these instruction It would not force a file system check at boot.
What I did was run fsck twice in a terminal window.
It eventually told me to reboot and it did a file system check at boot. Claimed to find a few errors.

However the free space issue is still showing only 1gb free.

would booting the gparted live cd and trying to adjust the partition be worth persuing?
Or is this going to eventually require a total reinstall with a wiped partiton back to unallocated space.

---

### Post by wonk-o-matic on 2007-06-20
What do 
   sfdisk -d /dev/hda
and 
   fdisk -l /dev/hda 
(that's a lowercase "L" option)
show?

---

### Post by Mr. C. on 2007-06-20
Don't thrash or try random cures that are likely to cause more severe problems.  I've already state that the partition map *has nothing to do with the file system's notion of its free space*.  Ignore the partition map.

The space is either in use, or the file system corrupted. Ext2 is reliable.

Run and show the output of the following:

```
df -h
du -s /*
```

We'll go from there.
MrC

---

### Post by OzzyFrank on 2007-06-20
OK, I'm pretty sure the space isn't being taken up by one large file, and the problem cannot be fixed with fsck, as good as that is for fixing things like a messed up journal. Contraty to the last post, I think this problem comes down to the partition table being a bit whacky from being created from the drive image. When first learning about disk images I saw a lot of mention of images being the same size as the total amount of the drive, and drives only ending up with the amount the image contained... basically down to limitations or default settings in programs, improper use of commands, etc. When I used DD a while back a 6Gb image to a 6.6Gb partition straight away reduced that partition by 600Mb; I tried a few things but I think it was eventually me rebuilding the partition table for that partition (or for the drive?). I did that from within Windows using Partition Table Doctor. You can make a backup of the table first, in case rebuilding it makes it worse or does nothing. I've used that program a few times now, and half the time it fixed things, and when it didn't I could restore the original partition table and continue on the quest for the answer. I'd try this, as with the backup feature it makes it safe. The program is freeware too, so try it. This might not be the answer, but it might (was for me).

---

### Post by sdowney717 on 2007-06-23
/mnt is a mounted windows xp partition

root@scott-desktop:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             9.0G  7.5G  1.1G  88% /
varrun                252M  232K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb            252M   96K  252M   1% /proc/bus/usb
udev                  252M   96K  252M   1% /dev
devshm                252M   16K  252M   1% /dev/shm
lrm                   252M   33M  219M  14% /lib/modules/2.6.20-16-generic/volatile
/dev/sda1             117G   67G   51G  58% /mnt/windows

root@scott-desktop:~# du -s /*
4640    /bin
36384   /boot
0       /cdrom
7176    /charts
128     /dev
11792   /etc
20684   /home
4       /initrd
0       /initrd.img
0       /initrd.img.old
629196  /lib
52      /lost+found
20      /media
69661653        /mnt
77516   /opt
0       /proc
2862320 /root
5944    /sbin
4       /srv
0       /sys
8       /test
128     /tmp
3600464 /usr
448480  /var
0       /vmlinuz
0       /vmlinuz.old
root@scott-desktop:~#

---

### Post by sdowney717 on 2007-06-23
root@scott-desktop:~# sfdisk -d /dev/sda
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=245151837, Id= 7, bootable
/dev/sda2 : start=245155680, size=   876960, Id=82
/dev/sda3 : start=246032640, size=144683280, Id=83
/dev/sda4 : start=        0, size=        0, Id= 0
root@scott-desktop:~# fdisk -l /dev/sda 

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15260   122575918+   7  HPFS/NTFS
/dev/sda2           15261       15315      438480   82  Linux swap / Solaris
Partition 2 does not end on cylinder boundary.
/dev/sda3           15315       24321    72341640   83  Linux
Partition 3 does not end on cylinder boundary.
root@scott-desktop:~#

---

### Post by sdowney717 on 2007-06-23
[http://ubuntuforums.org/showthread.php?t=407292&highlight=move+ubuntu+to+larger+partition](http://ubuntuforums.org/showthread.php?t=407292&highlight=move+ubuntu+to+larger+partition)

This poster appears to have done something similar to me. Moved ubuntu to a larger drive and it still remembers the original partition size.

---

### Post by kelvin spratt on 2007-06-23
Try booting into windows and do a disc check then bottom right hand corner look for safely remove software and remove reboot windows twice reboot Ubuntu, check disc space if still the same remount NTFS drives 
reboot and see if that works, Personally, i use Automatix to mount my drives I think it does a better job on my computer but that's personnel choice

---

