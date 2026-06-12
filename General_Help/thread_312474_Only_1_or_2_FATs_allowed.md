---
title: "Only 1 or 2 FATs allowed"
date: 2006-12-04
forum: General Help
---

### Post by John E on 2006-12-04
Since I installed Ubuntu (about 4 weeks ago) the one thing it's done consistently well is to mount my Windows FAT32 volumes.... until today...

All of a sudden, when running the **dosfsck** section of the boot-up sequence, one of my FAT32 volumes fails with a message saying "**Currently, only 1 or 2 FATs are supported, not 246**". Thereafter, the relevant volume cannot be mounted. Under Windows, the volume checks out OK.

Does anyone know how to fix this? Alternatively, is there a way to disable **dosfsck** during boot-up?

---

### Post by John E on 2006-12-04
I'm starting to think this might be a problem with a configuration file. If I restore an old backup that I made of Ubuntu when I first installed it, the problem goes away. Then, if I re-install my current version, it comes back. Therefore I think there's something wrong with Ubuntu, rather than the drive.

Can anyone think of a file that I could check (or re-install) ??

---

### Post by John E on 2006-12-05
***groan....*** just booted up a few minutes ago (having not used Ubuntu since yesterday) but now I have TWO of my FAT32 volumes both failing with this same error!!

I think this must be a corrupted file. Is there a way to list all the files that have changed since yesterday? At least that might give me some clue as to what's happening.

---

### Post by John E on 2006-12-06
I fixed the problem. It turned out that **fstab** was corrupted. Both the non-working partitions were marked as being /dev/hda2/ when they should have been hda6 and hda7 respectively (hda2 is actually my Ubuntu volume). It looks as though this problem was causing **dosfsck** to check the wrong partition in both cases, causing the failure. I don't yet know what caused the corruption though.

---

