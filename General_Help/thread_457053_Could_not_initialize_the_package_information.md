---
title: "Could not initialize the package information"
date: 2007-05-28
forum: General Help
---

### Post by rkrizan on 2007-05-28
A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'W:Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_feisty_multiverse_binary-i386_Packages), W:Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages), W:Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_feisty-updates_multiverse_binary-i386_Packages), W:Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_feisty-updates_universe_binary-i386_Packages), E:Problem parsing dependency Depends, E:Error occurred while processing thekompany-support (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/www.getautomatix.com_apt_dists_feisty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'


How can I fix this?

---

### Post by Mechanical on 2007-05-28
I woke up with the same problem.  I guess its automatix but I haven't seen a solution yet.

---

### Post by arnieboy on 2007-05-28
The erring package has long been fixed and a simple

```
sudo apt-get update
```

will fix this issue

---

