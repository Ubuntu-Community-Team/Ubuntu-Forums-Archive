---
title: "problem of crash in package"
date: 2014-08-10
forum: General Help
---

### Post by ThethundarBird on 2014-08-10
E: Encountered a section with no Package: headerE: Problem with MergeList /var/lib/apt/lists/eg.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

how to solve that i cant update nor open synaptic nothing at all

---

### Post by ajgreeny on 2014-08-10
Run command ```
sudo rm /var/lib/apt/lists/*
``` then update again with  ```
sudo apt-get update
```.

---

