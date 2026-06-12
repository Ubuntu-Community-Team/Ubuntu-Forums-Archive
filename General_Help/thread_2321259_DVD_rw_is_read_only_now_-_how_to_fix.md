---
title: "DVD r/w is read only now - how to fix?"
date: 2016-04-21
forum: General Help
---

### Post by ra7411 on 2016-04-21
Ub 14.04 lts

I've got a DVD r/w that I can't write to via copy/paste (Brasero was able write an iso to it) - it did copy/paste fine a few weeks ago.

In Disks it shows up as: /dev/sr0 (Read-Only) .

How do I get this thing back to r/w?

Thanks

---

### Post by ajgreeny on 2016-04-21
A DVD or CD filesystem is always read only.  There is nothing you can do about that, but I suspect you are trying to use the DVD in entirely the wrong way; you can not delete files from the disk but will have to erase it in order to rewrite another filesystem to it.

See this recent thread with a lot more detail:-
[http://ubuntuforums.org/showthread.php?t=2320798&p=13471656#post13471656](http://ubuntuforums.org/showthread.php?t=2320798&p=13471656#post13471656)

---

