---
title: "start-up error fsck"
date: 2007-02-03
forum: General Help
---

### Post by jmvidalvia on 2007-02-03
I moved some partitions, adapt grub.conf, but now I get this error at startup:

fsck.ext3: Unable to resolve 'UUID=360a705f-e21c-4dc7-bc47-374821b4a55a'^M
Replaying journal..
Reiserfs journal '/dev/hda3' in blocks [18..8211]: 0 transactions replayed
Checking internal tree..finished
Reiserfs super block in block 16 on 0x303 of format 3.6 with standard journal
Blocks (total/free): 3841536/2461396 by 4096 bytes
Filesystem is clean
Reiserfs super block in block 16 on 0x303 of format 3.6 with standard journal
Blocks (total/free): 3841536/2461396 by 4096 bytes
Filesystem is clean
fsck died with exit status 8

After Ctrl+D, everything works, but I would like to solve it.
Thank you!

---

### Post by dcstar on 2007-02-04
> **jmvidalvia said:**
> I moved some partitions, adapt grub.conf, but now I get this error at startup:

fsck.ext3: Unable to resolve 'UUID=360a705f-e21c-4dc7-bc47-374821b4a55a'^M
Replaying journal..
Reiserfs journal '/dev/hda3' in blocks [18..8211]: 0 transactions replayed
Checking internal tree..finished
Reiserfs super block in block 16 on 0x303 of format 3.6 with standard journal
Blocks (total/free): 3841536/2461396 by 4096 bytes
Filesystem is clean
Reiserfs super block in block 16 on 0x303 of format 3.6 with standard journal
Blocks (total/free): 3841536/2461396 by 4096 bytes
Filesystem is clean
fsck died with exit status 8

After Ctrl+D, everything works, but I would like to solve it.
Thank you!

Your /etc/fstab file has an invalid UUID because you have changed things.

There is a way to find the new UUID for the partition, and you will should manually change the file to fix it.

Do a seach for UUID and fsck, it should return some posts that have the full details on finding the new UUID.

---

### Post by Polygon on 2007-02-04
next time you boot up, run this command: (replace [partition slice] with the correct partition that is screwing up, like /dev/hda1 or something)

I think you put /dev/hda3 , but im not sure... someone please double check this!

```

sudo cp /etc/fstab /etc/fstab_backup
tune2fs -l /dev/[partition slice]

```

you should see something like this:

> tune2fs 1.35 (28-Feb-2004)
Filesystem volume name: root
Last mounted on: <not available>
**Filesystem UUID: 7d99ac7d-9fc5-42ea-8f47-f2fb92b6b8de**
Filesystem magic number: 0xEF53
Filesystem revision #: 1 (dynamic)
Filesystem features: has_journal resize_inode filetype needs_recovery sparse_super large_file
Default mount options: (none)
Filesystem state: clean
Errors behavior: Continue
Filesystem OS type: Linux
Inode count: 2076704
Block count: 4152802
Reserved block count: 207640
Free blocks: 4068278
Free inodes: 2076693
First block: 0
Block size: 4096
Fragment size: 4096
Blocks per group: 32768
Fragments per group: 32768
Inodes per group: 16352
Inode blocks per group: 511
Filesystem created: Fri Mar 4 13:13:51 2005
Last mount time: Fri Mar 4 13:15:17 2005
Last write time: Fri Mar 4 13:15:17 2005
Mount count: 1
Maximum mount count: 32
Last checked: Fri Mar 4 13:13:51 2005
Check interval: 15552000 (6 months)
Next check after: Wed Aug 31 14:13:51 2005
Reserved blocks uid: 0 (user root)
Reserved blocks gid: 0 (group root)
First inode: 11
Inode size: 128
Journal inode: 8
Default directory hash: tea
Directory Hash Seed: db72f256-ab6d-44ff-9fc5-f6256a64bcde
Journal backup: inode blocks

do that to the hard drive partition slice that fsck is complaining about, and then replace the UUID that is listed for the drive that keeps screwing up with the one that you just got with that command. Then hopefully it should work...

---

### Post by dcstar on 2007-02-04
> **Polygon said:**
> next time you boot up, run this command: (replace [partition slice] with the correct partition that is screwing up, like /dev/hda1 or something)

I think you put /dev/hda3 , but im not sure... someone please double check this!

```

sudo cp /etc/fstab /etc/fstab_backup
tune2fs -l /dev/[partition slice]

```
......

I'm not sure telling someone to use an EXT2 utility for a Reiserfs partition is going to be much help.

There is an easy way to see all the UUID mount points with a terminal command, I just cannot recall it at the moment which is why a forum search should be the best way to find it.

---

### Post by jmvidalvia on 2007-02-05
I solved it!
With:

sudo vol_id -u /dev/XXX%

I got the UID of every partition.
I checked my fstab: one hda was wrong, so I fixed it.
Its funny:
My Dapper worked, because it's fstab uses labels.
My Edgy crashed, because it uses UID's, and they changed when I changed my partitions.
Now everything is clear.
Thank you very much for your help!

---

