---
title: "SATA HD - Slow Copies, Changes to R/O Status"
date: 2007-06-14
forum: General Help
---

### Post by Anaximander Thales on 2007-06-14
Having an odd problem with a drive of mine.  It's an 80 gig SATA.  Half the drive goes to Windows, the other half to Linux.

There are 4 drives in total -- one of which is an external USB IDE drive (and is currently not mounted and shut off).  The other 2 SATA's have absolutely no problems, and the drive I'm having problems with checks out diagnostically.

The problem drive (/dev/sdc2) is mounted in fstab like so:
UUID=<blah>	/home/<user>/tmp_media	reiserfs	defaults	0	2

I've changed the mount point to /mnt/tmp_media and linked it to my home folder, also.  Regardless of how it's mounted, it results in the same problem.

Which is this.  I copy data to the drive (specifically -- raw and worked photos).  It copies a few jpegs fast, hits a raw image, pauses, speeds through a few raw images, pauses on a raw image and then hangs, eventually telling me that it can't copy the file would I like to skip it.  I obviously do, it gives the same error on another file, I skip all -- now the drive is read-only.  If I reboot, the data on the drive is lost, but I can read and write to the drive.

I initially thought it was a particular image causing the problems -- so I copied a different folder.  Similar results during the copy (quickly copies several items, hangs on an item, quickly, hang -- failure).

I then figured, since the drive has never had any data stored on the linux partition, I'd delete, recreate it and that should take care of the problem.  I'll lose part of my swap file, but todate, I haven't even taxed the machine hard enough to eat up the ram.  Removed all the linux partitions (2 -- one data, one swap).  Used fdisk to create a linux data partition, used mkfs -t reiserfs to initialize it.  Mounted it.  Copied -- hung -- read-only now.

Searching through, I thought perhaps DMA wasn't enabled -- SATA uses DMA by default, so it's not that.  Found sdparm.  Tried it, and I get an error that says:

    /dev/sdc2: ATA       WDC WD800JD-00LS  10.0
REQUEST SENSE failed, try again with '-v' option

Try it with the -v, get:

    /dev/sdc2: ATA       WDC WD800JD-00LS  10.0
    Request Sense cmd: 03 00 00 00 40 00 
request sense:  Fixed format, current;  Sense key: Illegal Request
 Additional sense: Invalid command operation code
REQUEST SENSE failed

So -- I'm not sure what to try now.

Any suggestions on what to do and what's causing the problem?

---

### Post by Anaximander Thales on 2007-06-15
Bump

---

### Post by wpshooter on 2007-06-15
Strictly a **GUESS** on my part, but do you think it may have anything to do with the FS type (reiserfs) that you are using ???

---

### Post by Anaximander Thales on 2007-06-15
I suppose it's a possibility -- however, the other two drives (which contain system information -- boot, root, var, usr & home -- separate partitions for each) are reiserfs as well -- and I'm having no problems with them.

I'll admit that I've been considering to try a different format.  I suppose I will and put an update here.

It seems as if it's not a really big problem -- there aren't many posts that can be found in google, and there isn't much information here about it here, either -- most problems are related to permissions.

I'll put an update on here later with the fs change.

---

### Post by Anaximander Thales on 2007-06-16
I tried ext3 FS.  Same results.

I thought, well -- my diags didn't show any problems, but I never checked for bad blocks.  Ran e2fsck -c -- it said 321 (I believe) blocks were bad.  Mounted it, tried a copy -- crapped out again.

---

### Post by wpshooter on 2007-06-16
> **Anaximander Thales said:**
> I tried ext3 FS.  Same results.

I thought, well -- my diags didn't show any problems, but I never checked for bad blocks.  Ran e2fsck -c -- it said 321 (I believe) blocks were bad.  Mounted it, tried a copy -- crapped out again.

I would always get the diagnostic software from the hard drive manufacturer to test the hard drive regardless of what O/S I might be running.

Hope you get it all sorted out, perhaps a new drive.

---

### Post by Anaximander Thales on 2007-06-17
Well -- all but the bad block diagnostics were from the manufacturer.

---

