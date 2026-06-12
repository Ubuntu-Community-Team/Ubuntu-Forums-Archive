---
title: "How can I fix apt-get?"
date: 2007-09-28
forum: General Help
---

### Post by Game_boy on 2007-09-28
I downloaded and installed a corrupt .deb called pdfedit accidentally.

It failed to install correctly and now apt-get/Synaptic is broken because when I want to use apt-get in any way it says it can't reinstall pdfedit because it can't find the archive and then crashes the whole process, and when I want to remove pdfedit it says I need to reinstall it first.

BBBBBBB@BBBBBBB-desktop:~$ sudo apt-get install pdfedit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package pdfedit needs to be reinstalled, but I can't find an archive for it.

BBBBBBB@BBBBBBB-desktop:~$ sudo aptitude remove pdfedit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Building tag database... Done      
The following packages will be REMOVED:
  pdfedit 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
dpkg: error processing pdfedit (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 pdfedit
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

What should I do? It's like a catch-22.

---

### Post by Seisen on 2007-09-28
Do this in the terminal

```
cd /usr/bin/dpkg
ls | less
```

look for that package and then when you find it type this in the terminal

```
sudo rm packagename
``` let me know if that fixes the problem.

---

