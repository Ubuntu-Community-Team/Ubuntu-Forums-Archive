---
title: "Can't install pango on ubuntu"
date: 2015-07-17
forum: General Help
---

### Post by Shwick2 on 2015-07-17
I'm trying to build gtk+1.3 on ubuntu and I'm getting an error during configure,

ld: cannot find -lpango

I tried installing a ton of pango libraries and its still not installed so I'm not sure what to do. I keep testing it with

ld -lpango

But get the same error. Has anyone successfully installed a pre-built pango on ubuntu? From any repos? Pango website says its difficult to build and I'd like to use a prebuilt binary if possible.

Also I had an error with atk not being found but all I had to do was install libatk1.0* and that was fixed.

---

### Post by monkeybrain20122 on 2015-07-17
Did you install libpango1.0-dev ?

---

### Post by Shwick2 on 2015-07-17
libpango1.0-dev is already the newest version
yep.  I think I did libpango1.0*, I did the graphite one, and I did another package that was supposed to contain pango, some grl one.

---

