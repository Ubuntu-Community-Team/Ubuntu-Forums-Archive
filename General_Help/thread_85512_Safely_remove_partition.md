---
title: "Safely remove partition"
date: 2005-11-02
forum: General Help
---

### Post by RubenGonc on 2005-11-02
I use a separate partition for /tmp. Can I remove this partition without break the ubuntu installation?

Tks

---

### Post by drummer on 2005-11-02
it's needed, but i don't know if it'll be recreated if removed. Perhaps you could make a copy of /tmp in the root partition under a different name, unmount or delete the /tmp partition and rename the copy to /tmp.

It might be safer to do this using a live cd with root access to the partitions though, then you'd be able to do the copy, edit fstab to remove the mounting of the separate /tmp and safely remove the separate /tmp partition later when it's not mounted.

But remember, ALWAYS backup your data before making any changes to partitioning, etc.

* Someone pls tell me if this isn't the way to do this.. just seems like an ok way to me. *

---

