---
title: "New file default mask"
date: 2008-02-29
forum: General Help
---

### Post by chocolatetoothpaste on 2008-02-29
Hello all,
  I am running a development server at my work for websites.  The problem is, when  user uploads a new file, the default mask is rw+r+r.  I want the new file to have group permissions set to write though.  Is there a way I can make that the default for new files?

---

### Post by pointone on 2008-02-29
/etc/profile

Change umask 022 to 002 for rw-rw-r--.

---

