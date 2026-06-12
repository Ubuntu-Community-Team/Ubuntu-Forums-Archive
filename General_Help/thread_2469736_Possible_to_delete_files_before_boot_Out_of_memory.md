---
title: "Possible to delete files before boot? Out of memory"
date: 2021-12-08
forum: General Help
---

### Post by QIII on 2021-12-08
Moved the General Help, as this is a request for help and not a chat.

What you have appears to be a *storage* problem, not a memory problem.

Understanding the difference is important.

Memory (think memory modules -- which in the case of the R Pi are soldered on) is a volatile, short-term store of information that the machine uses in its moment-by-moment operations.  It is constantly changing.  New bits are added and old ones discarded.  It disappears as soon as you turn the computer off.

Storage (think hard drives) is a non-volatile, long-term store of information that is available to the machine in a relatively stable form that persists across processes and across reboots.  Files live on storage media, where they can be read into memory for the machine to use, change (or not) and put back into storage.

Memory is ephemeral.  Storage is concrete.

Does that make any sense?

dd has a sinister nickname: "Disk Destroyer".  If you make a small mistake in what you tell it to do, your can lose everything.  dd expects you to understand what you are asking it to do and it doesn't ask questions to make sure you understand what you are doing.  In this case, you didn't realize what was going to happen and your *storage* media was filled.

Do you still have the original SD media?

---

