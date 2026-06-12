---
title: "Gparted froze. 500gig now unallocated."
date: 2008-05-23
forum: General Help
---

### Post by resonanttoe on 2008-05-23
Hi guys.

Ok the title is kind of a lie. Gparted didn't freeze, the whole system locked up trying to join a wireless network. More on that later. 

Anyway, its an external terabyte harddrive that I was trying to merge back into one single partition. (One was Ext3 and the other NTFS. The EXT3 partition had all my lovable data on it) The NTFS partition is still there, but the EXT3 has transformed into unallocated space. 

From reading around it seems as though some careful manipulations on the FSCK command is required, which I intend to try when I get home. However, I just thought I'd ask of any ideas on how to get that partition and said lovable data back in tact. 

Cheers
-Paul

---

### Post by ibuclaw on 2008-05-23
There is a package called testdisk in the repositories.

It recovers lost partitions brilliantly, but unfortunately, you can't recover the names (Comes out as gobble goop).

If you have enough space in your home folder (or on your NTFS drive), make a directory called "recover" and recover everything into that folder.
Check that most things appear to be there, then it should be safe to format the empty space back to ext3.

Regards
Iain

---

