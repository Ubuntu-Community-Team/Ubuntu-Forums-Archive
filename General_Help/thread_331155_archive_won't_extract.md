---
title: "archive won't extract"
date: 2007-01-04
forum: General Help
---

### Post by sdd231163 on 2007-01-04
Recently I tried compiling the latest freedroid rpg on ubuntu edgy but it wouldn't work b ecause when I tried extracting the .bz2 arhive (using ark or bunzip) the install-sh script couldn't be used by ./configure be cause only the record was there - the file was 0B in size compared with 9B (or KB i can't remember) in my fedora installation. Thus under fedora the compilation worked but under ubuntu it did't

---

### Post by bonzodog on 2007-01-04
have you tried re-downloading the archive? Also, when you next try it, use 

```
$tar -xvjf freedroid.tar.bz2
```

---

### Post by sdd231163 on 2007-01-04
turns out it needed automake 1.9 and version 1.4 is only the latest version.
the file was only a link.

---

