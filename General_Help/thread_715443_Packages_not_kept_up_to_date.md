---
title: "Packages not kept up to date?"
date: 2008-03-04
forum: General Help
---

### Post by KernelKing on 2008-03-04
I'm looking to install memcached on Gutsy. The latest package is 1.2.1-1 for Gutsy (and 1.2.2-1 for Hardy).  The most recent tar ball is 1.2.5.  The packages are lagging by months.

What do you do?  Install the package or the tarball?  Thanks for your input.

---

### Post by taurus on 2008-03-04
If you don't have any problems with the older version, stick with it.  If you need some features in the new version, then remove the old one and install the new one by hand.  Instead of running "sudo make install" to install it on the last step, just run "sudo checkinstall".

---

### Post by KernelKing on 2008-03-04
Thanks much!  I ddin't know about checkinstall.  Very useful!:)

---

