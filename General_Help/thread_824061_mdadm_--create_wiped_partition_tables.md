---
title: "mdadm --create wiped partition tables"
date: 2008-06-09
forum: General Help
---

### Post by azelter on 2008-06-09
I have a raid question relating to raid wiping my disk's partition table. 

The question is: is there any advantage of partitioning hard drives to be used in a raid array if you are intending to use the whole device?
i.e. is there an advantage of using /dev/sdc1 over /dev/sdc as a device in your raid array in the case that you want to use the whole disk anyway?

I am asking because of the following experience. Any comments would be welcome.

I set up a raid 6 using 8 drives. Before executing the (wrong) mdadm --create command I used fdisk to make one raid autodetect (fd) partition on each drive to be used. After that I did:
sudo mdadm --create --verbose  --auto=md /dev/md0 --level=raid6 --chunk=64   --raid-devices=8  --spare-devices=0  /dev/sd{a,b,c,d,e,f,g,h}

This resulted in what I wanted, a working raid 6 array. A couple of days later, however, I happened to use fdisk to look at one of these drives again, and it had no partitions on the drive. I then looked in the /var/log/messages and saw lines like saying "unknown partition table" for my raid disks.

I therefore failed one of my raid disks and removed it from the array and checked it with fdisk. Indeed it had no partitions. I therefore decided to put 2 new partitions on it (/dev/sdc1 and /dev/sdc2) and add it back to the array specifically making the same mistake as in my origonal command by doing the following: mdadm /dev/md0 --add /dev/sdc
Note that /dev/sdc1 and /dev/sdc2 would anyway be the wrong size for the raid array that /dev/sdc will become part of. I then rebooted to see what the message log says. It said:
kernel: [   40.413735]  sdc1 sdc2
kernel: [   40.413795] sd 2:0:0:0: [sdc] Attached SCSI disk
...
kernel: [   49.246366] md: bind<sdc>
...
kernel: [   49.729713]  disk 2, o:1, dev:sdc
So I see it detected the new partitions but anyway assembles sdc into the array.
So then I reboot again to see what it says after the next reboot and it says 'unknown partition table'. Checking with fdisk does indeed show that there are no longer any partitions on the device. Therefore adding the device back to the array caused it's partition table to be erased.

So to my question: is there any point in doing what I origonally ment to do - which was to make raid partitions on each of my 8 hard drives and then do:
sudo mdadm --create --verbose  --auto=md /dev/md0 --level=raid6 --chunk=64   --raid-devices=8  --spare-devices=0  /dev/sd{a,b,c,d,e,f,g,h}1

this time not forgetting to 1 after sd{a,b,c,d,e,f,g,h}
I assume this would leave my partition table intact ...

I have one more strange experience. If I remove sdc, repartition in to have one linux raid autodetect partition and then try to add it back with 
mdadm /dev/md0 --add /dev/sdc1
I get this error:
mdadm: add new device failed for /dev/sdc1 as 10: Invalid argument
But if I do:
mdadm /dev/md0 --add /dev/sdc
it adds it back saying:
mdadm: re-added /dev/sdc
and wiping my new partition table again!

---

### Post by fjgaude on 2008-06-09
Well, after testing, experimenting with mdadm for about three years I've found that a big raid5 or 6 array is best with one partition for each drive.

Now I know folks here have made successful raid arrays with say three partitions. When they do, they make three arrays out of the three partitions, one array for each partition.

I noramlly simply create an sda1, sdb1, etc., for each drive, --create the array, and then install the filesystem, usually ext3.

That's about it. I suggest you don't put any important data onto your array until you are satisfied with what you have, and understand the whole raid picture.

BTW, neither fdisk nor gparted really understands raid. They think there is never a valid partition table on the drives that make up an array. Use the mdadm -D command to know what is going on with arrays. Use the -Q command for individual drives. And the UUIDs that mdadm comes up with are not the same as Linux commands produce. Use blkid for that.

Hope this all helps.

---

### Post by grantemsley on 2009-05-25
I don't think there is much if any size or speed difference between using entire drives or a single partition on a drive.

I've always gone with making a single partition on the drive and using that for the array, because it avoids the confusion you ended up in when checking the disks with fdisk.  It also stops the drive from appearing as completely empty if you ever plug that drive into a windows machine.  And makes it easier to tell which drive is which when you plug a new drive in and the drive order changes.

But as long as you are aware that the drives aren't really empty, doesn't make much difference.

---

### Post by felipe1982 on 2010-01-28
I'm curious to know whether creating partitions on the DEVICES as type 0xDA (Non-FS Data) or 0xFD (Linux RAID Autodetect) make any difference.


There was a blog that suggests 0xFD is 'deprecated' and that using partition type 0xDA is suggested. Any thoughts?

---

### Post by ljwobker on 2010-01-31
one suggestion is to create a single partition per drive, then use the partitions as components of the array.  The idea behind this is that not all "1TB" drives (just an example) are exactly the same size -- so if you create partitions that are each slightly smaller than the full drive, you will be able to add/replace components later that may not be exactly the same size as the original ones.

---

### Post by bakegoodz on 2010-01-31
This is my educated guess. You created the first partitions with a utility that created your partitions with a GUID partition table. Then you tried to read it with utility that only understands the older type of partition tables. Then you ran into trouble when you repartition the drive because the original raid information was still coded on the Superblock (located at the end of the drive). Also GUID partitions create a redundant data at the end of the drive too, while old school MBR partition only write the beginning of the drive. So a GUID partition could be messed up too.  If you want to redo software raid on volume you need to use the command mdadm --zero-superblock the erase the raid information.

---

