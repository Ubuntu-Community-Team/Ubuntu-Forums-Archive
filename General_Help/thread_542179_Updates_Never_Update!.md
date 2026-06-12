---
title: "Updates Never Update!"
date: 2007-09-03
forum: General Help
---

### Post by InGunsWeTrust on 2007-09-03
I have the update manager up in the corner telling me there is one update. If I view the updates it shows the compiz-core needs to be updated. If I install the updates there are no error messages but compiz-core still needs to be updated. If I click the check button sure enough it is still there. If I use synaptic or apt-get install it looks successful but then it just wants to be updates still!

Here is terminal output

```
ty@ty-laptop:~$ sudo apt-get install compiz-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  compiz-core
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/197kB of archives.
After unpacking 0B of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  compiz-core
Install these packages without verification [y/N]? y
(Reading database ... 137591 files and directories currently installed.)
Preparing to replace compiz-core 1:0.5.2-0ubuntu3~ppa4 (using .../compiz-core_1%3a0.5.2-0ubuntu3~ppa4_amd64.deb) ...
Unpacking replacement compiz-core ...
Setting up compiz-core (0.5.2-0ubuntu3~ppa4) ...
ty@ty-laptop:~$ 

```

---

