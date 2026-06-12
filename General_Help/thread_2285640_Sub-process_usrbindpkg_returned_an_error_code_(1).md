---
title: "Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2015-07-07
forum: General Help
---

### Post by Roibeard on 2015-07-07
Hi all,

Fairly new  user here:
Ubuntu 14.04 LTS
got some problems relating to dpkg:

dpkg: error processing package dbconfig-common (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
Errors were encountered while processing:
 dbconfig-common


Failed to load the package list

This is a serious problem. Try again later. If this problem appears again, please report an error to the developers.
//details
E:The package dbconfig-common needs to be reinstalled, but I can't find an archive for it.


any suggestions welcome, thank you.

ps

I have tried downloading the dpkg-1.17.5ubuntu5.4  to put in usr/bin - but it won't let me (via GUI)

---

### Post by ian-weisser on 2015-07-07
dpkg is fine, Don't try to replace it or haywire around it. Listen to dpkg - it's trying to tell you something.

> **Roibeard said:**
> 
dpkg: error processing package dbconfig-common (--configure):
 [B]package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration[/B]
Errors were encountered while processing:
 dbconfig-common

Have you tried reinstalling dbconfig-common?
If so, please show us that session, with all the error messages intact and in context.
If you need help reinstalling the package, just say so and we are happy to walk you through it.


> **Roibeard said:**
> E:The package dbconfig-common needs to be reinstalled, but I can't find an archive for it.

Since the package is in main, and since you obviously downloaded it at least once before, this may be a connectivity or mirror issue. Keep an eye on it, and let us know if it recurs.

---

