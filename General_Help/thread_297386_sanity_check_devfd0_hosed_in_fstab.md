---
title: "sanity check: /dev/fd0 hosed in fstab?"
date: 2006-11-11
forum: General Help
---

### Post by tonyr on 2006-11-11
The default entry in /etc/fstab for the floppy in my Edgy installation
is missing the **fd0** part.  It looks like this:
```
/dev/        /media/floppy0  auto    rw,user,noauto  0      0

```
That's not a typo on my part. The **fd0** is really not there.  I checked
on both Kubuntu and Ubuntu, and it's the same both places.

Now I know that floppy drives are not used very much anymore, and I seem
to recall some floppy support being dropped somewhere (boot floppy creation
in kernel build?), and my installations are from Edgy Knot3 followed by
dist-upgrades, and I know how to fix the fstab entry.  

Is the floppy entry hosed in the final release, too?   Has anybody else
seen this?  I looked for a bug report at Malone, but didn't see anything
related, and I haven't found any other direct reference to this in the
forums.  I'm kind of assuming that this was a hiccup in the Knot series
and got fixed before final release.

---

