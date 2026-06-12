---
title: "RAID and mdadm Setup"
date: 2007-12-13
forum: General Help
---

### Post by Joshua on 2007-12-13
I need some help setting up a RAID array, but I'm having a lot of trouble finding good documentation.  Where I do find documentation, it's not very applicable to my setup.

First, I want to set up a RAID 5 array to store lots of media data.  I have a box with an 80GB drive, and Ubuntu Gutsy already installed.  I also have two 160GB drives, one 200GB drive and two 500GB drives.

I plan to combine the first three drives with the linear setting.  So it would be 160+160+200=520GB.

At that point I will have three drives that are about 500GB - perfect for RAID 5.

Now my problem - I already have most of my data on one of the 500GB drives, and no place to put it while I create the RAID 5.  To solve this problem, I planned to create a "degraded" 3-disk RAID 5 with the linear block and the other 500GB drive (one missing drive).  Then, I'd transfer all the data to the degraded RAID 5, and replace the missing drive with the third 500GB drive.  After rebuild I should have a RAID 5 with all my data, a total of 1TB of space, and protection from a single-disk failure (or multi-disk if they are all in the "linear" array).

- Will that work?

- If so, how do I do it?

-- Do I need to format all the drives to a specific type of file system?

-- Do I need to partition them to the same size?

- After I make the linear array, do I format/partition that?  How big and what type?

- After I make the RAID 5, how do I format/partition that?

- Can I use gparted to do the formatting?

- Is there a difference between using fdisk with the "linux raid auto" type and using the gparted raid flag without actually formatting anything? What if I do format it as, say, ext3?

- If not, what tool should I use?

- In my experimenting, I've noticed that mdadm seems to make a device like /dev/md0 but it also looks like it starts with a partition like /dev/md0p1.  Which am I supposed to format/partition, and which should I mount?

I know that's a lot, but I've been Googleing for three days now and can't figure it out.

Thanks for any help anyone can give.

---

### Post by Joshua on 2007-12-13
I found this post... of course I finally get the right search terms right after I make my own post.

[http://ubuntuforums.org/showthread.php?p=3420959](http://ubuntuforums.org/showthread.php?p=3420959)

But it still doesn't answer all my questions.  Like, will my proposed set-up work?  Or, do all the partitions have to be the same size for RAID 5?  That one is a big concern for me.  I'm worried that, unless the RAID daemon is smart enough, it will try to use the space on the larger disks even though the smaller disks wouldn't have the space to store the other parts of the data.  Anyway, hopefully a RAID expert will find this.

I'm really worried about just going for it because I have so much data - about 300GB.  My whole CD and DVD collections - plus photos and file backups.  I still have all the disks, but if I lose the data, it will take a really long time to re-rip all of that stuff.

---

### Post by fjgaude on 2007-12-13
I'm no expert but I have been building raid arrays for a number of months.

Okay, after you create an array, of any type, you create the filesystem for the array like,
```

sudo mkfs -t ext3 /dev/md0
```

Each drive should have been formated with ext3 and set to be Linux raid before creating the array.

In your case you will have two arrays, one for the Linear and the other for the raid5 of three disks.

mdadm is smart enough to make the raid5 array setting the three drives to be equal to the smallest. So you will have three 500G drives in the array even through the Linear array of will be bigger but the extra space will not be used by the raid5 array.

```
sudo mdadm --create /dev/md0 --linear --raid-devices=3 /dev/xxx /dev/yyy /dev/zzz
mkfs -t ext3 /dev/md0
sudo mdadm --create /dev/md1 --level=5 --raid-devices=3 /dev/md0 /dev/sdd1 missing
mkfs -ext3 /dev/md1
```


This command will show the progress of the array that is building:

```
sudo cat /proc/mdstat
```

Wait until the array is finished assembling.
Now copy from the missing disk with all your data to the /dev/md0 linear array.

```
sudo mdadm /dev/md1--add /dev/sd[missing drive name]
```

The "xxx", "yyy", missing name are the drive letters. I assume you will only use one partition, e.g., sda1, sdb1, sdc1, etc.

I've never created a linear array using mdadm. See if you can find if I'm right with the --linear optioon for the md0.

Carefully study the man pages for mdadm and get to understand all its features.

When you add the missing drive in it will take two hours or so for the array to sync up. Don't worry about that.

From what you said I think you are on your way to getting everything working the way you wish. It's a big job the first time you do it. I practiced over and over using empty disks without any data to learn. I did raid0, raid1, raid5 using up to four disks in each array until I felt confortable with the process.

That's the best I can do from memory for now... if you have questions as you go, please ask them and maybe someone or I can answer them.

Be careful, for if you make a mistake with the big disk that has all the data you will have to go to your CDs. <sigh>

Good luck.

---

### Post by Joshua on 2007-12-15
Ok, so I format all the drives to ext3, and set the RAID flag.  I used gparted to do this, as it appears that it uses the same commands that I would use (that you listed) otherwise.

Then I created the linear "array" and formatted that to ext3.  I used
```
mkfs -t ext3 /dev/md0
```
because it looked like gparted didn't see the RAID device properly.  It still shows a /dev/md0p1 partition rather than just the /dev/md0.

I've got this from fdisk at this point:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000362d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19457   156288321   fd  Linux raid autodetect

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00033088

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   fd  Linux raid autodetect

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006664c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a5010

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x17881787

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9543    76654116   83  Linux
/dev/hdb2            9544        9729     1494045    5  Extended
/dev/hdb5            9544        9729     1494013+  82  Linux swap / Solaris

Disk /dev/hdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005cb6a

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       24321   195358401   fd  Linux raid autodetect

Disk /dev/md0: 520.1 GB, 520125284352 bytes
2 heads, 4 sectors/track, 126983712 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table
```

Now I have two questions:
- Is this part normal?
```
Disk /dev/md0: 520.1 GB, 520125284352 bytes
2 heads, 4 sectors/track, 126983712 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table
```

- Also, do I need to set a RAID flag on the /dev/md0 device before I move on to creating the RAID 5?

---

### Post by fjgaude on 2007-12-15
All looks normal to me... GParted doesn't understand raid, no raid flag needs to be set after you have made the array, your md0. The /dev/md0p1 shown by GParted points to the first partition, p1. I've never used other than partition one with raid, but I think md, mdadm can handle multiple partitions if you can believe the man pages, near the bottom of the pages.

I'll trust you to get all the drive names correct as you make the raid5 array. <smile>

But before you do that, please mount the /dev/md0 and then do a sudo fdisk -l and show me the results.

---

### Post by Joshua on 2007-12-15
Here are the results from those commands:

```
joshua@Aeranth:~$ sudo mount /dev/md0 /mnt/share
[sudo] password for joshua:
joshua@Aeranth:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000362d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19457   156288321   fd  Linux raid autodetect

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00033088

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   fd  Linux raid autodetect

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006664c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a5010

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x17881787

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9543    76654116   83  Linux
/dev/hdb2            9544        9729     1494045    5  Extended
/dev/hdb5            9544        9729     1494013+  82  Linux swap / Solaris

Disk /dev/hdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005cb6a

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       24321   195358401   fd  Linux raid autodetect

Disk /dev/md0: 520.1 GB, 520125284352 bytes
2 heads, 4 sectors/track, 126983712 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table
joshua@Aeranth:~$ 
```

I also get a warning in gparted though.  It should be attached, but the text is:

```
e2label: No such file or directory while trying to open /dev/md0p1
Couldn't find valid filesystem superblock.

Couldn't find valid filesystem superblock.

dumpe2fs 1.40.2 (12-Jul-2007)
dumpe2fs: No such file or directory while trying to open /dev/md0p1

Unable to read the contents of this filesystem!
Because of this some operations may be unavailable.
```

I can open the /mnt/share in Nautilus, and write to it (only as root for now), and it says I have 452.3 GB free space.  So things sort of look good, I'm just worried about understanding how I should handle the /dev/md0 vs. /dev/md0p1 debate.  My mount command is only for /dev/md0.  Is that right?  Normally I would mount a specific partition, right?  But since fdisk doesn't see the /dev/md0p1, it seems like I should use /dev/md0 to reference the array.  It's not a concern for the linear block as long as I set up the RAID 5 properly, but then it would be a concern because I'd want to know if I can move partitions around and stuff.

By the way I really appreciate the help.  I'm already more confident about doing this.  One reason I've been including so much detail is that our discussion has been more informative and detail oriented than most of the howto's that I've found.  So I'm hoping that if I get the details in here, it will help other people that may be out there Googleing this type of thing.

---

### Post by fjgaude on 2007-12-15
Okay, all looks good. Please forget what GParted says about /dev/md0, it simply doesn't understand raid, period.

Well, I tell you, we all learn from each other as we try to help each other, one way or the other. <smile>

Change the root permission to /mnt/share to you, the user. Then you will have read/write permission. One easy way, and I tend to not use the command line as much as I can, is to:

```
gksudo nautilus
```
give your password and then go to the folder and change permissions from root to you the user.

Yes, use md0 only. Like:

```
sudo mount /dev/md0 /mnt/share/md0
```
or to what your mount point is. It can be simply /media

Okay, are you ready to create the raid5, using "missing" for that 500G drive that has all your data? After the creation we will have a few more things to do: copy all the data to the new array, /dev/md1, then after you are sure the array is fully synced, built, then add "missing" to it. Then another sync which will take two hours or so. But you can use cat /proc/mdstat to watch it progress.

Yes, it would be wonderful if you wrote a clean "how to" after this is all over. <grin>

---

### Post by Joshua on 2007-12-15
Ok, I just ran:

```
joshua@Aeranth:~$ sudo umount /dev/md0
umount: /dev/md0: not mounted
joshua@Aeranth:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active linear sdb1[2] sda1[1] hdc1[0]
      507934848 blocks 64k rounding
      
unused devices: <none>
joshua@Aeranth:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Sat Dec 15 12:07:11 2007
     Raid Level : linear
     Array Size : 507934848 (484.40 GiB 520.13 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Dec 15 12:07:39 2007
          State : active
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

       Rounding : 64K

           UUID : 5d368054:18044be2:a254d221:8a65d4f6 (local to host Aeranth)
         Events : 0.3

    Number   Major   Minor   RaidDevice State
       0      22        1        0      active sync   /dev/hdc1
       1       8        1        1      active sync   /dev/sda1
       2       8       17        2      active sync   /dev/sdb1
joshua@Aeranth:~$ sudo mdadm  --create --verbose /dev/md1 --level=5 --raid-devices=3 /dev/md0 /dev/sdd1 missing
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 64K
mdadm: /dev/md0 appears to contain an ext2fs file system
    size=507934848K  mtime=Sat Dec 15 13:48:20 2007
mdadm: /dev/sdd1 appears to contain an ext2fs file system
    size=488384000K  mtime=Wed Dec 31 19:00:00 1969
mdadm: size set to 488383936K
mdadm: largest drive (/dev/md0) exceed size (488383936K) by more than 1%
Continue creating array? y
mdadm: array /dev/md1 started.
joshua@Aeranth:~$ 
```

Now I've got:
```
joshua@Aeranth:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid5 sdd1[1] md0[0]
      976767872 blocks level 5, 64k chunk, algorithm 2 [3/2] [UU_]
      
md0 : active linear sdb1[2] sda1[1] hdc1[0]
      507934848 blocks 64k rounding
      
unused devices: <none>
joshua@Aeranth:~$ sudo mdadm --detail /dev/md1
/dev/md1:
        Version : 00.90.03
  Creation Time : Sat Dec 15 14:33:35 2007
     Raid Level : raid5
     Array Size : 976767872 (931.52 GiB 1000.21 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 3
  Total Devices : 2
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Sat Dec 15 14:33:35 2007
          State : clean, degraded
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 45f89736:4522643b:a254d221:8a65d4f6 (local to host Aeranth)
         Events : 0.1

    Number   Major   Minor   RaidDevice State
       0       9        0        0      active sync   /dev/disk/by-id/md-uuid-5d368054:18044be2:a254d221:8a65d4f6
       1       8       49        1      active sync   /dev/sdd1
       2       0        0        2      removed
joshua@Aeranth:~$ 
```

It doesn't look like it went through any rebuilding or anything.  It just came right up in degraded.  Do you think I should format it and start copying the files now?

---

### Post by fjgaude on 2007-12-15
Yes, all is good. I forgot that in building a clean array there is nothing to sync. Create filesystem now, and keep fingers crossed. After that is done. Do a df -h and see what the drives, array look like, after you have mounted both md0.

Then you unmount md0 before you create the raid5, else it will come up as "busy".

I'm not sure you will nornally want to mount md0. I think you shouldn't because it will be a "drive" of the raid5 array. I do believe I'm correct in this.

Every time you create a mount point it is as root, so you have to un-root it to "joshua" or whatever your user name is.

Now copy the data from "missing" to /dev/md0. You should be able to use Nartilus if you wish.

Ask questions if you are not dead sure of what you are doing... we do not wish to lose your data on that "missing" drive until we are sure it is on the raid5 array, which at first will only be two drives.

Ready, set, go...

---

### Post by Joshua on 2007-12-15
Shoot... it looks like I have to go run some errands.  I'll have to finish this up in a couple hours.  It's working on formatting now anyway.  I'll post the results as soon as I get back.

---

### Post by fjgaude on 2007-12-15
Okay, I'm in and out also. I see, after re-reading, that you have built the raid5, and likely didn't un-mount /dev/md0? Learn something new every hour.

After the two-disk raid5 array has a filesysystem, let's mount it and see what df -h has to say about it. And also fdisk -l. Okay?

---

### Post by Joshua on 2007-12-15
It looks like the formatting is done:

```
joshua@Aeranth:~$ sudo mkfs -t ext3 /dev/md1
[sudo] password for joshua:
mke2fs 1.40.2 (12-Jul-2007)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
122109952 inodes, 244191968 blocks
12209598 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
7453 block groups
32768 blocks per group, 32768 fragments per group
16384 inodes per group
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
        102400000, 214990848

Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 31 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
joshua@Aeranth:~$ sudo mount /dev/md1 /mnt/share
[sudo] password for joshua:
joshua@Aeranth:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb1              72G  2.7G   66G   4% /
varrun                250M   92K  250M   1% /var/run
varlock               250M     0  250M   0% /var/lock
udev                  250M  140K  250M   1% /dev
devshm                250M     0  250M   0% /dev/shm
lrm                   250M   38M  213M  15% /lib/modules/2.6.22-14-generic/volatile
/dev/md1              917G  200M  871G   1% /mnt/share
joshua@Aeranth:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000362d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19457   156288321   fd  Linux raid autodetect

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00033088

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   fd  Linux raid autodetect

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006664c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a5010

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x17881787

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9543    76654116   83  Linux
/dev/hdb2            9544        9729     1494045    5  Extended
/dev/hdb5            9544        9729     1494013+  82  Linux swap / Solaris

Disk /dev/hdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005cb6a

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       24321   195358401   fd  Linux raid autodetect

Disk /dev/md0: 520.1 GB, 520125284352 bytes
2 heads, 4 sectors/track, 126983712 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md1: 1000.2 GB, 1000210300928 bytes
2 heads, 4 sectors/track, 244191968 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table
joshua@Aeranth:~$ 
```

And I've started copying the couple hundred gigs of data over.

---

### Post by fjgaude on 2007-12-15
Wow, you are moving right along...

How do you boot your computer?

And before you add the "missing" into the array, do a sudo mdadm -D /dev/md1
just to be sure we have what we think we have.

---

### Post by Joshua on 2007-12-15
I'm still copying data.  It looks like it takes a while to copy almost 300 gigabytes.

As far as booting my system.  I'm not sure exactly what you mean.  Grub is the bootloader.    And I'm using the standard installation (Gnome) of Gutsy.

As far as booting... though, that does bring to mind several other questions.

I plan to use /etc/fstab to mount the RAID 5 array on every boot.  It will have to be there when the system comes up because I'm going to install MythTV and the backend will need to be able to find all the media files when it is run at boot time.  But will mdadm set up the array before the system tries to mount everything in the fstab file?  And I'll have to learn a lot more about how I can get mdadm to send me alerts about how the array is doing every so often.  Also, do you know if mdadm handles sleep and hibernate very well?  Or if there is a way to spin down the disks when they are not in use (this beast is loud with 6 drives and several fans in it)?  I guess the disk power management tools would also have to work well with mdadm.

---

### Post by fjgaude on 2007-12-15
Oh, I was just thinking that you likely use one drive to boot. Then the fstab file can have the /dev/md1 in it. The more I think about it the less I know.

What you are doing is okay, as far as I know. Raid within raid. You understand of course if you lose one of the six drives you are in degraded mode. And the speed of the md1 array is something else. You can test it using hdparm:

sudo hdparm -tT /dev/md1

The md1 drive will look like any other old drive to the system, but there coudl be a race issue with Ubuntu assembling md0 and then having it asseble md1 after. I'm sure you understand that.

Read the man pages for mdadm and you can get a feel for monitoring the arrays.

One last thing, a question: when you are notified that a particular drive has failed, how will you know which one to pull out, physically? <sigh>

Please make sure after the copy has been made to the two drives, before you add the third, that you access the two-array with Nautilus or with a CLI ls /dev/md1 just to make sure all the data is there.

---

### Post by Joshua on 2007-12-15
Oh yeah.  I have a separate 80Gb drive that is not part of any RAID.  Its even mounted in a different part of my case.

Then I have the 3 small drives and two other large 500Gb drives for the RAID.  And yeah, I know about losing any of the 3 smaller drives, or either of the 500Gb drives.  I chose RAID 5 because I figured it would be a good compromise between the number of drives need for the space you get, and the amount of redundancy.

I didn't know about the hdparm command.  I'll have to check it as soon as the stuff finishes copying.  (It's saying I have one more hour.)

As far as assembling the arrays in the right order, I thought that the mdadm.conf file would do that?  I'm actually not sure yet if I need to do something special to create that file or if running the create commands would do that automatically, but I figured I would check it after I get everything made.

I'm glad you mentioned about knowing which drive was failed.  I actually arranged the drives in my box in a specific order so that I would remember.  Of course it has now been several days since I hooked it all up, and I'm not sure any more. :(

That should be easy enough to figure out with several boots into the BIOS.

I will DEFINITELY be sure to check the files before I add the third drive.  While I was experimenting,  I was actually starting a couple movies and scrolling through some photos every time I change something to get some confidence in whether I would or wouldn't lose any data in this whole process.

---

### Post by fjgaude on 2007-12-15
Okay, I wish you good luck with this venture... it certainly will feel rewarding after learning, going through it all.

Your next step will be to add in the third drive to the array. I think you know how to do that.

Keep us postedo on your success.

You have to install hdparm using apt-get... I don't think it is loaded on OS install. It's a neat program and is very capable of lots of things, especially seq read and the like.

---

### Post by Joshua on 2007-12-15
Well, everything is copied.

Movies/music work.

I just got this:
```
joshua@Aeranth:~$ sudo mdadm --detail /dev/md1
[sudo] password for joshua:
/dev/md1:
        Version : 00.90.03
  Creation Time : Sat Dec 15 14:33:35 2007
     Raid Level : raid5
     Array Size : 976767872 (931.52 GiB 1000.21 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 3
  Total Devices : 2
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Sat Dec 15 22:20:03 2007
          State : clean, degraded
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 45f89736:4522643b:a254d221:8a65d4f6 (local to host Aeranth)
         Events : 0.372

    Number   Major   Minor   RaidDevice State
       0       9        0        0      active sync   /dev/disk/by-id/md-uuid-5d368054:18044be2:a254d221:8a65d4f6
       1       8       49        1      active sync   /dev/sdd1
       2       0        0        2      removed
joshua@Aeranth:~$
```

I think I'll go ahead and add the last disk.

The plan will be:
- format /dev/sdc1 to ext3
- flag it as RAID
- sudo mdadm --add /dev/md1 /dev/sdc1

<keeping my fingers crossed>

---

### Post by Joshua on 2007-12-15
So far so good.  I can still access my files.

```
joshua@Aeranth:~$ sudo mdadm --add /dev/md1 /dev/sdc1
mdadm: added /dev/sdc1
joshua@Aeranth:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid5 sdc1[3] sdd1[1] md0[0]
      976767872 blocks level 5, 64k chunk, algorithm 2 [3/2] [UU_]
      [>....................]  recovery =  0.0% (307516/488383936) finish=290.8min speed=27956K/sec
      
md0 : active linear sdb1[2] sda1[1] hdc1[0]
      507934848 blocks 64k rounding
      
unused devices: <none>
joshua@Aeranth:~$ sudo mdadm --detail /dev/md1
/dev/md1:
        Version : 00.90.03
  Creation Time : Sat Dec 15 14:33:35 2007
     Raid Level : raid5
     Array Size : 976767872 (931.52 GiB 1000.21 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Sat Dec 15 22:59:23 2007
          State : clean, degraded, recovering
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

 Rebuild Status : 0% complete

           UUID : 45f89736:4522643b:a254d221:8a65d4f6 (local to host Aeranth)
         Events : 0.618

    Number   Major   Minor   RaidDevice State
       0       9        0        0      active sync   /dev/disk/by-id/md-uuid-5d368054:18044be2:a254d221:8a65d4f6
       1       8       49        1      active sync   /dev/sdd1
       3       8       33        2      spare rebuilding   /dev/sdc1
joshua@Aeranth:~$ 
```

---

