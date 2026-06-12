---
title: "Problems using JFS and mdadm"
date: 2008-02-20
forum: General Help
---

### Post by effort on 2008-02-20
Hi all,

Having problems using three Samsung HD501LJ 500GB disks in a software raid5 array formatted with JFS. Using a Silicon Image sil3114 card. Every hour or so I get errors:

ERROR: (device md0): DT_GETPAGE: dtree page corrupt

Sometimes I get C stacks too:

Feb 20 17:44:59 futility kernel: [347119.786047] ERROR: (device md0): DT_GETPAGE: dtree page corrupt
Feb 20 18:45:43 futility kernel: [350760.238625]  [<f0e9b15a>] __get_metapage+0x39a/0x400 [jfs]
Feb 20 18:45:43 futility kernel: [350760.238668]  [__wake_up+56/80] __wake_up+0x38/0x50
Feb 20 18:45:43 futility kernel: [350760.238684]  [<f0e9a695>] release_metapage+0xc5/0x150 [jfs]
Feb 20 18:45:43 futility kernel: [350760.238700]  [<f0e92fee>] dtReadFirst+0x11e/0x220 [jfs]
Feb 20 18:45:43 futility kernel: [350760.238712]  [filldir+172/224] filldir+0xac/0xe0
Feb 20 18:45:43 futility kernel: [350760.238723]  [filldir+0/224] filldir+0x0/0xe0
Feb 20 18:45:43 futility kernel: [350760.238727]  [<f0e961f4>] jfs_readdir+0x4d4/0x1300 [jfs]
Feb 20 18:45:43 futility kernel: [350760.238744]  [filldir+0/224] filldir+0x0/0xe0
Feb 20 18:45:43 futility kernel: [350760.238752]  [<f0ea3645>] jfs_get_acl+0xe5/0x100 [jfs]
Feb 20 18:45:43 futility kernel: [350760.238770]  [<f082d18f>] apparmor_inode_permission+0x4f/0x70 [apparmor]
Feb 20 18:45:43 futility kernel: [350760.238786]  [<f0ea3970>] jfs_permission+0x0/0x10 [jfs]
Feb 20 18:45:43 futility kernel: [350760.238797]  [permission+270/288] permission+0x10e/0x120
Feb 20 18:45:43 futility kernel: [350760.238807]  [may_open+101/624] may_open+0x65/0x270
Feb 20 18:45:43 futility kernel: [350760.238820]  [cp_new_stat64+249/272] cp_new_stat64+0xf9/0x110
Feb 20 18:45:43 futility kernel: [350760.238846]  [sys_fstat64+30/48] sys_fstat64+0x1e/0x30
Feb 20 18:45:43 futility kernel: [350760.238853]  [filldir+0/224] filldir+0x0/0xe0
Feb 20 18:45:43 futility kernel: [350760.238856]  [vfs_readdir+148/176] vfs_readdir+0x94/0xb0
Feb 20 18:45:43 futility kernel: [350760.238865]  [sys_getdents+107/192] sys_getdents+0x6b/0xc0
Feb 20 18:45:43 futility kernel: [350760.238875]  [sysenter_past_esp+107/161] sysenter_past_esp+0x6b/0xa1

I then run a fsck and lose a few more files :/

I'm not sure what's wrong. The files are copied from older disks, some of which have bad blocks, however some data was lost after fscking that came from a drive that has no bad blocks.

Some info:

rich@futility:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sda1[0] sdc1[2] sdb1[1]
      976767872 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]

unused devices: <none>

Currently running 2.6.22 with mdadm v2.6.2

Can anyone help me? Am getting annoyed by the whole thing...

---

### Post by effort on 2008-02-21
Hey everybody,

Is there anything else I could include to make the problem easier to explain? Let me know :)

---

### Post by effort on 2008-02-21
After some investigation, it seems to happen at times when mt-daapd does a rescan of music found on this raid partition via a symbolic link on another disk. Doesn't happen every time...

---

### Post by fjgaude on 2008-02-21
What does

```
sudo mdadm -D /dev/md0
```

show?

And have you run fsck on the mounted array?

---

### Post by effort on 2008-02-26
rich@futility:~$ sudo mdadm -D /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Tue Feb 12 23:35:13 2008
     Raid Level : raid5
     Array Size : 976767872 (931.52 GiB 1000.21 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Feb 26 11:54:52 2008
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 9c6b9f62:568706ce:8b6f310b:f9d54333 (local to host futility)
         Events : 0.1478

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1



Running fsck just moves a few files to lost+found

---

### Post by fjgaude on 2008-02-26
Maybe you are having a drive that is going bad.

Wonder if JFS could be at issue, likely not.

---

### Post by effort on 2008-03-10
Might be right. Tried uninstalling mdadm and it seemed fine for a while, then it started regularly throwing this error in kern.log:

Mar 10 06:25:56 futility kernel: [905059.785933] ERROR: (device md0): DT_GETPAGE: dtree page corrupt

Same time every day. If it's tripping up on any periodical jobs, it might be a bad drive, although the drives were brand new when they started throwing errors. Shall run some bad sector checks on the drive.

---

### Post by effort on 2008-03-12
Few runs of badblocks -s -v -c 10240 over the drives over the night returned nothing of interest. All drives seem clean. Still wondering what the problem could be...

---

### Post by ramjet_1953 on 2008-03-12
Three questions, one that was asked previously:

1. when you ran fsck, was the drive mounted? That can cause big problems.

2. Is there any reason why you are using JFS? 

3. I'm wondering if it is worth saving your data, re-formatting and trying ext3?

Regards,
Roger :cool:

---

### Post by articpenguin on 2008-03-12
whats wrong with JFS? I use and i have no problems with it.

---

### Post by effort on 2008-03-12
1. when you ran fsck, was the drive mounted? That can cause big problems.

Nope. I ran fsck on /dev/md0 when the drive was unmounted. I guess if I had run fsck with the drive mounted, I'd be looking at widespread damage rather than a few files being leaked every so often.

2. Is there any reason why you are using JFS?

None. I've heard that other people are using it for raid, and I wanted to give it a go. Performance is comparable to ext3.

3. I'm wondering if it is worth saving your data, re-formatting and trying ext3?

A good point. However, there's a lot of data on the raid, and saving it somewhere will prove difficult. Furthermore, why?

---

### Post by fjgaude on 2008-03-12
It would be a good idea to figure out a way to backup you important data. No matter how much raid we have sooner or later we are going to have to call up the backup.

Look at the way IT shows use raid with multiple backup options in play.

You could be having a random error in one or more of your present drives and fsck doesn't catch it on one pass... random errors are so hard to tract down... it's the bain of many an existence.

Let us know if you find out what is causing your problems.

---

### Post by effort on 2008-03-14
Well of course :) My extra-important stuff, like photos and music, is burnt onto DVDs. 

I've run a readonly badblocks check on all three drives. I've done this five times per drive and have found no bad blocks.

I've been looking through the files that were put into lost+found and they have all occurred on files that were copied from a failing hard drive. Perhaps the files themselves contain inconsistencies, which are only picked up intermittently by processes that do background scanning, for example updatedb or mt-daapd? In which case, how do I repair these files?

---

### Post by effort on 2008-03-18
More fun:

Mar 18 06:30:32 futility kernel: [1595748.810963] ERROR: (device md0): dbAlloc: the hint is outside the map
Mar 18 06:30:32 futility kernel: [1595748.857085] attempt to access beyond end of device
Mar 18 06:30:32 futility kernel: [1595748.857097] md0: rw=1, want=584115604352, limit=1953535744
Mar 18 06:30:32 futility kernel: [1595748.857277] attempt to access beyond end of device
Mar 18 06:30:32 futility kernel: [1595748.857282] md0: rw=1, want=584115604360, limit=1953535744
Mar 18 06:30:32 futility kernel: [1595748.857293] attempt to access beyond end of device
Mar 18 06:30:32 futility kernel: [1595748.857297] md0: rw=1, want=584115604368, limit=1953535744

Suddenly I'm thinking that the machine has been named well...

---

### Post by effort on 2008-03-18
Just to add some context:

I've got three Samsung SpinPoint HD501LJ 500GB SATAII hard drives with one 500G partition created on each. I then used mdadm to create a raid5 array across three drives, which got me a 970GB partition in /dev/md0. I then formatted this to JFS. Then fun :(

---

