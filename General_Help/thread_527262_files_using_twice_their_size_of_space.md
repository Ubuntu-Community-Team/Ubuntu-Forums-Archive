---
title: "files using twice their size of space"
date: 2007-08-16
forum: General Help
---

### Post by ConfidentiaL on 2007-08-16
I solved this issue now, and I thought I should just say how:

First, on my main partition, I found a new trash /.Trash-root where the files taking up space were.
Second, the .wine directory somehow didn't count when I checked the size of my home directory, so now I know what was taking up the space there

**Original post:**
-------------
So, I decided to move my /home directory to a new partition, after I found out that ubuntu was something I really liked. I booted up with ubuntu cd as a liveCD and copied the contents of /home to the new partition. After completion I checked that the size and number of files matched on both partitions. Then I just did "Move to trash" on the old directory, edited fstab and booted up my installed system.

Then I realized that the amount of free space on both my new partition and my main partition was very low. Actually the amount of free space on my main partition hadn't changed at all, and the amount of space used on my new partition showed twice the size of what the files were.

I have checked in my home directory trashs and both of the root trashs, but nothing was there. Also, when I try to copy the files over to a new partition, the amount of files queued to move is many more than the amount of files that show when I see how much space the directories use.

Could someone please explain to me where my "ghost"-files are, and how to get rid of them?

---

### Post by dabl on 2007-08-16
When you "move to trash" the files aren't deleted, so that explains why no space was freed up. They aren't deleted until you "Empty Trash".

Trash is in a hidden folder on the partition or drive -- in your "view" menu, check "show hidden".  :)

---

### Post by ConfidentiaL on 2007-08-16
> **dabl said:**
> When you "move to trash" the files aren't deleted, so that explains why no space was freed up. They aren't deleted until you "Empty Trash".

Trash is in a hidden folder on the partition or drive -- in your "view" menu, check "show hidden".  :)

I booted with the liveCD when I "moved to trash", and as I said I checked the hidden trash directories... :/

---

