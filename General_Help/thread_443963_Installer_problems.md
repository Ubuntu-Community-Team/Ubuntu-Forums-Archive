---
title: "Installer problems"
date: 2007-05-14
forum: General Help
---

### Post by AWerner32 on 2007-05-14
whenever i try to run an installer of any type be it synaptic automatix or system update i am greeted with a lovely error . this is the one from synaptic

E: Dynamic MMap ran out of room
E: Error occurred while processing xfonts-cronyx-isocyr-misc (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_universe_bi nary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

---

### Post by compiledkernel on 2007-05-15
Hmmmmm....Memory Cache thingy. 

Try this. 

Add the following line to either /etc/apt/apt.conf

```

APT::Cache-Limit "8388608";
```

---

