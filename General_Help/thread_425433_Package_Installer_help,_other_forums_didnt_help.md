---
title: "Package Installer help, other forums didnt help"
date: 2007-04-27
forum: General Help
---

### Post by |FB|Jay on 2007-04-27
Hey fellow ubuntu users;

Im currently using Ubuntu 7.04 (Fiesty if i remember) and i desperatly need to use the apt-get and the deb installer. Unfortunatly, neithe rof these work for me.

The package Installer for DEB files states 'Your system has broken dependencies' and i tried the commands it says, synaptic allows me to get in the synaptic installer but fails to install anything. The apt-get install -f command shows this:
> Errors were encountered while processing:
 libgtkmm-2.4-1c2a
 libcairomm-1.0-1
 libdebconfclient0
 libdebian-installer4
 libdiscover1
 libfuse2
 libglibmm-2.4-1c2a
 libntfs9
 xfsprogs
E: Sub-process /usr/bin/dpkg returned an error code (1)


I want to install an online game, buy libgtk isnt installed, i plan to install vie apt-get but it fails as stated above.

Thanks if you reply,

Jay

---

### Post by bapoumba on 2007-04-27
Could you please post your sources.list ?
Open a terminal (> Accessories > Terminal) and run:
```
cat /etc/apt/sources.list
```

And the errors to:
```
sudo aptitude update
```

---

