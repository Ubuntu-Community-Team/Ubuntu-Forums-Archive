---
title: "what causes the error E: Encountered a section with no Package: header?"
date: 2018-07-21
forum: General Help
---

### Post by ardouronerous on 2018-07-21
Error:

```
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
```

I have encountered this problem multiple times since I started using Linux, starting with Xubuntu 12.04 and now on Lubuntu 16.04.

The problem is easily solved by using these Terminal commands:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

But why does this happen in the first place? Is there no way to prevent this at all? Thanks.

---

