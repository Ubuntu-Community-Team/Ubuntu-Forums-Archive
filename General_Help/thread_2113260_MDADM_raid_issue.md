---
title: "MDADM raid issue"
date: 2013-02-06
forum: General Help
---

### Post by brdohman on 2013-02-06
I recently had a drive fail on me with my raid6. I removed the drive using

```
mdadm --fail /dev/md0 /dev/sdb1
mdadm: set /dev/sdb1 faulty in /dev/md0
```

I continued to run the raid in degraded mode, until at one point it stopped mounting. I purchased a new drive that I would like to add back to my raid. I also purchased an SSD and re-installed ubuntu. Here is my issue. When I run 

```
sudo cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md127 : inactive sdh1[0](S) sdb1[4](S) sdc1[5](S) sdf1[1](S) sde1[3](S)
      7325679325 blocks super 1.2
```

I'm not quite sure what this means and where I should take this. I've also ran 

```
sudo mdadm --examine /dev/sd[bcefh]1 >> raid.status
```

and can see that the drives listed all show off their raid information. I am not sure how to build/recreate md127 back on this machine.  Hopefully this question makes sense.

---

### Post by SaturnusDJ on 2013-02-07
Stop all inactive arrays.

Use ```
mdadm --assemble --force /dev/md0 /dev/sd[bcefh]1
```

Flag --run might be needed also.

Then you can add the new disk.

---

### Post by brdohman on 2013-02-07
Would I be using /dev/md0 or /dev/md127 as shown

```
sudo cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md127 : inactive sdh1[0](S) sdb1[4](S) sdc1[5](S) sdf1[1](S) sde1[3](S)
      7325679325 blocks super 1.2
```

---

### Post by SaturnusDJ on 2013-02-07
You can take what you want, but /dev/md127 is often used by the system when it tries an automatic assembly. Just avoid that one for your own administration.

---

### Post by brdohman on 2013-02-07
I really really appreciate your help. It's been insanely useful to me. I read through the documentation for mdadm, but wanted to make sure I did it properly as to no lose my data.

---

### Post by brdohman on 2013-02-09
I'm not sure what happened over the last day w/ my drives, but now when I run 

mdadm --detail /dev/md0 

here is my output

```
/dev/md0:
        Version : 1.2
  Creation Time : Fri Feb  8 22:52:36 2013
     Raid Level : raid6
     Array Size : 5860018176 (5588.55 GiB 6000.66 GB)
  Used Dev Size : 1465004544 (1397.14 GiB 1500.16 GB)
   Raid Devices : 6
  Total Devices : 4
    Persistence : Superblock is persistent

    Update Time : Fri Feb  8 23:20:33 2013
          State : clean, degraded 
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : the-machine:0  (local to host the-machine)
           UUID : 8f0728ad:1f538f11:fd07649b:b8bacea2
         Events : 30

    Number   Major   Minor   RaidDevice State
       0       8      129        0      active sync   /dev/sdi1
       1       8       97        1      active sync   /dev/sdg1
       2       0        0        2      removed
       3       8       33        3      active sync   /dev/sdc1
       4       8       49        4      active sync   /dev/sdd1
       5       0        0        5      removed

```

The raid no longer mounts. Any way I could get it to mount? It shows up in other devices under Disks, but doesn't really give me a way to mount it and I couldn't find a command line option to do so.

---

### Post by SaturnusDJ on 2013-02-09
What's the error message?

This should work:
```
mount /dev/md0 /mnt
```

---

### Post by brdohman on 2013-02-09
I tried the above and here is what i got

```
~$ sudo mount /dev/md0 /mnt
mount: you must specify the filesystem type

~$ sudo mount -t ext4 /dev/md0 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

I know that the filesystem is ext4. I looked at the log files and I don't see anything pertaining to the raid.

---

### Post by SaturnusDJ on 2013-02-09
And there are no errors when assembling the array?

Then you might try fsck.ext4. I think you are able to analyse first, so say no to all changes/fixes and post the output here. You want to make an image first before applying any changes.

It's strange a degraded array looks to have a corrupt filesystem.

---

### Post by brdohman on 2013-02-09
It looks as if the superblock might be bad. Should I look in to zeroing out the superblock?

```
~$ sudo fsck /dev/md0
fsck from util-linux 2.20.1
e2fsck 1.42.5 (29-Jul-2012)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/md0

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

---

### Post by SaturnusDJ on 2013-02-09
I'm pretty sure you need to run fsck.ext4, and not fsck because that's ext2 only.

Zeroing superblocks is only if you want to destroy things.

---

### Post by tgalati4 on 2013-02-09
I don't think you can use fsck on virtual devices (md0) only real devices (/dev/sda), besides, fsck won't know how to handle a single drive in a striped RAID pool.  The error message that fsck gives is common to any drive it can't read for whatever reason.  If it has a recognizable file system, it will give status of that file system.

---

### Post by brdohman on 2013-02-09
To answer a question I missed earlier. I received no errors when assembling.

Here is what I got from the fsck on the drive
```
~$ sudo fsck /dev/sdc
fsck from util-linux 2.20.1
e2fsck 1.42.5 (29-Jul-2012)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdc

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

~$ sudo fsck /dev/sdc1
fsck from util-linux 2.20.1
fsck: fsck.linux_raid_member: not found
fsck: error 2 while executing fsck.linux_raid_member for /dev/sdc1
```

---

### Post by SaturnusDJ on 2013-02-09
This is the only right command:

```
sudo fsck.ext4 /dev/md0
```

---

### Post by brdohman on 2013-02-09
I took a look at this

[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)

```
~$ sudo mke2fs -n /dev/xxx
mke2fs 1.42.5 (29-Jul-2012)
Could not stat /dev/xxx --- No such file or directory

The device apparently does not exist; did you specify it correctly?
bdohman@the-machine:~$ sudo mke2fs -n /dev/md0
mke2fs 1.42.5 (29-Jul-2012)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=128 blocks, Stripe width=256 blocks
183132160 inodes, 732502272 blocks
36625113 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
22355 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000, 214990848, 512000000, 550731776, 644972544
```

Wondering if I should follow up w/ - sudo e2fsck -b block_number /dev/xxx

---

### Post by SaturnusDJ on 2013-02-09
Sorry didn't read the link. Sounds ok, but you need to run this for ext4. And dont't run it without the -n flag or you'll lose everything.

---

### Post by brdohman on 2013-02-09
When I follow the commands on the link

```
~$ sudo mke2fs -n /dev/md0
mke2fs 1.42.5 (29-Jul-2012)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=128 blocks, Stripe width=256 blocks
183132160 inodes, 732502272 blocks
36625113 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
22355 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000, 214990848, 512000000, 550731776, 644972544
```


```
sudo e2fsck -b 32768 /dev/md0
e2fsck 1.42.5 (29-Jul-2012)
e2fsck: Bad magic number in super-block while trying to open /dev/md0

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

I tried the next two backup blocks after the first w/ the same result.

Right now, I'm not horribly concerned w/ recovering the raid, just some of the data. If there is another way this would be simpler, I'm open to it. I'm ok w/ destroying the raid if there is a way to grab the data.

---

### Post by SaturnusDJ on 2013-02-09
Destroy raid = lose data.

Again: you don't specify ext4. Mkfs.ext4 is the ext4 version, again once more do not forget the -n flag.
There must be a way to look this up without this risky command pff.

---

### Post by brdohman on 2013-02-09
> **SaturnusDJ said:**
> Again: you don't specify ext4. Mkfs.ext4 is the ext4 version, again once more do not forget the -n flag.
There must be a way to look this up without this risky command pff.

I don't follow what you're saying here. Which command are you talking about?

---

### Post by SaturnusDJ on 2013-02-09
I assumed mke2fs = mkfs.ext2. But either that's not true or the -n flag result is the same on mkfs.ext4.
So go on.

But if I see this command it reminds me also back to 3 years ago. I ran it without reading and thereby destroyed all my data. That is why I was kind of trying to hold you back. ;) You see, if you run the command without -n flag you actually overwrite you current filesystem.

---

