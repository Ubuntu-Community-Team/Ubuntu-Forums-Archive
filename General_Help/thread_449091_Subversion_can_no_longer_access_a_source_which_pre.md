---
title: "Subversion can no longer access a source which previously had a permission-denied"
date: 2007-05-19
forum: General Help
---

### Post by franzsee on 2007-05-19
Good day,

Environment
* Kubuntu Fiesty Fawn
* Subversion 1.4.3

Steps to reproduce.
1. go to a source you have checked out with subversion.
2. use "svn update" on that source
* you will get an error message stating that you do not have permissions to do so
3. use "sudo svn update" on that same source [ and enter your password ]

Expected Result:
* The source will be updated.

Actual Result:
* Skipped '.'

Note that if you remove step#2, there would be problem whatsoever. But if a permission fails on a source, it seems that I can no longer access it via svn.

Any ideas?

Thanks,
Franz

---

