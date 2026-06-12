---
title: "error messages &quot;no caching mode page present&quot; on boot after upgrade to 13.04"
date: 2013-05-05
forum: General Help
---

### Post by muppet317 on 2013-05-05
just upgraded to xubuntu 13.04  and everything seems to be working fine except i now get this error message when booting up before the login screen

```
[   13.348713] sd 2:0:0:0: [sdb] No Caching mode page present
[   13.348719] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   13.354565] sd 2:0:0:0: [sdb] No Caching mode page present
[   13.354571] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   13.362945] sd 2:0:0:0: [sdb] No Caching mode page present
[   13.362951] sd 2:0:0:0: [sdb] Assuming drive cache: write through
```

sdb is a 2gb sd card (fat16) in an internal sd card reader which i leave in permanently, though it just contains documents. once through the login screen the sd card can mount and work as normal. the issue is just this error message is annoying and slows down the boot time.

with my very limited knowledge i can't see  why linux would want to use a cache on this drive as there already is a cache on the main hdd that the system runs from

any ideas how i stop the system looking for a cache on the sd card?

---

### Post by 2F4U on 2013-05-05
Known problem:

[http://askubuntu.com/questions/167343/what-is-a-asking-for-cache-data-failed-warning](http://askubuntu.com/questions/167343/what-is-a-asking-for-cache-data-failed-warning)

---

### Post by muppet317 on 2013-05-07
Those look pretty similar, but neither the post on askubuntu or the bug report seem to be boot error messages and i never had a problem with 12.04 (which both these bugs refer to) but only since i upgraded to 13.04. 
Should i report it as another bug, or just wait and hope it gets fixed in a future kernel upgrade?

---

### Post by neigun on 2013-05-19
It appears to be a bug on 13.04(?) So I would post it.

---

