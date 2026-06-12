---
title: "Unable to detect filesystem or/and partition not recognized"
date: 2013-08-23
forum: General Help
---

### Post by user_765 on 2013-08-23
The partition is there but its filesystem is unknown. The filesystem must be ext3 or ext2, more likely ext3.

[ATTACH=CONFIG]245611[/ATTACH]

```
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

dmesg | tail
VFS: Can't find ext3 filesystem on dev sda3.
VFS: Can't find an ext2 filesystem on dev sda3.

fdisk /dev/sda3 -l

Disk /dev/sda3: 51.6 GB, 51621857280 bytes
255 heads, 63 sectors/track, 6276 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sda3 doesn't contain a valid partition table
```

I tried TestDisk but it suggests very different partition table.
I'm not sure that the problem is in the partition table, because partitions look good and another partitions run well. The problem is only for sda3, probably it's filesystem.

**What else I can try before trying to find files using PhotoRec?**
My goal is to recover the filesystem, not only separate files because partition is used on production server.

The full story: My old PATA drive has 160 GB and I upgraded the system with new 1 TB SATA drive. Using dd I copied whole old drive to the new one. But the problem is not only on the new drive but also on the old. Therefore we cannot blame the copying (dd) for the situation, I think.

---

### Post by zteam2 on 2013-08-23
There is another program called gpart (not to be confused with Gparted), which can try to save your partitions.

Try that if TestDisk doesn't work.

---

### Post by 1clue on 2013-08-23
Not an expert at this, but I know you shouldn't be using fdisk.  It only understands ms-dos partition tables.  DOS partition tables became obsolete when hard disks exceeded 32 MB size.  Yes, 32 megabytes.  They've hacked it to give you bigger partitions, but if you're using a multi-terabyte drive you NEED to use GPT partitions.  You won't be able to get to all of your disk if you use the old partition table.

Also, I believe that GPT makes extended partitions unnecessary.  I believe it has support for a larger number of primary partitions.

I've been using fdisk since the late '80s or early '90s.  Never had a multi-terabyte drive until recently, I ran into all sorts of trouble with it until I found out about GPT partitions.  Fdisk does not understand them.

---

### Post by user_765 on 2013-08-26
Thank you for replies!
I'll try gpart on Saturday.
Last time when I partitioned a disk I tried to use partition table different from ms-dos (this name just sounds bad for me). But there was a problem, I don't remember exactly, maybe with labeling the partitions. Next time I'll try GPT.

---

### Post by oldfred on 2013-08-26
the fdisk command should have been sda not sda3, so that may be those errors.

Post this
sudo parted /dev/sda unit s print
       sudo blkid -c /dev/null -o list
    

If that shows valid partition entry and format then partition may just need fsck?

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sda3 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda3
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda3

---

### Post by user_765 on 2013-08-28
```
fdisk -l /dev/sda

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8f800000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6654    53448223+   5  Extended
/dev/sda2            6655       13181    52428127+  83  Linux
/dev/sda3           13182       19457    50411970   83  Linux
/dev/sda5   *        5223        6527    10482381   83  Linux
/dev/sda6            6528        6654     1020096   82  Linux swap / Solaris
/dev/sda7               1        5222    41945620+  83  Linux

Partition table entries are not in disk order

```

I cannot run parted. I can't install it, but I'll run it from live cd on Saturday and I will post the output.
```
blkid -c /dev/null -o list
device                        fs_type     label        mount point                       UUID
-----------------------------------------------------------------------------------------------------------------------------
/dev/sda2                     ext3                     /free                             ee21dc65-bd82-488b-a440-a303770368b7
/dev/sda5                     ext3        Debian       /                                 5258ab38-9026-4fd7-99c3-4071c4a9d47d
/dev/sda6                     swap                     <swap>                            
/dev/sda7                     ext3                     /third                            cb509f9f-1510-4728-a728-116d148caf70
```
```
e2fsck -fv /dev/sda3
e2fsck 1.40-WIP (14-Nov-2006)
Couldn't find ext2 superblock, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sda3

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

---

### Post by oldfred on 2013-08-28
You can try this:

 Using alternative superblock to check ext3
[http://planet.admon.org/using-alternative-superblock-to-check-ext3/](http://planet.admon.org/using-alternative-superblock-to-check-ext3/)
List backup superblocks:
sudo dumpe2fs /dev/sda3 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda3

---

### Post by user_765 on 2013-09-03
It seems there is no easy way to recover the partition.
I've restored much of the data from a backup. For now I stop trying to recover the partition.
Thank you for your help!

---

