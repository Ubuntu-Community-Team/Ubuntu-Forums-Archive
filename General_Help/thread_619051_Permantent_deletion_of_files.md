---
title: "Permantent deletion of files"
date: 2007-11-21
forum: General Help
---

### Post by dryte on 2007-11-21
I would like to know if there are any programs for ubuntu that will permanently delete a file from a harddrive.  Not just normal delete but actually overwrite the files bytes with 0 and 1. or something like that.

Thanks

---

### Post by banewman on 2007-11-21
That's what linux does as default - read some threads about trying to recover deleted files and you'll learn that it is not an option. Delete a file and it is overwritten with 0's. :)

---

### Post by posterboy on 2007-11-21
Use shred from the command line. NOTE! It will not actually remove the file unless you say shred -u.
It makes the file un-recoverable, even from forensics. As always, the man page is your friend.

---

### Post by az on 2007-11-21
> **banewman said:**
> Delete a file and it is overwritten with 0's. :)

The data itself is left intact.  It's the pointers to the data that are deleted (zeroed) from the allocation table.

---

### Post by atlfalcons866 on 2007-11-21
Be advised using Journaling file systems (JFS,Ext3,XFS,Reiserfs,Reiser4,NTFS) all keep metadata copies in its journal for sometime. This is not the exact file unless you are using journal data on ext3. Metadata is a file about the file.

---

### Post by atlfalcons866 on 2007-11-21
Ext3 has 3 journaling options

Journal 
    (slow, but least risky) Both metadata and file contents are written to the journal before being committed to the main file system. This improves reliability at a performance penalty because all data has to be written twice. Without this setting in /etc/fstab, a file being edited in-place during a power outage or kernel panic risks being corrupted, depending on how the application is writing to the file.
Ordered 
    (medium speed, medium risk) Ordered is as with writeback, but forces file contents to be written before its associated metadata is marked as committed in the journal. This is the default on many Linux distributions.
Writeback 
    (fastest, most risky; equivalent to ext2 in some sense) Here metadata is journaled but file contents are not. This is faster, but introduces the hazard of out-of-order writes where, for example, files being appended to during a crash may gain a tail of garbage on the next mount.

---

