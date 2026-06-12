---
title: "help!! can't get into my system"
date: 2007-01-24
forum: General Help
---

### Post by harty83 on 2007-01-24
I'm runningy edgy with latest updates.  I shut down my pc last night and all was well.  I started back up this morning and it crashes with something like the following

/dev/sda2 (my root filesystem) contains file system errors

Inodes that were part of a corrupted orphan linked was found

fsck died with status 4

Then it talks about running fsck manually.

So I entered maintenance mode, and ran fsck /dev/sda2 but it gives me something about bad superblocks

What do i do?

Thanks in advance! 

Alan

---

### Post by tombott on 2007-01-24
Did you try fixing the bad blocks?

Try doing ```
fsck -c -p -y
```

-c Checks for Bad Blocks
-p Is Auto Repair
- y Assumes Yes to all prompts

you may want to run without the -y but up to you

More info on fsck -

```
fsck 1.39 (29-May-2006)
Usage: fsck.ext3 [-panyrcdfvstDFSV] [-b superblock] [-B blocksize]
                [-I inode_buffer_blocks] [-P process_inode_size]
                [-l|-L bad_blocks_file] [-C fd] [-j external_journal]
                [-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list
```

---

### Post by harty83 on 2007-01-24
> **tombott said:**
> Did you try fixing the bad blocks?

Try doing ```
fsck -c -p -y
```

-c Checks for Bad Blocks
-p Is Auto Repair
- y Assumes Yes to all prompts

you may want to run without the -y but up to you

More info on fsck -

```
fsck 1.39 (29-May-2006)
Usage: fsck.ext3 [-panyrcdfvstDFSV] [-b superblock] [-B blocksize]
                [-I inode_buffer_blocks] [-P process_inode_size]
                [-l|-L bad_blocks_file] [-C fd] [-j external_journal]
                [-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list
```

I ran fsck -c -p but I get something like

```

/dev/sda2: inodes that were part of a corrupted orphan linked list found
/dev/sda2: unexpected inconsistancy.  Run fsck manually.

```

What do I do now?

---

### Post by tombott on 2007-01-24
try using -r as well this is the interactive mode it may give you more options

---

### Post by harty83 on 2007-01-24
> **tombott said:**
> try using -r as well this is the interactive mode it may give you more options

thanks!  did that and said yes to everything.  now I'm up and running.

Thanks!

---

### Post by tombott on 2007-01-24
Good stuff, am glad to hear it.

It does sound like you have problems with your HD though so if I was you I would back up your system to another HD as soon as possible.

Tom.

---

