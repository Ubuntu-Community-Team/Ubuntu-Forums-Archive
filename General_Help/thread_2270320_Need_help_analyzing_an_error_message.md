---
title: "Need help analyzing an error message"
date: 2015-03-22
forum: General Help
---

### Post by bobnutfield on 2015-03-22
Hello Everyone

I am runnning 14.04 and have a laptop with 160gb drive.  I want to free up the partitions that have other old distributions on them and use the entire disk for 14.04.  I know how to use gpartd to do this, but I did a sudo apt-get clean frist and got this:

no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory

What's going on?  Is my disk OK?  This is an old laptop I have been using for years, but I like it and it runs 14.04 just fine.

Any help appreciated.

Bob

---

### Post by Yellow Pasque on 2015-03-22
[http://ubuntuforums.org/showthread.php?t=2214042](http://ubuntuforums.org/showthread.php?t=2214042)
In particular, post #8 if you don't use samba (or post #9 if you do).

---

### Post by bobnutfield on 2015-03-22
Thank you very much, that fixed it.  I can with reclaiming the partitions now.

Bob

---

