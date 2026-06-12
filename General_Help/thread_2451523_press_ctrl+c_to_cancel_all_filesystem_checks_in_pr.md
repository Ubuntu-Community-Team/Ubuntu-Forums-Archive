---
title: "press ctrl+c to cancel all filesystem checks in progress"
date: 2020-10-06
forum: General Help
---

### Post by doom52 on 2020-10-06
Hello. I have this message during boot - "press ctrl+c to cancel all filesystem checks in progress" for about 5 seconds.

I have checked disk partitions with fsck, badblocks and smartctl and they all  show no errors/badblocks.

What can i do it that case?

---

### Post by TheFu on 2020-10-06
Are you booting from an installation flash drive, not a proper Ubuntu Installation?  
If you use a "Try Ubuntu" setup, this boots an ISO and part of the default processing in 20.04 is to validate the ISO isn't corrupted.

If the system actually is a regular install, then something about the shutdown isn't happening cleanly, so the OS thinks it needs to check the file systems.  I would boot into a "Try Ubuntu" environment or use the "Recovery Boot" option from the Grub Advanced menu, then manually run an fsck for all Linux file systems. Don't do this for Windows file systems.

---

### Post by doom52 on 2020-10-06
It is regular installation. I have already boot from a different installation and have run fsck for all linux partitions. Result is zero errors and badblocks.
What is strange that this message "press ctrl+c to cancel all filesystem checks in progress" appeared even when i boot for the first time from a bootable flash drive and ubuntu hasn't been even installed yet.

---

### Post by TheFu on 2020-10-06
For a bootable flash drive with the ISO on it, that is the expected behavior.

Depending on the file systems used, it can be set to run fsck on every file system, every time. For ext2/3/4, the **tune2fs** command let's us view and modify that setting.
```
$ sudo tune2fs -l /dev/mapper/ubuntu--vg-root |grep inter
Check interval:           0 (<none>)
```
On that system, running fsck is prevented. Seems to be a common default as I check a few other systems.
Here's one with a different value:
```
$ sudo tune2fs -l /dev/md2 |grep inter
Check interval:           15552000 (6 months)

```
The **tune2fs** manpage says:
```
       -i  interval-between-checks[d|m|w]
              Adjust the maximal time between two filesystem checks.  No  suf&#8208;
              fix  or  d  will interpret the number interval-between-checks as
              days, m as months, and w as weeks.  A value of zero will disable
              the time-dependent checking.

              It  is  strongly  recommended that either -c (mount-count-depen&#8208;
              dent) or -i (time-dependent) checking be enabled to force  peri&#8208;
              odic  full  e2fsck(8) checking of the filesystem.  Failure to do
              so may lead to filesystem corruption (due to bad disks,  cables,
              memory, or kernel bugs) going unnoticed, ultimately resulting in
              data loss or corruption.
```

On a dual boot system, I could see where something that Windows is doing resets the "file system properly closed" flag, so it gets marked as "improperly closed" and needs an fsck. I don't really know. I don't have dual boot systems.

Or it could be that only a check for that flag is showing up and fsck isn't actually running.  Does **systemd-analyze** actually show that fsck is taking long during boot?

I seldom reboot, so it hasn't really be an issue to me. The settings for my disks are to run fsck every 30 or 60 boots (can't recall), which is effectively 5 yrs, assuming I boot once a month. For example:
```
$ uptime
 16:08:19 up 24 days,  9:45,
```
That system probably has the longest uptime.  Here's a laptop:
```
$ uptime
 16:09:07 up 25 days,  2:59,
```
and a VM host system:
```
$ uptime
 16:09:32 up 5 days, 19:25,
```
As you can see, I just grabbed these from different systems within about a minute of each other.  I know the laptop needs to be rebooted. Just need to find a time when my work on it is at a good stopping point.

Thanks for this question.  I've just gone through all the file systems on my different machines and set the fsck check to be every 4 weeks. The basic command is this:
```
sudo tune2fs -i 4w /dev/md2
```
Just change the file system device. This tweak can be run on mounted, in-use, ext2/3/4 file systems.
```
$ sudo tune2fs -l /dev/mapper/ubuntu--vg-root |grep inter
Check interval:           2419200 (4 weeks)
```
Nice.

---

### Post by doom52 on 2020-10-06
Yes, when i boot ubuntu from installation flash drive i have seen this message. I installed it from this flash drive and i see it every boot.
And boot takes quite long time.

> sudo tune2fs -l /dev/mapper/ubuntu--vg-root |grep inter

shows: Check interval:           0 (<none>)

> For a bootable flash drive with the ISO on it, that is the expected behavior.
Why? Can it be expected for a normal installation since i installed ubuntu from that bootable flash drive?
I don't have dual boot either.

the whole log of tune2fs
```
tune2fs 1.45.5 (07-Jan-2020)
Filesystem volume name:   <none>
Last mounted on:          /
Filesystem UUID:          9f98df04-379e-4d4f-bf08-d6992eb51b50
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent 64bit flex_bg sparse_super large_file huge_file dir_nlink extra_isize metadata_csum
Filesystem flags:         signed_directory_hash 
Default mount options:    user_xattr acl
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              60907520
Block count:              243616768
Reserved block count:     12180838
Free blocks:              204514341
Free inodes:              58345374
First block:              0
Block size:               4096
Fragment size:            4096
Group descriptor size:    64
Reserved GDT blocks:      1024
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Sat Oct  3 12:21:43 2020
Last mount time:          Wed Oct  7 06:49:49 2020
Last write time:          Wed Oct  7 06:49:46 2020
Mount count:              4
Maximum mount count:      -1
Last checked:             Mon Oct  5 19:45:36 2020
Check interval:           0 (<none>)
Lifetime writes:          479 GB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:              256
Required extra isize:     32
Desired extra isize:      32
Journal inode:            8
First orphan inode:       24120041
Default directory hash:   half_md4
Directory Hash Seed:      6ab85b2b-3b76-4778-8751-dd22c680bc8a
Journal backup:           inode blocks
Checksum type:            crc32c
Checksum:                 0xf2fb60d4
```
looks ok to me.

---

### Post by doom52 on 2020-10-09
I copied ubuntu with dd on other disk(sdd) and i have this message on the new disk too. Something is odd.

---

### Post by doom52 on 2020-10-11
I have found this - [https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1875548](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1875548)
No one here knows about it?

---

