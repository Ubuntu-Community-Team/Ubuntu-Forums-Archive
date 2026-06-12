---
title: "&quot;Hash Sum mismatch&quot; errors from apt-get when using apt-cacher-ng"
date: 2013-04-17
forum: General Help
---

### Post by tk83 on 2013-04-17
I'm using apt-cacher-ng to cache any packages I install using apt-get. For some reason a few days ago I started getting Hash Sum Mismatch errors whenever I did apt-get update, but these only ever affected the Virtualbox repo, none of the others:
```
W: Failed to fetch copy:/var/lib/apt/lists/partial/download.virtualbox.org_virtualbox_debian_dists_precise_contrib_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch copy:/var/lib/apt/lists/partial/download.virtualbox.org_virtualbox_debian_dists_precise_contrib_binary-i386_Packages  Hash Sum mismatch
```

The fix I eventually found was:
# Delete all Release, Release.gz, Package, Package.gz, Package.bz2 etc. files in /var/lib/cache/apt-cacher-ng/download.virtualbox.org/
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
# repeat the above steps a few times if necessary

Hope it helps

---

### Post by FrankT-Qc on 2013-06-25
I have the same problem.

The fix works for me too. Put this in a cron job so my users leave me alone...

Anyone has a cleaner fix ?

---

