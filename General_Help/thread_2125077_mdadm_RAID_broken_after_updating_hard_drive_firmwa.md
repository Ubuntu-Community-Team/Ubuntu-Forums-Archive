---
title: "mdadm RAID broken after updating hard drive firmware"
date: 2013-03-12
forum: General Help
---

### Post by quickk on 2013-03-12
Hi everyone, 

    I have a RAID array with 2 drives, using mdadm.   The seagate drives that I am using have really loud seeking noises that really annoy me so I updated the hard drive firmware (I read that the new firmware might make the drives more quiet).    Upon re-booting, I can't get the raid array to start.  This is what I get:

```
sudo mdadm --assemble --scan
mdadm: failed to add /dev/sdb1 to /dev/md/1: Invalid argument
mdadm: failed to add /dev/sda1 to /dev/md/1: Invalid argument
mdadm: failed to RUN_ARRAY /dev/md/1: Invalid argument

```

Any ideas as to what I should do?

---

### Post by SaturnusDJ on 2013-03-13
Try manually:
```
mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1
```

When that doesn't work, you can try adding the --force and --run flags in the command.

---

### Post by quickk on 2013-03-13
I'm afraid that I just completely fubared my array and lost my data... I didn't know what to do and thought that if I just re-created the array with the same command I used to originally create it, then everything would be back.   So I did (before having seen your reply):

```
sudo mdadm --create /dev/md1 --metadata 1.2 --level=10 --layout=f2 --raid-devices=2 /dev/sda1 /dev/sdb1

```

This took about 6 hours to complete.   The problem is that now the array is not mounted.   Trying to do ```
sudo mdadm --assemble --scan
```
returns nothing (usually this would tell me that the array was started or something).   Looking in /dev for my array I found /dev/md127 (shoulnd't it of create /dev/md1 instead?).   Running ```
sudo mdadm --detail /dev/md127
``` gives ```
/dev/md127:
        Version : 1.2
  Creation Time : Tue Mar 12 21:27:15 2013
     Raid Level : raid10
     Array Size : 1951135744 (1860.75 GiB 1997.96 GB)
  Used Dev Size : 1951135744 (1860.75 GiB 1997.96 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Wed Mar 13 07:10:41 2013
          State : clean 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

         Layout : far=2
     Chunk Size : 512K

           Name : sacapus:1  (local to host sacapus)
           UUID : 0d8a05ae:50cdc3a3:54527ace:a2c665de
         Events : 19

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1

```

I really don't know what's going on, and am no expert with mdadm.   How do I get my data back?   I really appreciate any help.

---

### Post by quickk on 2013-03-13
Some more information: running ```
dmesg
``` tells me ```
[  271.270722] EXT3-fs (md127): error: can't find ext3 filesystem on dev md127.
[  271.276128] EXT4-fs (md127): VFS: Can't find ext4 filesystem
[  271.276309] FAT-fs (md127): invalid media value (0x60)
[  271.276311] FAT-fs (md127): Can't find a valid FAT filesystem
[  331.201214] EXT4-fs (md127): VFS: Can't find ext4 filesystem
[  383.964711] EXT3-fs (md127): error: can't find ext3 filesystem on dev md127.
[  383.972124] EXT4-fs (md127): VFS: Can't find ext4 filesystem
[  383.972239] FAT-fs (md127): invalid media value (0x60)
[  383.972242] FAT-fs (md127): Can't find a valid FAT filesystem

```
Yikes!   Is the situation hopeless?

---

### Post by SaturnusDJ on 2013-03-13
You recreated, but forgot the --assume-clean flag. This is no problem if resync/recovery doesn't start afterwards. In your case, that did happen...so as far as I know everything is lost.

---

### Post by quickk on 2013-03-13
That makes me very sad.   I do have the most important stuff backed up but still will lose some things.   Just so that I know, why do I need the --assume-clean flag?  I'm starting to wonder why I am even bothering with the raid array.   It seems like the probability of messing something up is much higher than the probability of a drive failure (I've had 2 drive failures in the last 20 years of using a computer, but I've already messed up at least twice in the last year of trying to use a raid array).

---

### Post by SaturnusDJ on 2013-03-13
The --assume-clean flag, prevents the array from calculating parity.

When the data is still there this should work:
```
mount /dev/md127 /mnt
```

---

### Post by SaturnusDJ on 2013-03-13
But how can you have a non-degraded raid 10 array with only two disks?

---

### Post by quickk on 2013-03-13
> 

    But how can you have a non-degraded raid 10 array with only two disks? 



mdadm is capable of doing this with only two drives: you get the read speed of raid 0 since the reads can be done in parallel.  See: [http://en.wikipedia.org/wiki/RAID#RAID_10](http://en.wikipedia.org/wiki/RAID#RAID_10).   I've benchmarked my setup and this indeed works---I get around 240 MB/s read with only two drives in this raid 10 setup.

---

### Post by SaturnusDJ on 2013-03-13
Okay. But no write benefits? If so, the setup must be similar to raid1. In that case there is a chance the data is still there.
The mount did not work?

---

### Post by quickk on 2013-03-13
Unfortunately, the mount does not work.  I get the following error
```
sudo mount /dev/md127 /mnt/
mount: you must specify the filesystem type

```

I just found a post [http://serverfault.com/questions/347606/recover-raid-5-data-after-created-new-array-instead-of-re-using]("http://serverfault.com/questions/347606/recover-raid-5-data-after-created-new-array-instead-of-re-using") that describes a situation very similar to mine.   I'll have to go through it carefully to try to understand what to do, but I'm now mildly optimistic that I'll be able to get my data back.

---

### Post by SaturnusDJ on 2013-03-13
Ok you can try that. Filesystemcheck sounds good. But watch out, don't say yes immediately if programs ask if they shall fix it for you.

If all of this fails, it might be possible to mount a single disk, as I've done with raid1.

---

### Post by quickk on 2013-03-20
Unfortuntately, nothing I tried got my data back.   I did have the most important things backed up, but it still sucks!   I took the drives out of my machine in case I find a way to recuperate the data in the future, but I'm not holding my breath.  Thank you for your help though!

---

