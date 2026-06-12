---
title: "unable to mount existing softraid array"
date: 2014-08-21
forum: General Help
---

### Post by dvog on 2014-08-21
Hello,

Last night I attached a ICY-BOX IB-RD3640SU3 to my Ubuntu 12.04 server via eSata. Unfortunately I did not attach any console to my server so I did not see what happened after reboot. 
Server is installed on softraid (md0), swap on md1, data on md2 - all RAID1 more data on a 4 disk RAID 5 (md3). This configuration was working stable for some years.
After attaching the console the system was unable to mount md2 and md3.

If I try to mount it manually the following error:
```
mount: wrong fs type, bad option, bad superblock on /dev/md3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
cat /proc/mdstat shows everythng ok:

```
Personalities : [raid6] [raid5] [raid4] [raid1] [linear] [multipath] [raid0] [raid10]
md2 : active raid1 sda3[0] sdb3[1]
      2901945280 blocks [2/2] [UU]

md0 : active raid1 sdb1[1] sda1[0]
      19534912 blocks [2/2] [UU]

md1 : active raid1 sdb2[1] sda2[0]
      7815552 blocks [2/2] [UU]

md3 : active raid5 sdd[1] sdf[3] sde[2] sdc[0]
      2930287488 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]

```
mdadm --examine /dev/sdf shows no errors for all drives:
```
/dev/sdf:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 4f69274f:47dd8388:f0ee56e6:eca8e294 (local to host dvog09)
  Creation Time : Mon Apr  5 16:15:35 2010
     Raid Level : raid5
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
     Array Size : 2930287488 (2794.54 GiB 3000.61 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 3

    Update Time : Thu Aug 21 09:55:55 2014
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : f7f9629d - correct
         Events : 241695

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       80        3      active sync   /dev/sdf

   0     0       8       32        0      active sync   /dev/sdc
   1     1       8       48        1      active sync   /dev/sdd
   2     2       8       64        2      active sync   /dev/sde
   3     3       8       80        3      active sync   /dev/sdf
```


Can somebody please help me to recover the data --- thank you

---

### Post by steeldriver on 2014-08-21
Hello and welcome to the forums - I've added some ```
 formatting tags to make your post easier for people to read

Can you share the actual full mount command you are using, and also any relevant dmesg output as hinted at by the mount error message? What does

[CODE]
sudo file -sL /dev/md3

```

say about the filesystem on the md3 array?

---

### Post by dvog on 2014-08-21
Hi steeldriver,

I used the following mount command:
```
sudo mount -t ext4 /dev/md3 /srv
```

dmesg shows this:
```
[  507.499952] EXT4-fs (md3): VFS: Can't find ext4 filesystem
```

```
:~$ sudo file -sL /dev/md3
/dev/md3: data
:~$

```

What puzzles me is that md0 (root partition) is working correctly, md2 (raid1) and md3 (raid5) not

---

### Post by dvog on 2014-08-22
problem solved, it was a filesystem not a softraid problem.

I was able to solve it by replacing the superblock with the following commands:

```
mke2fs -t ext4 -n /dev/md0
```

and

```
e2fsck -b 98304 /dev/md0
```

---

### Post by steeldriver on 2014-08-22
Great! please mark the thread as [SOLVED] to help others searching with a similar issue

---

