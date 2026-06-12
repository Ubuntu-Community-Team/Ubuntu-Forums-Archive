---
title: "[SOLVED] Package still broken?"
date: 2007-06-06
forum: General Help
---

### Post by DougieFresh4U on 2007-06-06
Have I missed some thing, or is the following package still broken?
 [B]dougie@DougiesToyBox:~$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  linux-backports-modules-generic 
The following packages will be upgraded:
  language-pack-en language-pack-gnome-en 
3 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 834kB of archives. After unpacking 3690kB will be used.
The following packages have unmet dependencies:
  linux-backports-modules-generic: Depends: linux-backports-modules-2.6.20-16-generic which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
linux-backports-modules-generic [2.6.20.15.14 (feisty, now)]

Score is 0

Accept this solution? [Y/n/q/?] 
[/B]

---

### Post by zvacet on 2007-06-06
```
sudo aptitude install  linux-backports-modules-2.6.20-16-generic
```

or you can go to the s**ynaptic<edit<fix broken packages**

---

### Post by DougieFresh4U on 2007-06-07
> **zvacet said:**
> ```
sudo aptitude install  linux-backports-modules-2.6.20-16-generic
```

or you can go to the s**ynaptic<edit<fix broken packages**



dougie@DougiesToyBox:~$ sudo aptitude install  linux-backports-modules-2.6.20-16-generic
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No candidate version found for linux-backports-modules-2.6.20-16-generic
The following packages have been kept back:
  linux-backports-modules-generic 
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
dougie@DougiesToyBox:~$

---

