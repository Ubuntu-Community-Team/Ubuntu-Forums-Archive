---
title: "synaptic package manager not opening"
date: 2013-03-12
forum: General Help
---

### Post by dakshesh10 on 2013-03-12
Hello, I am new to Ubuntu and I am getting an error while opening the Synaptic package Manager. 
And the error is as follows:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

please help....!! :confused::confused:

---

### Post by schragge on 2013-03-12
Open a terminal (**Ctrl**+**Alt**+**t**), and run
```
sudo rm /var/lib/apt/lists/*
sudo apt-get update
```

---

