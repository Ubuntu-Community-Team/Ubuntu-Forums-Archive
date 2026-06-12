---
title: "fsck.ext3: Device or resource busy"
date: 2007-01-15
forum: General Help
---

### Post by mdd4696 on 2007-01-15
Hi all,

I just set up a RAID-1 array using mdadm, using devices sda1 and sdc1. Then I tried rebooting.

When the system boots, fsck starts to verify all of the filesystems, and it gets stuck with the error:

```
[FONT="Courier New"][SIZE="1"]fsck.ext3: Device or resource busy while trying to open /dev/sdc1
Filesystem mounted or opened exclusively by another program?
fsck died with exit status 8
   ...fail!
 * File system check failed[/SIZE][/FONT]
```

A maintenance shell comes up, and if I hit CTRL-D the system resumes booting and everything is fine.

I think what is happening is that /dev/md0 is mounted and then fsck tries to check /dev/sdc1 (part of md0), but I really have no idea how to fix this.

My /etc/fstab looks like this:

```
[FONT="Courier New"][SIZE="1"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# /dev/sdb1
UUID=9f3efbc3-76fc-45a8-8e6b-61c0743ba55a /boot    ext3    defaults        0       2
# /dev/sdb2
UUID=ca1ea623-b8f3-4462-9ecd-186f803b902b /        ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=2bb1bc71-d75f-4f3f-bb8b-1f3c9ff90acc /usr     ext3    defaults        0       2
# /dev/sdb6
UUID=a945ccb8-d150-4c5a-b503-bdeb4457ea48 /var     ext3    defaults        0       2
# /dev/sdb7
UUID=c1a7b3a6-357f-46ef-9010-cbb8c06874a2 /home    ext3    defaults        0       2
# /dev/sdb8
UUID=3a2590ca-e925-482d-a2b9-20ecda0ede38 none     swap    sw              0       0

# /dev/md0
UUID=e0af3864-9afd-49e2-91f9-4a4b9f3f1abd /srv     ext3    defaults        0       3

/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0[/SIZE][/FONT]
```

My /etc/mdadm/mdadm.conf looks like this:

```
[FONT="Courier New"][SIZE="1"]DEVICE  /dev/sda1 /dev/sdc1
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=03f67648:ac3ced01:b35281eb:1ebf1232
[/SIZE][/FONT]
```

Does anyone have any ideas?

---

### Post by hal10000 on 2007-01-15
Is your raid array working, do you have access to it?

btw, look through the last line of your fstab - i think it should be /dev/fd0 instead of just /dev.

---

### Post by mdd4696 on 2007-01-15
The RAID array works fine, and I can access all of the data. The only problem I have is the boot hang-up.

---

### Post by mdd4696 on 2007-01-15
Interesting. I changed the PASS value to 0 in /etc/fstab for /dev/md0, and the system booted up normally. (As expected, since fsck skipped scanning the array).

However, I changed the PASS value back to 2, and then the UUID=xxx to /dev/md0. I got a new error on boot:

```
[FONT="Courier New"][SIZE="1"]/dev/md0: The filesystem size (according to the superblock) is 48839600 blocks
The physical size of the device is 48839584 blocks
Either the superblock or the partition table is likely to be corrupt!


/dev/md0: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
        (i.e. without -a or -p options)
fsck died with exit status 4
   ...fail!
 * File system check failed.[/SIZE][/FONT]
```

I guess the filesystems did not get resized with the partitions somehow? So I ran the commands:

```
[FONT="Courier New"][SIZE="1"]$ sudo e2fsck -f /dev/md0
e2fsck 1.39 (29-May-2006)
The filesystem size (according to the superblock) is 48839600 blocks
The physical size of the device is 48839584 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? no

Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/md0: 438/24428544 files (5.9% non-contiguous), 1200621/48839600 blocks
$ sudo resize2fs /dev/md0
resize2fs 1.39 (29-May-2006)
Resizing the filesystem on /dev/md0 to 48839584 (4k) blocks.
The filesystem on /dev/md0 is now 48839584 blocks long.
[/SIZE][/FONT]
```

This resized the filesystem I guess. My system now boots normally!

---

### Post by blader_se on 2007-08-12
Just to fellow googler like myself who might stumble in here:

I also got this message after adding four SATA RAID5 disks to my Ubuntu 6.10 RAID1 system (As described in [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID) and [http://www.linuxforums.org/forum/debian-linux-help/60295-problems-creating-raid-5-using-mdadm.html](http://www.linuxforums.org/forum/debian-linux-help/60295-problems-creating-raid-5-using-mdadm.html)).

First I got the trouble with mdadm renaming my newly created /dev/md3 to /dev/md0 (and thus also shifting /dev/md0 -> /dev/md1, /dev/md1 -> /dev/md2 /dev/md2 -> /dev/md3) This  was described  by wkulecz on [http://ubuntuforums.org/archive/index.php/t-286066.html](http://ubuntuforums.org/archive/index.php/t-286066.html) and the cure was to recreate /etc/mdadm/mdadm.conf, edited /boot/grub/menu.lst to change the kernel option root=/dev/md0 to root=/md1 (actually I ended up with using UUID instead) and edited /etc/fstab to reflect what the device assigments would be after booting with the raid5 array active.

Now I got the fsck.ext3: Device or resource busy for /dev/hda3 (which is part of the RAID1) as described here. My cure was to regenerate /etc/blkid.tab with blkid. Looking into /etc/blkid I could see that the old /dev/md0 disk references was there, and my newly added RAID5 did not show up at all.

And now the system booted up fine.

---

### Post by glave on 2007-09-07
> **blader_se said:**
> 
Now I got the fsck.ext3: Device or resource busy for /dev/hda3 (which is part of the RAID1) as described here. My cure was to regenerate /etc/blkid.tab with blkid. Looking into /etc/blkid I could see that the old /dev/md0 disk references was there, and my newly added RAID5 did not show up at all.

And now the system booted up fine.

Kudos! This just saved me as I was trying to correct an ongoing problem I'm having, this cropped up on me as well.

---

### Post by bjourne on 2008-03-22
Thanks. This worked for me too. I just had to rm /etc/blkid.tab and reboot.

---

