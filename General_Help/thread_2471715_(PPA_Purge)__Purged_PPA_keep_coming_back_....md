---
title: "(PPA Purge)  Purged PPA keep coming back ..."
date: 2022-02-07
forum: General Help
---

### Post by csae2608 on 2022-02-07
Hello,

today i wanted to upgrade 18,04 LTS to 20.04 LTS

however, the upgrade process would not pass through, most probably due to unofficial PPA§s


so i try to disable those, but they seem to bounce back every time.

```
Hit:1 http://it.archive.ubuntu.com/ubuntu bionic InRelease
Get:2 http://security.ubuntu.com/ubuntu bionic-security InRelease [88,7 kB]    
Get:3 http://ppa.launchpad.net/deadsnakes/ppa/ubuntu bionic InRelease [15,9 kB]
Hit:4 http://it.archive.ubuntu.com/ubuntu bionic-updates InRelease             
Hit:5 http://it.archive.ubuntu.com/ubuntu bionic-backports InRelease           
Get:6 http://ppa.launchpad.net/mozillateam/ppa/ubuntu bionic InRelease [20,8 kB]
Get:7 http://ppa.launchpad.net/deadsnakes/ppa/ubuntu bionic/main i386 Packages [37,9 kB]
Get:8 https://repo.radeon.com/amdgpu/21.40.2/ubuntu bionic InRelease [5.462 B] 
Get:9 http://ppa.launchpad.net/deadsnakes/ppa/ubuntu bionic/main amd64 Packages [37,9 kB]
Get:10 https://repo.radeon.com/rocm/apt/4.5.2 ubuntu InRelease [1.816 B]       
Get:11 http://ppa.launchpad.net/deadsnakes/ppa/ubuntu bionic/main Translation-en [8.404 B]
Get:12 http://ppa.launchpad.net/mozillateam/ppa/ubuntu bionic/main amd64 Packages [23,8 kB]
Get:13 https://repo.radeon.com/amdgpu/21.40.2/ubuntu bionic/main i386 Packages [12,9 kB]
Get:14 https://repo.radeon.com/amdgpu/21.40.2/ubuntu bionic/main amd64 Packages [13,8 kB]
Get:15 http://ppa.launchpad.net/mozillateam/ppa/ubuntu bionic/main i386 Packages [23,9 kB]
Get:16 https://repo.radeon.com/rocm/apt/4.5.2 ubuntu/main amd64 Packages [25,2 kB]
Get:17 http://ppa.launchpad.net/mozillateam/ppa/ubuntu bionic/main Translation-en [6.700 B]

```

with the help of this guide and synaptic/terminal here i remove

[https://itsfoss.com/how-to-remove-or-delete-ppas-quick-tip/](https://itsfoss.com/how-to-remove-or-delete-ppas-quick-tip/)

"mozillateam" "deadsnakes" and "amdgpu"

afterwards i would do "sudo apt update"

and result only show "ubuntu sources"


however, 

```

Checking package manager
Reading package lists... Done    
Building dependency tree          
Reading state information... Done

Calculating the changes

Calculating the changes

Could not calculate the upgrade 

An unresolvable problem occurred while calculating the upgrade. 

If none of this applies, then please report this bug using the 
command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal. If 
you want to investigate this yourself the log files in 
'/var/log/dist-upgrade' will contain details about the upgrade. 
Specifically, look at 'main.log' and 'apt.log'. 


Restoring original system state

Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done

```



and afterwards, the PPA are back instated.


Is there another more concise way to remove those unwanted PPA for the moment?


thanks

---

### Post by csae2608 on 2022-02-07
Ok, 

found a way to remove these unwanted PPA, as shown in the link above under Method N.3,

```
sudo rm -i /etc/apt/sources.list.d/*
```

and stating "Y" for "yes" for every proposal would rid me of those PPA, but the upgrade to 20.04 LTS would stall nevertheless .


here is the log from /var/log/dist-upgrade

apt.log [URL="https://paste.kodi.tv/ojurexohul"]https://paste.kodi.tv/ojurexohul
[/URL]main.log [URL="https://paste.kodi.tv/bovilayemo.kodi"]https://paste.kodi.tv/bovilayemo.kodi


[/URL]Thanks

---

### Post by Impavidus on 2022-02-07
Your main.log has two errors related to the epsonscan2 and epsonscan2-nonfree-plugin packages. Those are epson scanner drivers. You can remove them before the upgrade. Then go to the epson website and download the drivers for the new Ubuntu release. Install those after the upgrade.

The main problem is mentioned in your apt.log. With some digging I found this line:```
    python3.8-dev:amd64 Hängt ab von on libpython3.8:amd64 < 3.8.12-1+bionic3 @ii mK > (= 3.8.10-0ubuntu1~20.04.2) can't be satisfied!
```Looks like there's a version conflict in python and your current version appears to be 3.8.12-1+bionic3, which is later than 3.8.10-0ubuntu1~20.04.2, which is the version you get on Ubuntu 20.04. The version in the official repos for Ubuntu 18.04 is 3.8.0-3ubuntu1~18.04.2, which is older than your version. And the upgrader doesn't know how to solve this. Did one of those PPAs give you a newer version of python?

Replacing the python version from the official repos with a different version is a recipe for disaster. It's hard to solve. You could try downgrading python 3 to the version in the bionic repository first. Don't think too long about it though; a fresh install takes just half an hour.

---

### Post by csae2608 on 2022-02-07
> **Impavidus said:**
> Your main.log has two errors related to the epsonscan2 and epsonscan2-nonfree-plugin packages. Those are epson scanner drivers. You can remove them before the upgrade. Then go to the epson website and download the drivers for the new Ubuntu release. Install those after the upgrade.

The main problem is mentioned in your apt.log. With some digging I found this line:```
    python3.8-dev:amd64 Hängt ab von on libpython3.8:amd64 < 3.8.12-1+bionic3 @ii mK > (= 3.8.10-0ubuntu1~20.04.2) can't be satisfied!
```Looks like there's a version conflict in python and your current version appears to be 3.8.12-1+bionic3, which is later than 3.8.10-0ubuntu1~20.04.2, which is the version you get on Ubuntu 20.04. The version in the official repos for Ubuntu 18.04 is 3.8.0-3ubuntu1~18.04.2, which is older than your version. And the upgrader doesn't know how to solve this. Did one of those PPAs give you a newer version of python?

Replacing the python version from the official repos with a different version is a recipe for disaster. It's hard to solve. You could try downgrading python 3 to the version in the bionic repository first. Don't think too long about it though; a fresh install takes just half an hour.


Thanks very much for helping me,

yes , i had "deadsnakes! repo for python3.8    but did not think this would have been a problem, but after quick look in apt.log noticed the python issue aswell,
however would not have thought of the Epson scan packages, although i had quite some issues before on 20.04 and later with Epson Driver and Scanner, sadly.


Resolved by installing the 20.04 LTS anew, not very elegante, but now its quick and am happy about it.

All the best.

---

