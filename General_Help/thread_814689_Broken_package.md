---
title: "Broken package"
date: 2008-05-31
forum: General Help
---

### Post by personal-data-removed on 2008-05-31
I cant remove linux-ubuntu-modules-2.6.24-12.generic

It gives the following error:
E: linux-ubuntu-modules-2.6.24-12-generic: subprocess post-removal script returns status error exit 1

---

### Post by Prospero2006 on 2008-05-31
Look for the problematic package here

/var/lib/dpkg/status

(That's a text file.)

You can remove the problematic entry there and the error will go away, but be very careful with that file. Back it up first!

---

### Post by personal-data-removed on 2008-06-01
Thanks for the help, but i didnt found the package at /var/lib/dpkg/status.

---

