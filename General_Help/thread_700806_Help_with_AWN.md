---
title: "Help with AWN"
date: 2008-02-18
forum: General Help
---

### Post by Muscar on 2008-02-18
Well, i installed the AWN packages from SPM and i got this error:
E: /var/cache/apt/archives/libawn0_0.2.1-0ubuntu1~gutsy1_i386.deb: trying to overwrite `/usr/lib/libawn.so.0.0.1', which is also in package libawn-bzr

:confused:

---

### Post by RumorsOfWar on 2008-02-18
Awn looks like it will be cool, but its a bit cutting edge for Ubuntu. That deb file seems to have been compiled with more cutting-edge libraries, and probably for a more up to date kernel. 
It *may* be safe to overwrite libawn.so.0.0.1 , and install, But if you tried to install something else that needed it you'd be screwed. 
I would look for an older version of Awn.

---

