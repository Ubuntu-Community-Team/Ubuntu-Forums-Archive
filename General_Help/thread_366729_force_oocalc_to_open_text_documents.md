---
title: "force oocalc to open text documents"
date: 2007-02-21
forum: General Help
---

### Post by der_vegi on 2007-02-21
hi!

i've got some data from a measurement which is a text file but i want to open it in openoffice (2.0.4, im running edgy) calc because sometimes - if you're lucky - the data is then already arranged in columns.

under ms windows - which i don't have anymore - it is still possible to open plain text documents with oocalc, but in the linux-version the file is automatically opened in oowriter.

any ideas how you can force oocalc to open the text file? tanks!

---

### Post by ruru on 2007-11-11
You've probably solved this by now - but, just in case, my solution is to 'open with' the custom command:
```
oocalc -calc -o %f
```
which will open oocalc in import mode.

---

