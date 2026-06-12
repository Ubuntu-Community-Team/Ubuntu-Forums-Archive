---
title: "Mounting wikipediafs"
date: 2008-01-31
forum: General Help
---

### Post by tickingaway on 2008-01-31
I installed fuse, the python-fuse bindings, and wikipediafs today.  When I try "mount.wikipediafs /mnt/wikipedia"  I get the following python errors.

 File "/usr/bin/mount.wikipediafs", line 68, in <module>
    import wikipediafs.WikipediaFS
  File "/usr/lib/python2.5/site-packages/wikipediafs/WikipediaFS.py", line 21, in <module>
    from wikipediafs.WikipediaArticle import WikipediaArticle
  File "/usr/lib/python2.5/site-packages/wikipediafs/WikipediaArticle.py", line 23, in <module>
    from wikipediafs.logger import logger
ImportError: cannot import name logger

Has anyone else experienced this problem?

---

