---
title: "Can't Install Ubuntu 7.10 in wubi"
date: 2008-03-09
forum: General Help
---

### Post by jakey123 on 2008-03-09
:lolflag: I can not install ubuntu 7.10 in wubi i downloaded wubi and an ubuntu 7.10 iso but when i lanuch wubi it starts down loading the7.04 iso how can i fix this:lolflag:  :confused:

---

### Post by Rocket2DMn on 2008-03-09
Wubi is not an officially supported method of installing.  From what I understand, it doesn't setup a real install as we know it, but rather writes to a file rather than setting up a linux and swap partition.  If you're serious about installing, we recommend burning the 7.10 iso file to a cd-r as an image, then installing the normal way.
You can find some details on that here: [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
Since you are running windows, you will need to resize your windows partition to make room for Ubuntu, so if you decide to install, you will first need to defragment your windows drive before you resize the windows partition from the LiveCD during the install process.

As always, make sure you have all of your important stuff backed up before you start fiddling with partitions or installing anything.

---

### Post by twright on 2008-03-09
just burn the .iso to cd and wubi.exe is included on it

it may or may not be supported but it sure is convenient :)

---

