---
title: "packet writing / udftools seems to be broken"
date: 2006-08-27
forum: General Help
---

### Post by kornelix on 2006-08-27
I tried two approaches: following instructions found in fedora, and following instructions found in ubuntu forums, "packet writing without tears" (I tried these after failing to find any user instructions within the udftools package).

The ubuntu how-to did not get to first base. The cdrwtool command to initialize the media with a udf file system exited with an error:
```
# cdrwtool -d /dev/hdb -q
command failed: a1 01 00 00 ... - sense 00.30.00
blank disk: Illegal seek

``` 
I then tried following the man page for mkudffs, which failed with a seqmentation fault.

The fedora how-to actually wrote some files on a DVD-RW, but afterwards the system went into a funny loop, spinning the drive up and down, up and down... I could not unmount or eject, even as root user, so I had to crash the system to get my DVD drive back. 

I think this package is purely experimental and should be removed, or users should be warned not to waste their time with it.

If someone has a better recipe, I would love to try it.

---

