---
title: "Damaged package unremovable with apt-get"
date: 2007-03-11
forum: General Help
---

### Post by erdalronahi on 2007-03-11
I had some errors on the disk which were fixed by fsck. But now the abiword-plugins package is damaged and blocks all apt-get actions. If I try to remove it with

```

sudo apt-get remove abiword-plugin

```

I get the following result:
```

files list file for package `abiword-plugins' is missing final newline

```

and no action is possible, not even updates of other packages. What can I do to repair the system?

---

### Post by erdalronahi on 2007-03-11
I found the answer in another thread. 

#9 in [http://ubuntuforums.org/showthread.php?t=12737](http://ubuntuforums.org/showthread.php?t=12737) has the solution, step 1 and 4 are enough. The key is to remove the package information from /var/lib/dpkg/status.

---

