---
title: "Hard drive failure, bad superblock ?"
date: 2007-08-20
forum: General Help
---

### Post by jba on 2007-08-20
Cheers, 

A couple of days ago my Feisty Server started acting up, and I noticed that one of the disks wouldn't mount. There were complaints in ***dmesg ***like : 

```

[82912.434063] ide: failed opcode was: unknown
[82912.434215] end_request: I/O error, dev hdg, sector 63
[82912.434225] Buffer I/O error on device hdg, logical block 7
[82915.087153] hdg: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
[82915.087174] hdg: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=64, sector=64

```

Anyway, I ran ***dd_resuce*** for a backup of the volume and it turns out that about 1MB out of the 80GB were corrupted, so I figure that there's a good chance to recover at least some of the data on it. 

But the weird thing is that I cannot run fsck on it. I'm running 

```

> fsck /dev/hdg

fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)

fsck.ext2: Bad magic number in super-block while trying to open /dev/hdg

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:

e2fsck -b 8193 <device>


```

I'm running ***mke2fs -n /dev/hdg ***to list all the alternate superblocks but I'm having no luck using these, it renders the same error as above. And I also get the same error in ***dmesg ***as in the top of this post. 

Any ideas ?

Thanks in advance.

---

### Post by kidders on 2007-08-21
Hi there,

Since you've gone to the trouble of dumping your disk's contents to a file, I would suggest running fsck (or any other utils you choose) on that, rather than the disk itself. You see, the first block of errors you posted suggests physical damage or mechanical failure.

If your disk has SMART, you might want to do some exploring ... hopefully the problems are limited to small areas of your disk, that you can instruct Linux not to try to use. Be sure to check your cables ... loose connections could also cause these sorts of issues.

Anyhow, if you're *sure* the parameters you're passing to mkfs are identical to those used to create your filesystem in the first place, not being able to identify *any* valid superblocks is very suspicious. It would require far more than 1MiB of corruption, imo.

I would suggest:
[LIST]
[*]Recreate your damaged filesystem from scratch. Instruct mkfs to create a bad block list That might take *quite* some time.
[*]Re-verify the surface of your disk, to ensure that the block map is accurate. Mechanical faults can cause bad blocks to "move around", essentially making your disk useless ... so if this happens, you need to know about it!
[*]Use your disk dump to try to recover as much data as you can. Some kinds of files are easier than others, but hopefully you can get a good deal back.[/LIST]

---

### Post by jba on 2007-08-27
> **kidders said:**
> 
Anyhow, if you're *sure* the parameters you're passing to mkfs are identical to those used to create your filesystem in the first place, not being able to identify *any* valid superblocks is very suspicious. It would require far more than 1MiB of corruption, imo.


Well, I'm not sure I'm passing the same parameters... I have no idea what parameters I used. Like I said, I used " mke2fs -n /dev/hdg " to find the superblocks, but that's only as good as the parameters used...  I seem to recall using GParted to create the filesystem, forever ago, and I'm pretty sure I was using defaults all the way.

---

### Post by jocko on 2007-08-27
I think you'll have to run fsck on a partition, not the entire drive
(i.e /dev/hdg[COLOR=Blue]1[/COLOR] and not /dev/hdg).

---

### Post by kidders on 2007-08-28
> **jocko said:**
> I think you'll have to run fsck on a partition, not the entire driveThat's certainly true .... running fsck on something other than a filesystem makes no sense. Well spotted!

> **jba said:**
> Well, I'm not sure I'm passing the same parameters... I have no idea what parameters I used.In that case, re-running mkfs won't tell you anything useful. Hopefully you won't need to now though ... assuming hdg <-> hdg1 wasn't just a typo.

---

### Post by jba on 2007-09-07
Well, true that I was running the commands on /dev/hdg and not the partition /dev/hdg1.

Running fsck on /dev/hdg1 resulted in this:

```
# fsck /dev/hdg1
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
fsck.ext2: No such file or directory while trying to open /dev/hdg1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

Same result for alternate superblocks. I'm a bit out of my depth here... /dev7hdg1 is the only partition on the drive, but it's not mounted.. is that a problem for fsck ? Can you somehow force a mount ?

---

### Post by kidders on 2007-09-07
> **jba said:**
> ```
fsck.ext2: No such file or directory while trying to open /dev/hdg1
```

That means /dev/hdg doesn't have a partition #1 on it. Assuming you're using a DOS-compatible partition scheme, that suggests there are *no* partitions on that disk. Doing a **sudo fdisk -l /dev/hdg** would confirm that.

Some possible explanations:[LIST]
[*]You don't mean "hdg" at all... but perhaps "hdf" or "hde".
[*]The very start of /dev/hdg has been badly damaged.
[*]In an earlier attempt to force your system to view /dev/hdg as a filesystem, and attempt to repair it, you overwrote your partition table.[/LIST]**Edit:** Incidentally, you should *absolutely never* attempt to use fsck on a mounted filesystem. (Just in case.)

---

### Post by jba on 2007-09-08
> 
# The very start of /dev/hdg has been badly damaged.



The one is a given I think, since dd_rescue immediately gets errors, starting from block 56 or so.  And most erroneous blocks (less than 900kB of them) comes within the first 500 MB of the 80 GB drive. 

So, what options do I have for recovering the data, assuming the partition table is borked ? The whole drive was just one giant partition. And all I had on it was about 8 GB worth of music files, so I'm counting on about 99% of that still being intact on the drive and it would be nice to be able to extract it. 

Thanks for the help everyone!

---

### Post by kidders on 2007-09-08
Hi there,

What format is your music in?

The reason I ask is that **foremost** is able to recover certain files from a damaged disk, based on their metadata & internal structures ... but it doesn't look as though MP3s are among them.

Unfortunately, if we assume your filesystem's own internal structures have been destroyed, your options are a little limited, in terms of what software would be capable of restoring your files. I would suggest reading about some of the forensic data recovery apps available from Ubuntu's repos & elsewhere. If you find one that seems promising, give it a try. What chance they have of working probably depends on the specific technique they use.

---

### Post by jba on 2007-09-08
> **kidders said:**
> Hi there,

What format is your music in?

The reason I ask is that **foremost** is able to recover certain files from a damaged disk, based on their metadata & internal structures ... but it doesn't look as though MP3s are among them.



OGG and MP3... of course. :/

---

