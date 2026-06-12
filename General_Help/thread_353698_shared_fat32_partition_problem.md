---
title: "shared fat32 partition problem"
date: 2007-02-05
forum: General Help
---

### Post by petkoff on 2007-02-05
I've had xubuntu running on my laptop on a 10gb ext3 partition.  I keep a 10gb ntfs partition for XP, and a shared 50gb fat32 partition for documents, music, etc.

Ubuntu has no problem mounting/viewing/editing files on the fat32 partition, and can see files/folders created or edited by Windows.  However, Windows doesn't see any of the changes made by the other OS.  New files/folders are invisible, and changes in existing files don't register.

My fstab entry for the partition is:
/dev/hda2 /mnt/shared vfat defaults,umask=000 0 0

I've also tried:
/dev/hda2 /mnt/shared vfat iocharset=utf8,umask=000 0 0
and
/dev/hda2 /mnt/shared vfat auto,user,utf8,umask=000 0 0

Any suggestions?

---

