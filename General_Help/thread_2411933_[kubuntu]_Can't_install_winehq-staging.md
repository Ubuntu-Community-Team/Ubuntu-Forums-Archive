---
title: "[kubuntu] Can't install winehq-staging"
date: 2019-02-05
forum: General Help
---

### Post by Ziad_Arafat on 2019-02-05
When I try to install winehq-staging using the instructions on their website and adding the ppa I get this odd dependency error. 

```
sudo apt-get install winehq-staging                                             
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 winehq-staging : Depends: wine-staging (= 4.0~rc7~bionic)
E: Unable to correct problems, you have held broken packages.

```

Here is my sources.list 

```
deb [arch=arm64] http://ports.ubuntu.com/ubuntu-ports/ bionic main universe restricted multiverse
deb [arch=amd64,i386] http://us.archive.ubuntu.com/ubuntu/ bionic main universe restricted multiverse 
deb [arch=amd64,i386] http://us.archive.ubuntu.com/ubuntu/ bionic-updates main universe restricted multiverse 
deb [arch=amd64,i386] http://us.archive.ubuntu.com/ubuntu/ bionic-updates main universe restricted multiverse 
deb [arch=amd64,i386] https://dl.winehq.org/wine-builds/ubuntu/ bionic main

```

everything else with apt seems to be working fine.

---

### Post by howefield on 2019-02-05
Thread moved to the "*General Help*" forum.

---

