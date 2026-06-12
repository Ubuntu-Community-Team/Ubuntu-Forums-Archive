---
title: "&quot;Internal error&quot; every time I boot Ubuntu 14.04?"
date: 2015-01-20
forum: General Help
---

### Post by Nathan_McAuley on 2015-01-20
Hi, 

I get the following error every time I start my computer. I'm new to Linux so I'm not entirely sure what it means. Can anyone shed some light on this or point me in the direction of a fix? 

ExecutablePath
/usr/lib/gvfs/gvfsd-cdda
Package
gvfs-backends 1.20.1-1ubuntu1
ProblemType
Crash
Title
gvfsd-cdda crashed with SIGSEGV in _IO_vfprintf_internal()

etc etc

Any ideas? I have already run apt-get update and apt-get upgrade but it's still happening.

---

### Post by sandyd on 2015-01-20
Possibly related to [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1204632](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1204632)

---

