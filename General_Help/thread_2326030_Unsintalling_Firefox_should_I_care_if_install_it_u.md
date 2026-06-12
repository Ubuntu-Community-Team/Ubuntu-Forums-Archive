---
title: "Unsintalling Firefox: should I care if install it using apt-get or dpkg?"
date: 2016-05-27
forum: General Help
---

### Post by tirengarfio2 on 2016-05-27
Hi,

I have installed Firefox and I don't know if I installed it using dpkg or apt-get, or **any other way** so I don't know know what to do to uninstall it. Does the the way to uninstall it depends on the way I installed it (apt-get ordpkg)?

---

### Post by howefield on 2016-05-27
You could try looking in the file ~/.bash_history file which will detail the 500 (I think) commands used.

Or alternatively the log files for dpkg and apt can be found at...

```
var/log/dpkg.log
```
```
var/log/apt/history.log
```

---

### Post by ajgreeny on 2016-05-27
```
grep -i " install " /var/log/dpkg.log.1 /var/log/dpkg.log | grep *packagename* 
```will specifically show if you, or perhaps the system, installed it either as a stand-alone or as a dependency of another package, provided logrotate has not removed that entry due to its age.

Or just use ```
 dpkg -s packagename 
```for the status of that package.

---

### Post by Impavidus on 2016-05-28
apt-get keeps track of all dependencies and calls dpkg for the actual installation or deinstallation. dpkg can uninstall firefox, but may break the dependency relations as it doesn't uninstall the packages depending on firefox (if there are any). If you use apt-get anything depending on firefox will be uninstalled too, keeping the package system consistent.

---

