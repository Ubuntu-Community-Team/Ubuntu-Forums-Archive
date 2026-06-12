---
title: "Unable to run mozilla"
date: 2008-03-11
forum: General Help
---

### Post by jackmcslay on 2008-03-11
I'm trying to install archived versions of mozilla from [http://www.mozilla.org/releases/](http://www.mozilla.org/releases/) but if I run either the installer or the unpackaged software from the tar.gz, I get the following error

```
 error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
```

even if libgtk1.2 is properly installed. I've tried reinstalling it, but nothing changes.

What could be the problem? I'm running Ubuntu 7.10 x64 on an athlon 64 3200+ pc

---

### Post by bharadwaj on 2008-03-11
First install libgtk1.2 or later from synaptic package manager. Then check if any other dependencies are required.

---

### Post by jackmcslay on 2008-03-11
it's already properly installed, as already mentioned

---

