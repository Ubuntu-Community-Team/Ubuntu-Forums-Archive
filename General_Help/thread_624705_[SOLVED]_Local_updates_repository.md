---
title: "[SOLVED] Local updates repository"
date: 2007-11-27
forum: General Help
---

### Post by BillDozer on 2007-11-27
Hi,

I have 4 PC's running Ubuntu and I was just wondering whether it would be possible to have a shared updates pool, so that when one of the PC's downloads an update it will be stored on a shared place (NFS mount for instance). When the next PC needs the same update it will get it from the shared location instead of getting it over the internet and add the packages that were not downloaded yet the same place.

Is this easy to configure?

---

### Post by b20963a2 on 2007-11-27
Have a look @
[LIST]
[*]apt-cacher
[*]apt-mirror
[/LIST]

---

### Post by BillDozer on 2007-11-28
Nice,

Will give apt-cahcer a try, sounds exactly like the thing I want. :-)

---

