---
title: "trouble enlarging logical partition"
date: 2008-03-18
forum: General Help
---

### Post by ahurd on 2008-03-18
I have a logical partition in an extended partition which has adequate extra space. When I try to use gparted on a live disk to enlarge the logical, it allows only a very slight enlargement, nothing near the extra space in the extended partition. Could anyone offer any help? Thanks.

---

### Post by Rocket2DMn on 2008-03-19
I don't have a working answer for you, but after 11 hours, you don't have any responses.  Consider this a bump for your thread as well.

I know it can be tough or impossible to resize logical partitions, because they are exactly that.  You can try shrinking the the physical partition first, then expanding the physical root of the logical partitions to use that space.  Then perhaps you will be able grow the logical partitions.
If the space that you are trying to expand into is formatted with NTFS, make sure it is defragmented first.  Always have good backups before fiddling with partitions.

---

