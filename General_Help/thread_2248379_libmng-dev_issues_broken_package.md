---
title: "libmng-dev issues broken package"
date: 2014-10-14
forum: General Help
---

### Post by cscj01 on 2014-10-14
Ever since I upgraded fron Ubuntu 12.04.5 x64 -> 14.04.1, i have been getting a message on Update Manager saying that updates to libmng-dev were held back.  I had libmng2 and libmng1 installed.  This seemed somewhat redundant (I'm really not sure, but the description was the same for both, and I assumed that libmng2 was the latest), so I removed libmng1.  I tried to upgrade libmng-dev, but it still failed as a broken package.  I tried Fix Broken Packages from within Synaptic, but I received the following message:```
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
```I then removed libmng-dev and tried to install it with Synaptic.  Once again I received a message about broken packages```
Could not apply changes!
Fix broken packages first.
```Then I open a terminal and entered the following and got these results:```
sudo apt-get install libmng-dev
[sudo] password for butch: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libmng-dev : Depends: liblcms2-dev but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```So I then entered the following:```
sudo apt-get install liblcms2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 liblcms2-dev : Depends: liblcms2-2 (= 2.5-0ubuntu4) but 2.5-1 is to be installed
E: Unable to correct problems, you have held broken packages.
```I am at a loss as to how to proceed.  In particular, how do I fix this broken package?  Thanks.

---

### Post by cscj01 on 2014-10-15
I was able to resolve this by using the following:```
sudo aptitude install libmng-dev
```I had to accept the second solution that downgraded liblcms2-dev.  I then issued the following commands which performed no actions:```
sudo apt-get update
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get upgrade
```

---

