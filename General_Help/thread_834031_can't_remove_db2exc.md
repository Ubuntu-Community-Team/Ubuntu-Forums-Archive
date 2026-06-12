---
title: "can't remove db2exc"
date: 2008-06-19
forum: General Help
---

### Post by aljosa on 2008-06-19
i've found on some blog that i can normally install db2exc in hardy if i add gutsy partner repository. now i want to remove it and when i try to remove it i get "Package is in a very bad inconsistent state" so i try to reinstall it and i get this:

# apt-get install --reinstall db2exc
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/214MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]?
(Reading database ... 200551 files and directories currently installed.)
Preparing to replace db2exc 9.5.0-1gutsy1 (using .../db2exc_9.5.0-1gutsy1_i386.deb) ...
Unpacking replacement db2exc ...
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
dpkg: error processing /var/cache/apt/archives/db2exc_9.5.0-1gutsy1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/db2exc_9.5.0-1gutsy1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


any idea how to fix this?

Aljosa

---

### Post by cariboo on 2008-06-21
Have you tried to use Synaptic's broken package function.

Jum

---

### Post by aljosa on 2008-06-23
yes, still broken. how can i force removal of db2exc?

---

### Post by wirah on 2008-07-07
I got this same problem. goto /var/apt/cache/packages, crack the db2exc package open, remove some stuff from the prerm script, try again, and repeat until it works.

It's a pain, i've filed a bug already.

Ant

---

