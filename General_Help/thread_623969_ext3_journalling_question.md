---
title: "ext3 journalling question"
date: 2007-11-26
forum: General Help
---

### Post by CrazyGuy123 on 2007-11-26
Could an expert point out the flaw in my logic here:

[LIST=1]
[*]Ubuntu uses EXT3 by default.
[*]EXT3 is a journalled filesystem.
[*]With a journalled filesystem, changes are atomic.
[*]When changes are atomic, it is impossible for the filesystem to become inconsistant.
[*]Even if only meta-data journalled, file system structure changes are still guaranteed to be atomic, and therefore consistant after a crash.
[*]If the filesystem is always guaranteed to be consistant, and there is no filesystem driver bugs, there is no reason to ever run a disk consistancy check.
[*]Ubuntu runs a filesystem check regularly by default.
[/LIST]

To me, that implies that either:
[LIST=a]
[*]My reasoning above is wrong
[*]There are suspected bugs in the implementation of EXT3, or the linux kernel, or disk drivers, which would cause corrupt disk writes, making the filesystem inconsistant without being recoverable with the journal.
[/LIST]

Can anyone point out the flaw in my reasoning...

---

### Post by scorp123 on 2007-11-26
> **CrazyGuy123 said:**
>   [*]With a journalled filesystem, changes are atomic. NOPE, they are not "atomic". Only the soon-to-be-released Reiser4 and Ext4 have that feature, current Ext3, ReiserFS, XFS and so on don't have that yet!

"Journaled" file systems only keep track of what was done to the filesystem, e.g. they compare "what is" with "what should be" and based on this try their best to repair any corruption that may have occurred. Non-journaled filesystems (such as Ext2, DOS, etc.) don't have any such possibility, they will maybe only notice "Ooops, something is wrong here but I don't know what" and then need to do a full check to find out what kind of corruption happened. That's the difference.

The idea of "atomic" transfers (e.g. a write operation either completely succeeds or completely fails; no more "half written" and thus corrupted files) is very very new and I don't know of any implementation yet (e.g. an OS that *really* uses these features).

---

### Post by CrazyGuy123 on 2007-11-26
let me re-phrase that bullet point then:

[LIST]
[*]Meta data changes are atomic - ie. a delete operation will not end up with the file removed but the space not reclaimed.
[/LIST]

This documents quite well what the ext3 journal can do:
[http://donner.cs.uni-magdeburg.de/bs/lehre/wise0001/bs2/journaling/journal-design.pdf](http://donner.cs.uni-magdeburg.de/bs/lehre/wise0001/bs2/journaling/journal-design.pdf)

It seems to boil down to everything can be reversed or completed, with the exception of file contents data.  Since errors in file data can't be either detected or corrected with a disk scan, I still don't understand why fsck is run on ext3 filesystems.

To word the question differently, what is there a disk check could pick up that the journal wouldn't have already corrected.

---

### Post by scorp123 on 2007-11-26
> **CrazyGuy123 said:**
>  To word the question differently, what is there a disk check could pick up that the journal wouldn't have already corrected. [http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)

" ... _**No checksumming in journal**_

Ext3 does not do checksumming when writing to the journal. If **barrier=1** is not enabled as a mount option (in /etc/fstab), and if the hardware is doing out-of-order write caching, one runs the risk of severe filesystem corruption during a crash. (This option is not enabled by default on almost all popular Linux distributions, and thus most distributions are at risk.)

Consider the following scenario: If hard disk writes are done out-of-order (due to modern hard disks caching writes in order to amortize write speeds), it is likely that one will write a commit block of a transaction before the other relevant blocks are written. If a power failure or kernel panic should occur before the other blocks get written, the system will have to be rebooted. Upon reboot, the file system will replay the log as normal, and replay the "winners" (transactions with a commit block, including the invalid transaction above which happened to be tagged with a valid commit block). The unfinished disk write above will thus proceed, but using corrupt journal data. The file system will thus mistakenly overwrite normal data with corrupt data while replaying the journal. If checksums had been used (if the blocks of the "fake winner" transaction were tagged with mutual checksum), the file system could have known better and not replayed the corrupt data onto the disk. ..... "

There you go.

---

### Post by scorp123 on 2007-11-26
Just to add to your comments: If you want a journaled filesystem which really can do without lengthy filesystem checks on system-boot go for XFS. I myself use XFS a lot on my Linux servers and I am quite happy with it.

[http://oss.sgi.com/projects/xfs/](http://oss.sgi.com/projects/xfs/)

".... _**# Quick Recovery**_

The XFS journaling technology allows it to restart very quickly after an unexpected interruption, regardless of the number of files it is managing. Traditional filesystems must do special filesystem checks after an interruption, which can take many hours to complete. The XFS journaling avoids these lengthy filesystem checks. .... "

---

### Post by CrazyGuy123 on 2007-11-26
Yep, but hows that different from EXT3 journals?  Both XFS and EXT3 do meta-only journalling.  Why should ext3 require constant checks when xfs requires none?

EDIT:  sorry - didn't read your first post.   I see - so it's because the assumptions that the filesystem makes about it's own write cache flushes being done properly are wrong because the hardware ignores the flush request?   I guess thats a lower level bug with particular disk types.

---

