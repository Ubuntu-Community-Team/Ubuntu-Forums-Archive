---
title: "Updating without update manager"
date: 2013-09-23
forum: General Help
---

### Post by sideburns on 2013-09-23
My sister needs to update her netbook, but every time she tries, update-manager crashes.  Right now, I'm talking her through reporting this as a bug (The crash report suggests this.) but she still needs to get updated.  If nothing else, we'll need to get the fixed version of update-manager installed.  I'm sure that it's fairly trivial to do, but as I don't use Ubuntu myself, I don't know the right command, so a pointer in the right direction will be appreciated.

---

### Post by bibek2 on 2013-09-23
sudo apt-get update
then
sudo apt-get dist-upgrade

---

### Post by sideburns on 2013-09-23
Thanx, but I don't think that dist-upgrade is needed because AFAIK she's running the latest version.  Still, it's nice to know that, for this at least, apt-get and yum (what I use) have the same syntax.

---

### Post by ibjsb4 on 2013-09-23
Number 3

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by deadflowr on 2013-09-23
```
sudo apt-get upgrade
```
will safely upgrade the system,
```
sudo apt-get dist-upgrade
```
will upgrade the system, but may change or remove packages.
Which might cause stability issues.

---

### Post by bibek2 on 2013-09-23
> **deadflowr said:**
> ```
sudo apt-get upgrade
```
will safely upgrade the system,
```
sudo apt-get dist-upgrade
```
will upgrade the system, but may change or remove packages.
Which might cause stability issues.

I always thought that apt-get upgrade only updates the packages that are currently installed and does not add or remove packages to satisfy new dependencies which may result in unstable system whereas apt-get dist-upgrade installs new dependencies as well hence you are guaranteed a working system. Thanks for clarifying :)

---

