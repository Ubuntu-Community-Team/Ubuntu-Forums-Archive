---
title: "fakeRAID, Dual Boot, lost partition"
date: 2016-07-25
forum: General Help
---

### Post by Johnius on 2016-07-25
I lost my data partition.  My Windows boot sector got mixed up, so I tried reinstalling Windows.  The Windows partition editor erased my Logical Partition with all of my data on it.  Gparted found the RAID, found the partition table, but can't find a file system on the disk. The "Unallocated" portion of the screen shot is where all of my data is stored.  I have it mostly backed up, but I've made some important changes since the last full backup that I'd like to recover.  Can I just allocate this as Ext4 and have my data back?  Am I missing something?  I also tried testdisk and it throws all kinds of errors and doesn't display any data in the manner described by the walkthrough, but I'm willing to try anything before I cause any further damage or erase the partition.

I've tried changing the filetype in testdisk, but it won't let me view the files. It has an option to rebuild with the superblock, but I'm not familiar with how that works.  Here is the output: 

Disk /dev/mapper/pdc_fgejdfii - 1999 GB / 1862 GiB - 3906249984 sectors

     Partition                  Start        End    Size in sectors

  Linux                 1104024830 3902343677 2798318848
superblock 0, blocksize=4096 []

To repair the filesystem using alternate superblock, run
fsck.ext4 -p -b superblock -B blocksize device

---

### Post by oldfred on 2016-07-25
I do not know RAID, but is this RAID 0 or RAID 1?
RAID 0 has half of data on each drive and that may be why you have trouble with testdisk.

Windows typically destroys linux logical BIOS/MBR partition tables on major upgrades, or reinstalls. It just forgets to include them when it rewrites partition table.
But typically testdisk or parted rescue restore missing partitions in partition table and work well with standard MBR(msdos) partition tables. But RAID is different.

I do not know details of how your RAID writes its /mapper partition table. 
With MBR, all that is required is to restore start & size of partition into partition table.

---

### Post by Johnius on 2016-07-25
Thanks for the reply. It's a RAID 0+1, so best of both worlds. I can still read all the other partitions that were primary partitions. The logical partition is the issue. I tried using gparted and the rescue command, but to no use. It still sees the one partition I want as "unallocated".

---

### Post by Johnius on 2016-07-31
Alright, so I now have a .dd image of my lost partition, which is great. I can see it in gParted and wrote the partition table with TestDisk and so I can see the image.dd file. This is where I am currently stymied.  I cannot for the life of me figure out how to mount the image so I can check to see if my files are still there.  Could someone please tell me how to mount this image? I'm running from a live CD, I mount /dev/sda1 then try to mount /tmp/HDD/image.dd and it keeps throwing "Invalid argument" no matter what arguments I change or attempt.  I'm obviously doing something wrong somewhere, I just don't know enough to know where.

---

### Post by oldfred on 2016-07-31
Still know nothing about RAID.

There is this old thread:
 mount dd image of and entire disk 
[http://ubuntuforums.org/showthread.php?t=711773](http://ubuntuforums.org/showthread.php?t=711773)

---

### Post by Johnius on 2016-08-01
I went through that thread and the commands must have changed since it's creation.  I have adjusted the syntax and locations every way I can think and nothing seems to work.  Everything results with "mount.nlfs2: Error while mounting /dev/loop1 on /home/user: Invalid argument"

---

### Post by Johnius on 2016-08-01
A little more research shows that it could be that Linux is not detecting the filesystem.  I'm running TestDisk on it again to see if I can find the thing within the thing and make it all work.  I'm honestly not super hopeful, as this is my first go-around and my disk system makes things extra complicated. But we shall see what we shall see.

---

### Post by Johnius on 2016-08-01
TestDisk finds like six partitions where there should be only one and won't read any of them.  I'm guessing at this point, I've lost all of my data.  I'll try to run some diags on the actual disk since the image isn't cooperating.

---

