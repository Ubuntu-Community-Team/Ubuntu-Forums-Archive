---
title: "which repository did the package come from?"
date: 2019-12-14
forum: General Help
---

### Post by Skaperen on 2019-12-14
i have a package that is already installed.  is there a way to find which repository it came from, even if it is no longer there and even if it now comes from a different repository?  is this possible for packages not currently installed?

---

### Post by 0x656b694d on 2019-12-17
i'd say no. One could go through all known (suspected) repos to check if there's such a package with the exact version there and make a guess. Same for not installed packages.

---

### Post by yetimon_64 on 2019-12-18
With Synaptic Package Manager and the quick filter and using the origin selection it can be pretty easy to find the repository a package comes from. 

Even quicker/easier is to use the command "apt-cache show <package-name>" in terminal and the repository that supplies it is listed under "Section".

Both methods mentioned above will show the repository holding a package whether or not it is installed. I don't fully understand what you mean by "even if it is no longer there and even if it now comes from a different repository" but if a package is in any repository that is enabled in the users installation, irrespective of whether it is installed or not, it is pretty easy to find the repository it is from.

**Edit:** if the package is from a repo that is not enabled in the users installation it may be a bit trickier and require a bit of research on google. I've often used google with a package name with the distro/release details related to it to find the source repo with ubuntu packages.

---

