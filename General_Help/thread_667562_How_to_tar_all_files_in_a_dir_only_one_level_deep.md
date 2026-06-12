---
title: "How to tar all files in a dir only one level deep?"
date: 2008-01-14
forum: General Help
---

### Post by isync on 2008-01-14
Hi!

I have the following dir layout

mydir/
_____dira/
________subdir1
________subdir2
________subdir3
_____dirb/
________subdir1
________subdir2
________subdir3
_____dirc/
________subdir1
________subdir2
________subdir3

Is there a way to include all first-level subdirs into my tar (dira,dirb,dirc) while excluding sub-sub dirs (subdir1,subdir2,subdir3). Something like a dive-only-this-deep option??

---

### Post by capink on 2008-01-14
```
find /path/to/my/dir -maxdepth 2 -type f -exec tar rvpf /path/to/tar/archive {} \;
```

---

