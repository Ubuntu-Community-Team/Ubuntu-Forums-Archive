---
title: "aptitude question"
date: 2008-07-06
forum: General Help
---

### Post by NetworkGuy on 2008-07-06
I'm trying to install a package from the ppa.launchpad.net.   Aptitude is holding back the 5 packages I need.   I think I need a gpg key but can't find it.  Can someone point me in the right direction?

Thanks.

EDIT - Update Manager is a godsend  :)

---

### Post by EXCiD3 on 2008-07-06
haha yeah for some reason aptitude likes to hold back packages. you dont *need* gpg keys, they are just there to authenticate the the source you are downloading the packages from is legit and not some phony place.

---

### Post by aroch1 on 2008-07-06
If you don't want to leave the terminal/aptitude for the GUI/Update Manager, you can do

```
sudo aptitude dist-upgrade
```

or

```
sudo aptitude safe-upgrade
```

to get it to install the held-back packages.

---

### Post by EXCiD3 on 2008-07-07
Thanks aroch1...after all this time ive used ubuntu...ive never even see safe-upgrade before! just goes to show how helpful the forums are! :)

---

