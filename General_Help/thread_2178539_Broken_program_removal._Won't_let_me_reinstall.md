---
title: "Broken program removal. Won't let me reinstall"
date: 2013-10-03
forum: General Help
---

### Post by GRX13 on 2013-10-03
I don't remember what I did but I have kid3 which is a metadata editor stuck under my Sound & Video menu and tab completes as kid3-qt in terminal but refuses to open either way saying:

> kid3-qt: error while loading shared libraries: libkid3-gui.so: cannot open shared object file: No such file or directory
I removed it using synaptic, aptitude and a sudo rm -rf from /etc at one point I think. 

If I reinstall it from an outdated repository it will not open and removing that does not remove the name from the menu or the tab completed name in terminal, the symlink I think.

What can I do to completely remove kid3-qt now?

Ubuntu 12.04 with lxde.

Edit: There is still kid3-qt hiding in /usr/local/bin.

---

### Post by Bashing-om on 2013-10-03
Groxxxy; Hi !

Have you tried:
```

sudo apt-get remove --purge kid3-qt

```
If not, there may now be not enough left on the system for the package manager to work with. But may get errors to indicate where else to look.

[INDENT][INDENT]worth a shot
[/INDENT][/INDENT]

---

### Post by GRX13 on 2013-10-03
> Package kid3-qt is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
I had tried that command already. At the moment I cannot use the program that wouldn't install flawlessly because it uninstalled incorrectly. I don't know how to find all remnants of kid3/kid3-qt to remove it manually.


Edit: Used grep -Hri 'kid3' > foo.txt in /usr to find all the junk and sudo rm -f. I installed from an old repo and it works fine now. Now I have to work out why I can't compile a better version from git.

---

### Post by Bashing-om on 2013-10-04
Groxxxy; That is tough !

Maybe:
```

ls -la /var/lib/dpkg/info/kid3-qt.list

```
and if that file is still in existence.
```

cat /var/lib/dpkg/info/kid3-qt.list

```
which is the config file for every file that "kid3-qt" installed and where those files were installed to.

[INDENT][INDENT]hope burns eternal
[/INDENT][/INDENT]

---

