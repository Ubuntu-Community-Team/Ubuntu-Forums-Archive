---
title: "problem on startup: fsck.vfat: Permission denied"
date: 2007-03-31
forum: General Help
---

### Post by FAT_C on 2007-03-31
i got a problem when i startup my linux, it jump to text mode and get some fail
it asked me to check /var/log/fsck/checkfs
then i will be in text mode of root, and i can use "Control+D" to continuous with graphic mode(to login screen)

below is what inside checkfs

Log of fsck -C -R -A -a
Sat Mar 31 13:31:01 2007

fsck 1.39 (29-May-2006)
fsck.vfat: Permission denied
fsck died with exit status 8

Sat Mar 31 13:31:01 2007
----------------

does anyone know how to fix this problem??

thx,&& regard

---

### Post by acormack on 2007-04-01
what partitions do you have on the hard disk?

when did it start happening?

had anything changed at that time?

---

### Post by FAT_C on 2007-04-01
> **acormack said:**
> what partitions do you have on the hard disk?

when did it start happening?

had anything changed at that time?

i have more than 4 partitions with 3 physical harddisks
before that happen, i installed Beryl,
and reinstall windows XP on the other partition,
i recover "vista" boot menu, then recover grub

yes, i got three systems in a computer

regard

---

