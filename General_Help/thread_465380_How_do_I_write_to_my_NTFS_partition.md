---
title: "How do I write to my NTFS partition?"
date: 2007-06-05
forum: General Help
---

### Post by BobLand on 2007-06-05
I'm unable to write to my PalmIV from Evolution, JPilot, KPilot, and any other sync program.  Therefore, I'd like to transfer some of the various ldif, cvs, tab, pdb, pcb, pc3 files up to the NTFS partition so I can boot into Windows and load the Palm.

Hopefully I can get it loaded to reformat the data, copy it back down to LInux and try again.

The NTFS partition says it is read-only.  I tried changing it with sudo but that didn't work.  I'm guessing as long as I can see it I should be able to change it.  No?

bobland

---

### Post by merlinus on 2007-06-05
Install ntfs-3g from Applications/Add Remove.

-merlin

---

### Post by aysiu on 2007-06-05
> **merlinus said:**
> Install ntfs-3g from Applications/Add Remove.

-merlin
More details (with screenshots) here:
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

---

### Post by BobLand on 2007-06-05
That was easy.  Are there any gotchas?  Should I return the partition to read-only.  If yes how would I do that?

Thanks.  This has been a big help!
bobland

---

### Post by GuitarRocker2562 on 2007-06-05
well, you can totally delete your partition, but it is highly unlikely now.

---

