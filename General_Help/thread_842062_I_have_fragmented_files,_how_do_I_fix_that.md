---
title: "I have fragmented files, how do I fix that?"
date: 2008-06-27
forum: General Help
---

### Post by Drezliok on 2008-06-27
I have fragmented files, how do I fix that in linux.

I know linux doesn't need defragging but my file system say I have noncontiguous files which I think means fragmented.

Is there a way to fix this?

---

### Post by Gunman1982 on 2008-06-27
Noncontigues could stand for files which end abruptly mising some information or are shorter than the length given in the file header. When do you get the error? On boot? from a specific application?

---

### Post by mcduck on 2008-06-27
noncontinuos indeed means that the files are fragmented, nut there's no reson to do anything for it.

Linux filesystems do not suffer from fragmentation until the disk is almost completely full. (So a bit of fragmentation will not reduce your systems performance in any way.)

There are some defragmenting tools, but they are mostly simple scripts and such, made by people who really feel the need to defrag even when there realy isn't any reason. These tools do not usually give any benefits and can actually decrease your system's performance..

---

