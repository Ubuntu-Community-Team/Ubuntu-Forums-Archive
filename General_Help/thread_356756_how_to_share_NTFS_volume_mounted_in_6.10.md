---
title: "how to share NTFS volume mounted in 6.10"
date: 2007-02-08
forum: General Help
---

### Post by shredswithpiks on 2007-02-08
So I've got my NTFS volumes all mounted up and read/writable

is there any way I can share folders from volume? When I attempt to share it from the gnome gui it tells me "cannot access [whatever folder]" and won't hold the settings on the share.

???

---

### Post by Sef on 2007-02-08
Linux can read NTFS, but not write to it.  Linux and Windows can write to ext2, ext3, and FAT32.  If you want to write to NTFS, then you need to download some beta software: [ntfs-3g]("http://ubuntuforums.org/showthread.php?t=217009&highlight=write+NTFS").

---

