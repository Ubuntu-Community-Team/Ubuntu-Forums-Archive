---
title: "Question about using software on USB in Linux"
date: 2013-05-06
forum: General Help
---

### Post by speedruntrainer on 2013-05-06
Hello.

I have a question.
In Windows if you have something on your USB you extracted from a zip or rar before, you can use it on every computer without installing.

How does that work in Linux?

Thanks.

---

### Post by OmgItsPixelated on 2013-05-06
pretty much the same from my experiences.

---

### Post by speedruntrainer on 2013-05-06
Ok, I post here when I need help then ;)

---

### Post by slickymaster on 2013-05-06
> **OmgItsPixelated said:**
> pretty much the same from my experiences.

Assuming your USB stick is ext3 or ext4 file system, because if it's a FAT32 USB stick it's not quite so, due to permissions. You can't chmod FAT32 files, only Linux file systems and NTFS accept it.
NTFS is a POSIX-compatible file system, and it is possible to use permissions on NTFS (see [ntfs-3g manpage]("http://anpages.ubuntu.com/manpages/oneiric/man8/ntfs-3g.8.html#contenttoc") and [Ownership and Permissions]("http://www.tuxera.com/community/ntfs-3g-advanced/ownership-and-permissions/"))

---

