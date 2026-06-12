---
title: "Can't boot into Ubuntu after deleting Windows"
date: 2013-04-14
forum: General Help
---

### Post by Draz1 on 2013-04-14
Hello everyone,

So I foolishly deleted my WIndows partition that was installed along Ubuntu.  I had copied all my files over from windows to my home (pics, music, documents) and figured I would erase the Windows partiton to free up space since I wasn't going to use it anymore.  Now I can't even see my Ubuntu partition unless I open up a program such as testdisk.  I have found all my files that I copied over through testdisk which are located on the Ubuntu extended partition.  

I ran Boot Info Script here is the log:

Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1         599,650,302   976,771,071   377,120,770   5 Extended
/dev/sda5         969,080,832   976,771,071     7,690,240  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda5        4090ec97-913a-4639-98af-9dac5e7d960b   swap       
/dev/sr0                                                iso9660    Ubuntu 12.04 LTS i386

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)

Also I took a screen shot testdisk showing the partition:

 imgur.com/pz4PUdd

Is there anyway of recovering this partition so it is detectable?  Any help would be appreciated.

Thanks

---

### Post by Draz1 on 2013-04-14
Forgot to mention, I tried running Boot-repair, but it doesn't give me an option to repair.  The log shows "Error: Can't have a partition outside the disk!"

---

### Post by oldfred on 2013-04-14
I would go back to testdisk and see if it will restore your Linux partition(s). You only have the extended partition with swap using all of the extended partition.

What did you use to delete Windows? Gparted should have just deleted the NTFS partition, but you now have sda1 as the extended partition, but it is at the very end of the drive. Or remaining partition also was reordered.

 repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition]("https://help.ubuntu.com/community/DataRecovery#Lost%20Partition")
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by Draz1 on 2013-04-14
Thanks for the reply.

I actually used the Windows disc to delete it...

I now realize how badly I messed it all up and really hope I can recover the partition.  I have about 40GB of data I need to pull off of it.  I have tried testdisk and like I said, I can see all the partition and all the files on there.  I guess I could copy them out using testdisk?  Unfortunately, I don't have an external hard drive.

---

### Post by Impavidus on 2013-04-14
Was this a real dual boot (Ubuntu installed by booting from a dvd/usb drive) or wubi (Ubuntu installed using the installer running in windows? In the first case, I wonder how the windows boot loader got into the MBR, in the second case why there is a swap partition.

---

### Post by oldfred on 2013-04-14
Since OP has swap I assume it was a full install. And Windows partition tools do not "see" Linux partitions, so it often rewrites the partition table incorrectly.
While it really is important to have good backups, testdisk has been good at recovering missing partitions. You do need to have some idea of what your partitions were as it will find all the old versions and you cannot have overlapping partitions, so best to only restore the last configuration you had. And if you made lots of changes that can be difficult to surmise from a long list of alternative that testdisk may show.

---

### Post by Draz1 on 2013-04-14
Hey Impavidus, yes this was a full install from the Ubuntu disc.  

Would you guys say just recovering the files to an external drive is my best option?  I would of course have to buy one, but if that is a sure way of retrieving my files, I will go ahead and get one.

---

### Post by oldfred on 2013-04-14
You should be backing up on a regular basis anyway to another drive, so yes if you are willing to get another drive by all means do it.
I backup to another internal drive, to flash drives, & to DVDs, so I use a variety of backups.

---

### Post by Draz1 on 2013-04-14
Thanks for the reply.

So I'm running GParted and it is showing my extended drive as being mainly unallocated.  This is what I see:

/dev/sda1 extended 179.83GiB
    unallocated unallocated 176.16GiB

Not sure what is going on, but I do know all the files are still there.

---

### Post by Draz1 on 2013-04-14
the unallocated is part of the extended partition.

---

