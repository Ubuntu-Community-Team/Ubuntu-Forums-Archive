---
title: "Installing svn2bzr"
date: 2007-08-15
forum: General Help
---

### Post by igb on 2007-08-15
I am hoping to migrate my VCS system from svn to bzr. I need to convert some of my svn repositories to bzr. I have checked out David Allouche's svn2bzr, built and installed it. However, whenever I run it e.g. svn2bzr --help I get:

Segmentation fault (core dumped)

I am running Feisty. Any clues as to how to proceed and get it working?

Ian.

---

### Post by jelmer on 2008-03-01
Hi Ian,

svn2bzr is no longer maintained these days. If you install the bzr-svn package you should be able to use the "svn-import" command to convert your repository.

Cheers,

Jelmer

---

### Post by igb on 2008-03-01
Thanks for that.

Ian.

---

