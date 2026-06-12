---
title: "Another issue with read only file system"
date: 2023-01-27
forum: General Help
---

### Post by winston61 on 2023-01-27
Ubuntu 22.04 Deskmate on Raspberry pi 4(4g). Entire file system is read only. Seeking help all suggestions have failed. Others are just incomprehensible. If I reburn the sd card and reinstall, is  there a way to make the file system r/w?

---

### Post by TheFu on 2023-01-27
Yes, but when a file system goes read-only, that's the file system trying to protect itself when a failure is imminent.  I've never seen a file system repeatedly go read-only unless it was going to fail shortly.  Shortly could be today or in 1 month, but it is going to fail.

That applies to SSDs too.  I've had 2 SSDs go read-only before they failed.  I think that was pure luck, since SSDs often just fail, without any warning first.

I'm assuming there haven't been power cuts.  If anyone yanks the power from the computer, the file system needs to be fsck'd at the next startup to ensure the journal is replayed and cleaned.  Journaled file systems are great!  Non-journaled file systems have a place, but they don't handle unexpected issues cleanly and the fsck can take much longer.  Of course, journaled file systems are harder on flash storage like SDHC/microSD and thumb-drive flash storage.  For SSDs and normal HDDs, you definitely want to use journaled file systems whenever possible.

---

### Post by ActionParsnip on 2023-01-27
fsck the SD card in another Linux system to check health, then replace in the Pi

---

