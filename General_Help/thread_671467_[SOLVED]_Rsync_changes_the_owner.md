---
title: "[SOLVED] Rsync changes the owner"
date: 2008-01-18
forum: General Help
---

### Post by Super TWiT on 2008-01-18
I am writing a backup script using rsync.  When I copy over another user's data, from within root, rsync changes the owner to me and changes the group to root.  This happens even though I have -a specified.  According to rsync's man page this shouldn't happen.   "--archive
    This is equivalent to -rlptgoD. It is a quick way of saying you want recursion and want to preserve almost everything (with -H being a notable omission). The only exception to the above equivalence is when --files-from is specified, in which case -r is not implied."

---

### Post by Super TWiT on 2008-01-19
Anyone?

---

### Post by Super TWiT on 2008-01-20
Fixed it!  I needed to put -A there as well to preserve the Access Control Lists.

---

