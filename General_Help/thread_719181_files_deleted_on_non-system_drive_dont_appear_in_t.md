---
title: "files deleted on non-system drive dont appear in trash?"
date: 2008-03-08
forum: General Help
---

### Post by DyDx on 2008-03-08
I looked at the threads that came up when i tried posting this but none of the proposed solutions worked for me.

I'm using 7.10 Gutsy Gibbon

When I "Move to Trash" some folders on a NTFS partition they do not appear in ~/.Trash or in Trash:: within Nautilus. If I delete a folder that is on my / partition (ext3) it does appear in the trash.

The partition is being mounted with a UUID.

Does anyone have any ideas how to fix this? I didn't delete anything super important but it'd be nice to know how to fix in case I do!

---

### Post by DyDx on 2008-03-08
OK I found the solution immediately after posting :D 

To make it clearer for anyone who has this problem:

It is specific to NTFS-3G partitions. If you delete something then you can find it in /path/to/partition/.Trash-username

---

