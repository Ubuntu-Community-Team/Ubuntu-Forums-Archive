---
title: "Unmet Dependencies"
date: 2012-11-28
forum: General Help
---

### Post by captaincactuz on 2012-11-28
Hello, I run Ubuntu 12.04 and have been having a problem with unmet dependencies: 

The following packages have unmet dependencies:
 libmtp-dev : Depends: libmtp8 (= 1.0.2-1ubuntu1) but it is not installable
 libusb-dev : Depends: libusb-0.1-4 (= 2:0.1.12-14ubuntu0.2) but 2:0.1.12-20 is to be installed

I believe these unmet dependencies are what are preventing me from being able to install any new software and from even accessing the software center because it says the the package catalog needs to be repaired but it never works.

I have tried sudo apt-get -f install, I have also tried removing libmtp-dev and libusb-dev but to no avail.

Any suggestions? :confused:

---

### Post by gnusci on 2012-11-28
Did you try:

$ sudo apt-get update
$ sudo apt-get upgrade

---

### Post by captaincactuz on 2012-11-29
manny@manny-Qosmio-X505:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libmtp-dev : Depends: libmtp8 (= 1.0.2-1ubuntu1) but it is not installable
 libusb-dev : Depends: libusb-0.1-4 (= 2:0.1.12-14ubuntu0.2) but 2:0.1.12-20 is installed
E: Unmet dependencies. Try using -f.

---

### Post by mc4man on 2012-11-29
Well your 
libmtp8 (= 1.0.2-1ubuntu1) is from lucid, the version in precise is libmtp[COLOR="Red"]9[/COLOR] (1.1.3-1ubuntu0.1)

As far as libusb-0.1-4 (2:0.1.12-20) that's the precise version but it's trying to instll the lucid version of libusb-dev (2:0.1.12-14)

Maybe post your sources.list
```
cat /etc/apt/sources.list
```

Also possibly open software sources
 ```
software-properties-gtk
```
and switch to a new server, try Main server, then close software sources & update sources
```
sudo apt-get update
```
ect..

---

### Post by captaincactuz on 2012-11-29
Okay I changed the server to main, updated then tried to upgrade and got the same response as before. Here's the content of sources.list:


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

---

### Post by mc4man on 2012-11-29
Do you have any ppa's enabled?
ls /etc/apt/sources.list.d

What happens if you install libmtp9?
```
sudo apt-get install libmtp9
```

if it installs without issue or is already installed then simulate removing libmtp8 & post
```
sudo apt-get -s purge libmtp8
```

---

### Post by captaincactuz on 2012-11-29
I've got these ppa's, but I disabled them all:

ehoover-compholio-precise.list          kubuntu-ppa-backports-precise.list
ehoover-compholio-precise.list.save     kubuntu-ppa-backports-precise.list.save
glennric-dolphin-emu-precise.list       pmcenery-ppa-precise.list
glennric-dolphin-emu-precise.list.save  pmcenery-ppa-precise.list.save


And also it seems I already have libmtp9:

manny@manny-Qosmio-X505:~$ sudo apt-get install libmtp9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libmtp9 is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libmtp-dev : Depends: libmtp8 (= 1.0.2-1ubuntu1) but it is not installable
 libusb-dev : Depends: libusb-0.1-4 (= 2:0.1.12-14ubuntu0.2) but 2:0.1.12-20 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

manny@manny-Qosmio-X505:~$ sudo apt-get -s purge libmtp8
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libmtp-dev : Depends: libmtp8 (= 1.0.2-1ubuntu1) but it is not installable
 libusb-dev : Depends: libusb-0.1-4 (= 2:0.1.12-14ubuntu0.2) but 2:0.1.12-20 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by mc4man on 2012-11-29
Try 
sudo apt-get clean
Then see if anything changes after updating sources

---

### Post by captaincactuz on 2012-11-29
Same thing after the sudo apt-get clean:


The following extra packages will be installed:
  libmtp-dev libusb-dev
The following packages will be upgraded:
  libmtp-dev libusb-dev
2 upgraded, 0 newly installed, 0 to remove and 38 not upgraded.
2 not fully installed or removed.
Need to get 45.6 kB of archives.
After this operation, 494 kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main libmtp-dev amd64 1.1.3-1ubuntu0.1 [10.6 kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main libusb-dev amd64 2:0.1.12-20 [35.0 kB]
Fetched 45.6 kB in 0s (51.3 kB/s)    
dpkg: dependency problems prevent configuration of libmtp-dev:
 libmtp-dev depends on libmtp8 (= 1.0.2-1ubuntu1); however:
  Package libmtp8 is not installed.
dpkg: error processing libmtp-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libusb-dev:
 libusb-dev depends on libusb-0.1-4 (= 2:0.1.12-14ubuntu0.2); however:
  Version of libusb-0.1-4 on system is 2:0.1.12-20.
dpkg: error processing libusb-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 libmtp-dev
 libusb-dev

---

### Post by mc4man on 2012-11-29
nv for a minute

---

### Post by captaincactuz on 2012-11-29
nv?

---

### Post by captaincactuz on 2012-12-01
bump

---

