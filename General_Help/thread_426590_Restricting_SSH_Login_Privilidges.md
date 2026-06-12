---
title: "Restricting SSH Login Privilidges"
date: 2007-04-28
forum: General Help
---

### Post by Orbit45244 on 2007-04-28
I am trying to set up my Subversion Repository to use SSH encryption. The problem is I don't trust some of my co-workers with the power to login to my machine via ssh. I was wondering if there was a way to allow my co-workers to use svn+ssh without giving them SSH login access. I have tried changing the shells of the co-worker's user accounts to /usr/sbin/nologin and /bin/true and they just cause subversion to stop working.

EDIT:
I'm using Ubuntu 7.04 by the way.

---

