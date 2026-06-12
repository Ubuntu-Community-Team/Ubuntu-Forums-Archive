---
title: "Very slow deletion files in trash with no progress + cannot deselect trash icon."
date: 2013-12-15
forum: General Help
---

### Post by IbraM on 2013-12-15
I have a trash with about 5 000 files. When I try to clear it or just delete some selected files I see a deletion window with no progress which just freezes for a long time, doesn't show any progress and closes after all files deleted. Trash icon is selected at that moment and no mouse actions could deselect it. Other part of OS is responsible and works well but deletion is very very slow.

I see this window all the deletion time with no progress changing. Closed after all files deleted. Cannot close it.
[IMG]http://plasmon.rghost.ru/private/50990135/23d87dbe25edc94d73a768a20b38d3bb/image.png[/IMG]

This cannot be deselected.
[IMG]http://rghost.ru/private/50990165/f5c527058bcfe8b34146e4934f81e908/image.png[/IMG]

**Info**:
**OS**: Xubuntu 12.04 x86
**Core**: Linux 3.2.0-58-generic #88-Ubuntu SMP Tue Dec 3 17:40:43 UTC 2013 i686 athlon i386 GNU/Linux
**File types in trash**: pdf, deb and tar.gz.
HDD with 7200 rpm, OS is on ext4 partition
Every time I open trash from thunar it fills the list of files about ~30 sec
Deletion result is always OK but done very slow. 15 selected small (~250kb) files are deleted in ~2 min...
Files in trash a deleted from ext4 and ntfs filesystems. How to locate the reason of problem?

---

### Post by bashiergui on 2013-12-17
My Russian sucks, can you translate the pop-up window? Is &#1082;&#1086;&#1088;&#1079;&#1080;&#1085;&#1072; the trash can?
What does top look like when you're deleting them?
How much ram do you have in this machine?

---

### Post by IbraM on 2013-12-18
> **bashiergui said:**
> My Russian sucks, can you translate the pop-up window?
File Actions
Removing files...
Preparing...
> Is &#1082;&#1086;&#1088;&#1079;&#1080;&#1085;&#1072; the trash can?
Yes.
> What does top look like when you're deleting them?
Sorry, I don't know what do you mean.

> How much ram do you have in this machine?
1024 mb

---

### Post by mörgæs on 2013-12-18
**Top** is a process which runs from the command line. It shows processor load, among other things. Press q for quitting top.

Please also post a complete hardware description.

---

### Post by rnerwein2 on 2013-12-18
hi folk
if you got 5000 files in one directory - it's not a linux or unix problem. my stomage says me - you get some procedures which always are copying files
to the directory. there is a locking machanismen in the system and must be atomic. 5000 files is only your problem
chiao

---

### Post by bashiergui on 2013-12-18
Have you tried removing all the files out of trash, then delete a few at a time.

Or try using the command line and use ```
rm /path/to/file
``` just be careful with the rm command because you can delete the entire file system if you're careless.

---

