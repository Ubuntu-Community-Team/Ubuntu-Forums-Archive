---
title: "Package not available (openssh-server)"
date: 2006-12-09
forum: General Help
---

### Post by purebad on 2006-12-09
I have a fresh install of edgy on a desktop and I wanted to enable ssh, so per numerous threads, I tried: sudo apt-get install openssh-server I get the response:

Package openssh-server is not available, but is referred to by another package. This may mean the package is missing, has been obsoleted, or is only avaiable from another source
E: Package openssh-server has no installation candidate 

do I need to change something with my repositories?

---

### Post by Azakus on 2006-12-10
Yes. You need to enable some of the multiverse and universe repos (not on by default in a fresh install). Just remove the "#" sign in front of the repos that have multiverse and/or universe in them in your sources.list file.

---

