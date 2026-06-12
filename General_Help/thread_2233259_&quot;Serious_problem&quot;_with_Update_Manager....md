---
title: "&quot;Serious problem&quot; with Update Manager..."
date: 2014-07-07
forum: General Help
---

### Post by t0p on 2014-07-07
Tried to run Update Manager and got this message:

> 
Could not initialise the package information


An unresolvable problem occurred while initialising the package information.


Please report this bug for the 'update-manager' package and try to include the following error message:


'E:Encountered a section with no Package: header, E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'

Using Ubuntu 12.04. I don't think I've done anything recently that could have caused this.  Is it just me, or is there a repo issue?

---

### Post by ubudog on 2014-07-07
Try this:

```
sudo rm /var/lib/apt/lists/*
```
```
sudo apt-get update
```

---

### Post by t0p on 2014-07-08
Thanks ubudog that did the trick.

---

### Post by ubudog on 2014-07-08
Sweet.  :guitar:

---

