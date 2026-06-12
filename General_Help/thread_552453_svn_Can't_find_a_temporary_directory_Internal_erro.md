---
title: "svn: Can't find a temporary directory: Internal error"
date: 2007-09-16
forum: General Help
---

### Post by earobinson on 2007-09-16
I have a svn repository that for some reason I cant access. I keep getting this error "svn: Can't find a temporary directory: Internal error"
```
earobinson@minusone:/media/data$ svn up
svn: Can't find a temporary directory: Internal error
earobinson@minusone:/media/data$ svn info
Path: .
URL: svn+ssh://earobinson@192.168.1.109/media/data/svn/data
Repository Root: svn+ssh://earobinson@192.168.1.109/media/data/svn/data
Repository UUID: 5d7d7bd3-862b-0410-9974-d22d6bbdcf2f
Revision: 1885
Node Kind: directory
Schedule: normal
Last Changed Author: earobinson
Last Changed Rev: 1885
Last Changed Date: 2007-09-15 17:06:08 -0400 (Sat, 15 Sep 2007)
```
It works on the computer the repo is hosted on.

Any help would be great ... Thanks

Edit: ```
svn co svn+ssh://earobinson@192.168.1.109/media/data/svn/data
```

---

### Post by earobinson on 2007-09-16
Fixed, the server computer had run out of space!

---

