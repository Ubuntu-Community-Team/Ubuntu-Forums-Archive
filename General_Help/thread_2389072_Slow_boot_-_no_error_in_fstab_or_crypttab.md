---
title: "Slow boot - no error in fstab or crypttab"
date: 2018-04-11
forum: General Help
---

### Post by Abdujaparov on 2018-04-11
Hi,
I installed ubuntu 17.10 on my desktop but the boot is very very slow. Ubuntu spent more then 5 minutes to startup. 3-4 minutes are spent until the login screen and after login I wait for other 1-2 minutes before desktop is shown.
Looking in forum I found that could be a problem related to swap or related to missing device inserted in /etc/fstab but no particular device is inserted there, only swapfile.
Swap seems defined correctly.
I checked /etc/crypttab too but nothing is defined there.

I checked using: systemd-analyze blame and I noticed that docker spent more than 1 minute.
I removed docker but the booting time is almost the same.

What must I check?

Thanks.

---

