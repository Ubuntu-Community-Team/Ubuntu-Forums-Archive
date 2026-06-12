---
title: "Segfault and other strange behaviour on fresh installed System"
date: 2008-01-29
forum: General Help
---

### Post by gilbertf on 2008-01-29
Hello,
for the second time I have installed Ubuntu 7.10 Server on a machine using to different install media.
When I tried to run sudo it segfaults -> reinstalling sudo "helps", it now throws no message anymore but still not does anything. Same with depmod, just segfault. Or xfs_check -> XFS lib not found....

I know that the hardware works well, an parallel installed Windows Server on the same HW Raid has no problems.

For depmod error happens in strcmp() of /lib/tls/i686/cmov/libc.so.6

thanks a lot
Gilbert

---

### Post by rich.bradshaw on 2008-01-29
Did you burn the install cd at a low speed?

Burning them too fast often results in this type of error as random files get corrupted.

If you aren't aware of this issue, I'd try burning the cd again at the slowest possible speed, probably 1x and try again.

It will take ages to burn, but it's worth the wait as it should work fine!

---

