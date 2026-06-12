---
title: "Can't remove KDM"
date: 2007-07-26
forum: General Help
---

### Post by x1a4 on 2007-07-26
Hi, 

I can't remove KDM.  I get the following errors: 

dpkg: error processing kdm (--purge):
 subprocess pre-removal script returned error exit status 1
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 kdm
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Exit 255

How do I get rid of KDM?  Thank  you.

---

### Post by x1a4 on 2007-07-28
My bad.  I changed /bin/sh to point to ZSH, I now changed it back to DASH and it works.

---

