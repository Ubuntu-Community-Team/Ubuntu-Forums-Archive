---
title: "slickedit 11 in ubuntu"
date: 2006-11-14
forum: General Help
---

### Post by xcity on 2006-11-14
Do any one has similar problem in slickedit 11 under ubuntu? Using default installation, and even configuration is in default. 

I experienced random crash, it happen with no precondition. When you open a menu, or click a tab, it just freeze. You even can not close slickedit, or switch to any other program until you kill this slickedit.

It only happen in version 11, all the previous version is just fine.

---

### Post by genbell on 2007-05-10
I have a similar problem. When I open files from a NFS mounted filesystem it freezes. No problems with local files.

---

### Post by ypereto on 2008-06-27
I also had a similar problem.
Slickedit would randomly stall for several seconds (10ish).
I fixed this by moving my workspace and project files to a local directory but keeping my source files on the nfs mount.

I believe slickedit was trying to acquire a lock on the workspace file, but nfs was slow to grant this lock.

You can confirm this by using strace and seeing what slickedit is doing during these stalls.
(strace /opt/slickedit/bin/vs 2>&1) | grep fcntl

---

