---
title: "Problems installing programs due to missing ppa files"
date: 2018-01-19
forum: General Help
---

### Post by eprevodilac on 2018-01-19
Hello all, 

I'm trying to install tails-installer on my Ubuntu Gnome 17.04 install, however I keep getting errors when trying to install the "additional packages" apt-get automatically downloads alongside it.

Here is the output of 'sudo apt-get install tails-installer':
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  p7zip p7zip-full python-configobj python-urlgrabber
Suggested packages:
  p7zip-rar python-configobj-doc
The following NEW packages will be installed:
  p7zip p7zip-full python-configobj python-urlgrabber tails-installer
0 upgraded, 5 newly installed, 0 to remove and 43 not upgraded.
Need to get 1,461 kB/1,697 kB of archives.
After this operation, 6,787 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Err:1 http://us.archive.ubuntu.com/ubuntu zesty/universe amd64 p7zip amd64 16.02+dfsg-2
  404  Not Found [IP: 91.189.91.23 80]
Err:2 http://us.archive.ubuntu.com/ubuntu zesty/universe amd64 p7zip-full amd64 16.02+dfsg-2
  404  Not Found [IP: 91.189.91.23 80]
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/p/p7zip/p7zip_16.02+dfsg-2_amd64.deb  404  Not Found [IP: 91.189.91.23 80]
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/p/p7zip/p7zip-full_16.02+dfsg-2_amd64.deb  404  Not Found [IP: 91.189.91.23 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

Interestingly enough, when I tried the same install using the i3 window manager I got a different error, one concerning missing Release files for the default zesty repositories.

---

### Post by DuckHook on 2018-01-20
Welcome to the forums, eprevodilac.

Zesty is out of support and its repos have been retired. The error you are getting is because *apt* cannot find the repos. You need to either:
[LIST=1]
[*]Upgrade to Artful, which is good to July of this year, or
[*]Install Xenial which is a LTS and good until 2021.
[/LIST]
Instructions for End-of-Life upgrades: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

