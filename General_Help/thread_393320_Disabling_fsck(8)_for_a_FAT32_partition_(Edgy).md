---
title: "Disabling fsck(8) for a FAT32 partition (Edgy)"
date: 2007-03-25
forum: General Help
---

### Post by ExplodingPickle.org on 2007-03-25
I just set up Ubuntu Edgy to dual-boot with Windows XP (on a FAT32 partition). When I boot into Ubuntu, fsck(8 ) always takes a long time to call dosfsck(8 ), which takes a long time to check my entire Windows partition. I don't usually use files on that partition anyways, and when I do I usually just mount it manually. I removed the line to mount it from /etc/fstab, but fsck(8 ) still checks it anyways. On another computer of mine with Ubuntu Edgy, it only checks the disk every 30 mounts. Is there any way to configure fsck(8 ) only to check my ext3 partition every 30 mounts, or something like that, and to never check my FAT32 partition unless I mount it?

---

### Post by simonn on 2007-03-25
Put back the line to mount the FAT fs in fstab and...

```

$ man fstab
...
If the sixth field is not present or zero, a value  of  zero  is  returned and 
fsck will assume that the filesystem does not need to be checked.
...

$ man tune2fs
...
       -c max-mount-counts
              Adjust the number of mounts after which the filesystem  will  be
              checked  by e2fsck(8).
...

```

Read the man files to make sure you understand what you are doing and make sure you have a goog backup - if you value your data anyway.

---

### Post by dcstar on 2007-03-26
> **simonn said:**
> Put back the line to mount the FAT fs in fstab and...

```

$ man fstab
...
If the sixth field is not present or zero, a value  of  zero  is  returned and 
fsck will assume that the filesystem does not need to be checked.
...

$ man tune2fs
...
       -c max-mount-counts
              Adjust the number of mounts after which the filesystem  will  be
              checked  by e2fsck(8).
...

```

Read the man files to make sure you understand what you are doing and make sure you have a goog backup - if you value your data anyway.

That command only applies to EXT2/3 filesystems, **not** DOS/FAT filesystems.

If the last character on the specific /etc/fstab line is changed to "0", then is should be checked by fsck when mounted.

---

### Post by simonn on 2007-03-26
> **dcstar said:**
> That command only applies to EXT2/3 filesystems, **not** DOS/FAT filesystems.

However...

[QUOTE=ExplodingPickle.org]
Is there any way to configure fsck(8 ) only to check my ext3 partition every 30 mounts,
[/quote]

---

### Post by dcstar on 2007-03-26
> **simonn said:**
> However...

Correct, reading the title of this particular thread and then the initial text sent me in that direction.

---

### Post by dannyboy79 on 2007-03-26
> **dcstar said:**
> That command only applies to EXT2/3 filesystems, **not** DOS/FAT filesystems.

If the last character on the specific /etc/fstab line is changed to "0", then is should be checked by fsck when mounted.

Incorrect, fsck has had capabilities to check fat partitions for awhile. You can even check out your /var/log/fsck/* and if you have any fat partitions you'll see somethign like this:
Log of fsck -C -R -A -a
Tue Mar 13 03:55:03 2007

fsck 1.39 (29-May-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda1: 220649 files, 3665979/15312004 clusters
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hdb5: 122194 files, 1681108/1876384 clusters

I don't know if it can check NTFS or not??

Also, your second statement isn't correct either. According man fstab:
The sixth field, (fs_passno), is used by the fsck(8) program to determine
     the order in which filesystem checks are done at reboot time.  The root
     filesystem should be specified with a fs_passno of 1, and other filesys-
     tems should have a fs_passno of 2.  Filesystems within a drive will be
     checked sequentially, but filesystems on different drives will be checked
     at the same time to utilize parallelism available in the hardware.  If
     the sixth field is not present or zero, a value of zero is returned and
     fsck will assume that the filesystem does not need to be checked.

Basically what I do is just make sure that my root filesystem is set at 1 and my other ext3/fat32 partitions are set at 2. A lot of people just set their FAT partitions at 0 though because they are afraid that dosfsck will harm their hard drives contents. To each is own.

---

### Post by orb9220 on 2007-03-28
> I don't know if it can check NTFS or not??

Yes if I change the 1 at the end of my ntfs and fat32 to a zero that DOES turn off disk check for those to partitions.

Have been doing this on clean install of fiesty and edgy.

---

### Post by dannyboy79 on 2007-03-28
yeah but can fsck check a ntfs partition, that's what you quoted but didn't answer? Now to be rude but I already knew this so why did you quote my line can I ask?

---

