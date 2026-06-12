---
title: "/ filesystem read-only at first boot"
date: 2005-10-17
forum: General Help
---

### Post by carmelo on 2005-10-17
Hi, i'm using Ubuntu 5.10 breezy preview updated every day.

Every mornig, at the first boot after few minutes the / filesystem is mounted read-only and i must reboot.
After the reboot i have no problem for all the day.

I tried with kernel 2.6.12-9-386 and with 2.6.12-9-686-smp (I have e PIV 3 GHz HT) with no results.

Any suggestions ?

Thanks.

---

### Post by carmelo on 2005-11-14
Problem resolved.

It was a memory problem discovered by memtest86+.
I replace DIMM with problem and now i have no problem.

---

