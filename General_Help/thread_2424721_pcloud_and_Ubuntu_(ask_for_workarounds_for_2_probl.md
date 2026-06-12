---
title: "pcloud and Ubuntu (ask for workarounds for 2 problems)"
date: 2019-08-13
forum: General Help
---

### Post by rwigle on 2019-08-13
I am test driving pcloud and have come up with a few problems. I wonder if there are work arounds.

[LIST=1]
[*]shell programs don't run from folders in the pCloudDrive folder So "./spill.sh" won't work though "bash spill.sh" will.
[*]no soft links allowed in the pCloudDrive folder
[*]
[/LIST]

I think I can work around the first problem but the second is really problematic for me. I hope someone has a workaround. pCloudDrive is mounted as FUSE about which I know nothing.

---

### Post by TheFu on 2019-08-13
I know ZERO about pcloud.

Not all file systems support symbolic linking.  Open a bug with the project and see what they say about it.

---

