---
title: "Software Updater keeps installing packages that apt says are unused"
date: 2016-06-01
forum: General Help
---

### Post by vincent36 on 2016-06-01
Software Updater keeps installing (or offering to install) several packages that later on turn out to be unused (through apt-get autoremove). I would assume that both would come to the same result.

[ATTACH=CONFIG]269382[/ATTACH][ATTACH=CONFIG]269383[/ATTACH]

If i remove the packages the system keeps running just fine except for software updater popping up telling me it needs the packages. I am thinking that apt-get is correct and software updater is not.

---

### Post by howefield on 2016-06-01
Try removing them and then update the system from the command line..

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by vincent36 on 2016-06-01
Done, results in the same thing. 
After a while the software updater will pop up (or if you start it manually it will check of course) with those specific packages that need updating.

Good to mention, i usually update from the commandline, i even made an alias for it.
update='sudo apt-get autoremove && sudo apt update && sudo apt upgrade'

---

### Post by howefield on 2016-06-01
So, were those four packages reinstalled with the command line update/upgrade ?

If not, try installing them with apt-get.

---

### Post by vincent36 on 2016-06-01
I can install them manually and oddly enough autoremove then doesn't complain about them being unused. what happened?

[edit] removed my start of the reply since i even confused myself [/edit]

---

### Post by Impavidus on 2016-06-01
Both software updater and apt-get upgrade will offer upgrades to those packages as long as they are installed, even if they are autoremovable. Autoremovable packages are those packages that are marked as automatically installed and are not depended upon by other installed packages. By manually installing those packages they get marked as manually installed, so they will not be autoremoved.

---

### Post by vincent36 on 2016-06-01
Awesome, thanks for that answer, explained and taken care of

---

