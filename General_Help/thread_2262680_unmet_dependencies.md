---
title: "unmet dependencies"
date: 2015-01-26
forum: General Help
---

### Post by samuel23 on 2015-01-26
Hello. I am having trouble installing updates that the synaptic package manager finds. It says 'fix broken packages first'. I am running an ubuntu 12.04, do not have the installation disk. Also, after checking for updates, The package manager says "An error occured. Please run package manager from the right click menu to see what's wrong. The error message was'Error: Broken Count >0 '. "Any information that is needed I can provide, also on a side note, I am a newer user. Thank you):P

---

### Post by Impavidus on 2015-01-26
Let's find out what the problem is. Open a terminal and execute these two commands:```
sudo apt-get update
sudo apt-get upgrade
```We could use the GUI, but command line stuff is easier to explain over the web.

---

### Post by samuel23 on 2015-01-26
The command sudo apt-get update worked fine, but when i typed in  sudo apt-get upgrade this was the result:


sam@erin-PowerEdge-SC420:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 gir1.2-glib-2.0 : Depends: libglib2.0-0 (>= 2.39.91) but 2.32.4-0ubuntu1 is installed
 glib-networking : Depends: libglib2.0-0 (>= 2.39.4) but 2.32.4-0ubuntu1 is installed
 glib-networking-services : Depends: libglib2.0-0 (>= 2.39.3) but 2.32.4-0ubuntu1 is installed
 libgirepository-1.0-1 : Depends: libglib2.0-0 (>= 2.39.0) but 2.32.4-0ubuntu1 is installed
 libudev1 : Depends: libc6 (>= 2.17) but 2.15-0ubuntu10.5 is installed
E: Unmet dependencies. Try using -f.

---

### Post by samuel23 on 2015-01-26
(Sorry for the delay, was busy)

---

### Post by Impavidus on 2015-01-26
Try running```
sudo apt-get -f install
```as suggested. If you wish, you can first run ```
apt-get -f install -s
```This will tell you what apt-get will do. If it wants to remove anything important (which is unlikely), report back.

---

### Post by samuel23 on 2015-01-26
why would it want to remove anything important?

---

### Post by samuel23 on 2015-01-26
By the way, thank you very much for responding so quickly.

---

### Post by mc4man on 2015-01-26
If still stuck may be informative to see results of this - (picking one 'random' package from post 3, all of which seem to be indicating an attempt to upgrade well past 12.04 versions
```
apt-cache policy libudev1
```

---

### Post by Impavidus on 2015-01-27
> **samuel23 said:**
> why would it want to remove anything important?

I don't know. There is a package conflict and apt-get -f install will attempt to solve it by installing, upgrading or removing packages. So it may uninstall packages, but as I don't know what causes the problem I don't know what will be removed. But rarely something important.

It doesn't suggest to run apt-get -f install for no reason.

---

