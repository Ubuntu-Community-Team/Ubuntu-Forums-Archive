---
title: "Check a backup . . . checksum?"
date: 2007-02-14
forum: General Help
---

### Post by kolinab on 2007-02-14
Hi,

So my laptop HD is nearly full. I have used Rsync to make a backup/copy of my /home partition files to my external HD. I'll be leaving some of my media files exclusively on the external to make more room on my laptop.

I didn't get any errors when I did my Rsync backup/transfer, and the size of the data sems to match. But is there a way to do a checksum on a batch of files to compare if nothing got corrupted or something? I don't really know how checksums work - maybe there is a more appropriate tool for checking that everything is hunky dory? What might that be?

Or, if doing a checksum is what I want to do, what tools do I need? How do I do it?

Thanks!

K

---

### Post by Johan! on 2007-02-14
You need md5sum and/or cfv.

Read their man pages for more info.

---

### Post by SuSUntu on 2007-02-14
**md5sum** and **cfv** are excellent tools to know about and use, but **rsync** automatically performs a checksum on the tranferred files without any parameters being set by the user.

To avoid confusion with the -c, --checksum option of rsync, the man pages provide this explanation:

> 
**-c, --checksum**
This forces the sender to checksum every regular file using a 128-bit MD4 checksum. It does this during the initial file-system scan as it builds the list of all available files. The receiver then checksums its version of each file (if it exists and it has the same size as its sender-side counterpart) in order to decide which files need to be updated: files with either a changed size or a changed checksum are selected for transfer. Since this whole-file checksumming of all files on both sides of the connection occurs in addition to the automatic checksum verifications that occur during a file's transfer, this option can be quite slow.

**Note that rsync always verifies that each transferred file was correctly reconstructed on the receiving side by checking its whole-file checksum, but that automatic after-the-transfer verification has nothing to do with this option's before-the-transfer "Does this file need to be updated?" check.**


---

### Post by kolinab on 2007-02-14
Wow. Perfect. I guess if I had read the rsync info a little more carefully I could have discovered that myself. So I'll trust rsync.

Now I'm off on a tangent learning about md5sum and cfv anyway.

Thanks for the info!

---

