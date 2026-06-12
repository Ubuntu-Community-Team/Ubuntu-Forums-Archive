---
title: "looking for a script to rename series S01E01.mkv to xx.S01E01.mkv"
date: 2017-10-21
forum: General Help
---

### Post by wagner.f on 2017-10-21
Hello there all, 
Who can help me out? ;)
Looking for a script that can rename multiple media files in a folder like S01E01.mkv 12 episodes
Back to example Black.Sails S01E01.mkv 
                         Black.Sails S01E2.mkv etcetra...
through terminal headless server..
Thank you :D

---

### Post by TheFu on 2017-10-22
I use 'rename' for this.
```
$ rename 's/S01E/S01E0/g' *mkv
```
of course, that will probably rename E10-E99 in ways you don't want, so be more restrictive on the filename pattern (globbbing) to limit which files are actually renamed.

---

