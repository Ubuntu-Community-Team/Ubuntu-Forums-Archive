---
title: "Can't uninstall serpentine - ubuntu-desktop package broken?"
date: 2007-03-01
forum: General Help
---

### Post by kngcrntrd on 2007-03-01
I am running Edgy Eft on a Dell Inspiron 1150 laptop.  I recently installed the cd burning tool serpentine.  Now I want to uninstall.  When using aptitude, I get:

```
master@master:~$ sudo aptitude remove serpentine
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  ubuntu-desktop 
The following packages will be REMOVED:
  serpentine 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 684kB will be freed.
The following packages have unmet dependencies:
  ubuntu-desktop: Depends: serpentine but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
ubuntu-desktop

Score is -301

Accept this solution? [Y/n/q/?] 
```

I have tried updating and upgrading.  I have tried reinstalling ubuntu-desktop.  I have done:  ```
 sudo aptitude -f install 
```  I have also done all this with apt-get.  It's not extremely important that I am able to remove serpentine, but I figured that a broken ubuntu-desktop is a problem.  Any ideas?

---

