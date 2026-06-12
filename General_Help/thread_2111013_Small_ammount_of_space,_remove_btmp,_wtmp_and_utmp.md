---
title: "Small ammount of space, remove btmp, wtmp and utmp??"
date: 2013-01-31
forum: General Help
---

### Post by pingit on 2013-01-31
Hi,

I am opperating on a very small HDD, and trying to save every grain of MB's.

Trying to disable all the logs possible, then i got to btmp, wtmp, and utmp.

Are they safe to remove with

ln -s /dev/null /var/log/wtmp
ln -s /dev/null /var/log/btmp
ln -s /dev/null /var/run/utmp

Just wondering if it's safe, like i said very small ammount of space.

Thanks in advance.

---

