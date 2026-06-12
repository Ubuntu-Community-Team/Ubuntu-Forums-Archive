---
title: "why ln -sv /mnt/lfs/tools / creates /tools symlink"
date: 2015-04-01
forum: General Help
---

### Post by rail.shafigulin on 2015-04-01
I can't figure out why the following command creates a /tools symlink

ln -sv /mnt/lfs/tools / 

If I read the manual correctly the symlink should be  /  and not /tools. So why is /tools created. Can anyone explain this?

Any help is appreciated.

---

### Post by bardo2 on 2015-04-03
there seems to be some misunderstanding, both: what ln does, and: its syntax.
from man ln i get this
```
NAME
       ln - make links between files

SYNOPSIS
       ln [OPTION]... [-T] TARGET LINK_NAME   (1st form)
       ln [OPTION]... TARGET                  (2nd form)
       ln [OPTION]... TARGET... DIRECTORY     (3rd form)
       ln [OPTION]... -t DIRECTORY TARGET...  (4th form)


```
So you are using 3rd form (not first)!

Anyway: if that were possible, it would create an endless nested structure (recursive), right?
i dont understand, in which way this would make sense. And if it would, i would consider bind mount instead.

---

