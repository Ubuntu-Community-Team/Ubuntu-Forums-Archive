---
title: "Disk space dissapears"
date: 2007-05-26
forum: General Help
---

### Post by Miwashi on 2007-05-26
I downloaded about 24 Gb of files.

I then erased about 12 Gb of these ...

When I downloaded about 2Gb there was a complaint of "out of space".

Obviously the 12 Gb I deleted haven't been deleted. Does anyone have a clue of how to solve this and to get my "disk space" back.

I have done the obvious as deleting .Trash and so forth.

---

### Post by taurus on 2007-05-26
What are the outputs of these two commands from a terminal?

Applications -> Accessories -> Terminal
```
df -h
du -h ~
```

---

### Post by pmg on 2007-05-26
How did you delete the files?  Some tools move the files to a .Trash directory so they can be recovered.

Is it possible something still had the files open?  Even if you remove the directory entry for a file, if a process has it open the disk data blocks for it aren't actually freed until any processes with the file open have closed it.

---

