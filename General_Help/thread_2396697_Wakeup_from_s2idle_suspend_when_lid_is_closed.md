---
title: "Wakeup from s2idle suspend when lid is closed"
date: 2018-07-19
forum: General Help
---

### Post by lowette on 2018-07-19
Since my upgrade to kernel 4.17.5-041705-generic (from 4.15.x) my suspend (which is s2idle, only one available on my Dell XPS13 9365) resumes with the lid closed - it didn't do that before.
When suspending by closing the lid, the suspend happens, but then gets resumed again.
When suspending from the console with the lid open, it stays suspended until I close the lid, then the resume happens again.
I tried disabling LID0 (and all others) in /proc/acpi/wakeup, but that didn't change things.

Any idea what could be triggering this unwanted resume?
In the dmesg output I don't see anything particular on what triggered this event; how can I enable more debug output wrt identifying the wakeup event?

Many thanks for any insight!

---

