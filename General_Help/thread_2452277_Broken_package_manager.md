---
title: "Broken package manager"
date: 2020-10-19
forum: General Help
---

### Post by jamesoreilly on 2020-10-19
Hello,

I'm running ubuntu 18.04. When I run sudo apt-get update, I get the error given below.

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/developer.download.nvidia.com_compute_cuda_repos_ubuntu1804_x86%5f64_Packages
E: The package lists or status file could not be parsed or opened.

I've scoured all the forums and they invariably say to remove package lists and then update:

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

I've tried to remove the problematic file myself.
However the error persists. I can't update or uninstall any packages. Any help is appreciated.

---

### Post by Bashing-om on 2020-10-19
jamesoreilly - Hello

Try it like:
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt update
sudo apt upgrade

```

> 
MergeLists are a working tool of apt, part of the way it keeps track of which packages are in which repositories. It's the gears of a text-based database that apt relies upon. When corrupted, they can be safely deleted. Apt will recreate them during the next apt update.


[INDENT]maybe now Yes
[/INDENT]

---

