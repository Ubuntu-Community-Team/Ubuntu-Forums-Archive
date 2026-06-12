---
title: "Package kept back"
date: 2020-11-30
forum: General Help
---

### Post by ordak on 2020-11-30
I try to update and then upgrade this PC. I get:

```
21 packages can be upgraded. Run 'apt list --upgradable' to see them.
```

now:
```

:~$ sudo apt upgrade

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  nvidia-dkms-435
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

Why the 21 packages are not upgraded ?

What to do with kept back package ?

---

### Post by deadflowr on 2020-11-30
Your output only shows one package to be held back and nothing to upgrade.
Try an apt full-upgrade as it has more function over just apt upgrade.

(apt upgrade will install new packages and updates, but it will not remove packages if the update requires it.
apt full-upgrade will remove packages if an update requires it)

---

### Post by ActionParsnip on 2020-11-30
If a package is ready but depends on a package version that is not yet in the repositories then it will be kept back. Once the dependency is met then the package will install. This is by design and makes total sense.

---

