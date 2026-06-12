---
title: "Can't install FIrestarter :("
date: 2005-05-09
forum: General Help
---

### Post by ntrsfrml on 2005-05-09
hey guys.. i wanna install a firewall to my Ubantu install.. Tried installing FIrestarter today with 

```
sudo apt-get install firestarter
```

in Terminal console.. But i get this:

```
manu15@MSHOME:~$ sudo apt-get install firestarter
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  firestarter
0 upgraded, 1 newly installed, 0 to remove and 17 not upgraded.
Need to get 569kB of archives.
After unpacking 2122kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  firestarter
Install these packages without verification [y/N]? y
Err http://backports.ubuntuforums.org hoary-backports/universe firestarter 1.0.3-1.1~5.04ubp1
  500 Internal Server Error
Failed to fetch http://backports.ubuntuforums.org/backports/dists/hoary-backports/universe/binary-i386/firestarter_1.0.3-1.1~5.04ubp1_i386.deb  500 Internal Server Error
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

Is the server offline or my cache repositories are corrupted?  :-? 

Please help.. :|

---

### Post by Efwis on 2005-05-09
[QUOTE=ntrsfrml]hey guys.. i wanna install a firewall to my Ubantu install.. Tried installing FIrestarter today with 

```
sudo apt-get install firestarter
```

in Terminal console.. But i get this:

```
manu15@MSHOME:~$ sudo apt-get install firestarter
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  firestarter
0 upgraded, 1 newly installed, 0 to remove and 17 not upgraded.
Need to get 569kB of archives.
After unpacking 2122kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  firestarter
Install these packages without verification [y/N]? y
Err http://backports.ubuntuforums.org hoary-backports/universe firestarter 1.0.3-1.1~5.04ubp1
  500 Internal Server Error
Failed to fetch http://backports.ubuntuforums.org/backports/dists/hoary-backports/universe/binary-i386/firestarter_1.0.3-1.1~5.04ubp1_i386.deb  500 Internal Server Error
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

Is the server offline or my cache repositories are corrupted?  :-? 

Please help.. :|[/QUOTE]
 I would recommed trying 

sudo apt-get update. then try it again

---

### Post by ubuntu_demon on 2005-05-09
currently there are problems with the backports server. You should try to comment the backports reps, install firestarter and uncomment the reps again. They will try to get backports up as soon as possible.

edit : it is fixed already!

---

