---
title: "Unable to Install/Update/Etc."
date: 2013-06-03
forum: General Help
---

### Post by mjkaufer on 2013-06-03
Hi guys.
Whenever I try to run apt-get install for a program I'm trying to install (e.g. Synaptic), I get yelled at. 

```
 
$me@me:~$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libjpeg8-dev : Depends: libjpeg8 (= 8d-1) but 8c-2ubuntu7 is to be installed
 synaptic : Depends: libept1.4.12 but it is not going to be installed
            Depends: libvte9 (>= 1:0.24.0) but it is not going to be installed
            Recommends: rarian-compat but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

apt-get -f install yields me with this
```

$me@me:~$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 libjpeg8-dev : Depends: libjpeg8 (= 8d-1) but 8c-2ubuntu7 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies




```

Does anyone here have any suggestions/solutions for me? Ubuntu 12.04 
The contents of my sources.list are here:
[http://pastebin.com/AHch11ZB](http://pastebin.com/AHch11ZB)

Thanks in advance.

---

### Post by fantab on 2013-06-03
Try the following command in the TERMINAL:

```
sudo dpkg --purge libjpeg8
sudo apt-get remove --purge libjpeg8
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install synaptic
```

If you still get errors, then post the output of *sudo apt-get update* here.

---

### Post by mjkaufer on 2013-06-05
#apt-get update throws no errors, but installing new packages does. 
For instance, trying to install synaptic throws the following code at me.
```
me@me:~$ sudo apt-get install synapticReading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libjpeg8-dev : Depends: libjpeg8 (= 8d-1) but 8c-2ubuntu7 is to be installed
 synaptic : Depends: libept1.4.12 but it is not going to be installed
            Depends: libvte9 (>= 1:0.24.0) but it is not going to be installed
            Recommends: rarian-compat but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).



```

---

### Post by fantab on 2013-06-05
Rerun the commands in post #10 but replace 'libjpeg8' with **'libjpeg8-dev' **in the first two commands.

---

