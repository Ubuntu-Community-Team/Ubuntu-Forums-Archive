---
title: "Inconsistency detected by ld.so"
date: 2005-06-09
forum: General Help
---

### Post by ksmith on 2005-06-09
Hello,

I logged in this morning and tried to search with apt-cache but this is the result:

```
kcs@kyel:~$ sudo apt-cache search TAO
Inconsistency detected by ld.so: dl-version.c: 230: _dl_check_map_versions: Assertion `needed != ((void *)0)' failed!
``` 
Well, that's no good. I searched google and these forums w/o any luck. Figured I'd try to reinstall apt which gets me this result:

```
kcs@kyel:~$ sudo apt-get install --reinstall apt
Reading package lists... Done
Building dependency tree... Done
Segmentation fault
``` 
Oh, vim seg faults as well.

This is a very new install with just a few packages added from the Unofficial Ubuntu 5.04 Starter Guide so I don't really know what I could have done to break it.

I may just reinstall but I'm curious to know if anyone has any insights here.

Thanks,
Kyle

---

