---
title: "Can't update LLVM in a release upgraded Ubuntu (19.10 &gt; 20.04)"
date: 2020-04-23
forum: General Help
---

### Post by CelticWarrior on 2020-04-23
The 'libc++1' package is being kept for some reason:
```
The following packages have been kept back:
  libc++1
```

The Updates utility shows this versions:
```
Installed: 1:9.0-49~exp1
Available: 1:10.0-50~exp1
```

How can I investigate why this is?
What can be the causes, i.e., what is using this specific version and keeping it from being updated?
Is this a problem?

---

### Post by &amp;KyT$0P# on 2020-04-23
> **CelticWarrior said:**
> How can I investigate why this is?

Can you please post the output from running these commands in Terminal? -
```
sudo apt-get update
apt-get -s install libc++1/focal
```

---

### Post by CelticWarrior on 2020-04-23
> **halogen2 said:**
> Can you please post the output from running these commands in Terminal? -
```
sudo apt-get update
apt-get -s install libc++1/focal
```

Sure. :P

From 'sudo apt-get update':
```
Hit:1 http://linux.teamviewer.com/deb stable InRelease                         
Hit:2 http://archive.canonical.com/ubuntu focal InRelease                      
Ign:3 http://liveusb.info/multisystem/depot all InRelease                      
Ign:4 http://repo.vivaldi.com/stable/deb stable InRelease                    
Hit:5 http://repo.vivaldi.com/stable/deb stable Release                      
Hit:6 http://liveusb.info/multisystem/depot all Release                
Hit:7 http://repo.yandex.ru/yandex-disk/deb stable InRelease           
Get:10 http://archive.ubuntu.com/ubuntu focal InRelease [265 kB]               
Hit:11 http://ppa.launchpad.net/atareao/atareao/ubuntu focal InRelease         
Ign:12 http://dl.google.com/linux/chrome/deb stable InRelease                  
Hit:13 http://dl.google.com/linux/chrome/deb stable Release                    
Hit:14 http://ppa.launchpad.net/gerardpuig/ppa/ubuntu focal InRelease          
Hit:16 http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu focal InRelease
Hit:17 http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu focal InRelease    
Hit:18 http://ppa.launchpad.net/phoerious/keepassxc/ubuntu focal InRelease     
Hit:19 http://ppa.launchpad.net/slytomcat/ppa/ubuntu focal InRelease           
Hit:20 http://ppa.launchpad.net/team-xbmc/ppa/ubuntu focal InRelease           
Hit:21 http://archive.ubuntu.com/ubuntu focal-updates InRelease                
Hit:22 http://archive.ubuntu.com/ubuntu focal-backports InRelease              
Hit:23 http://archive.ubuntu.com/ubuntu focal-security InRelease               
Fetched 265 kB in 16s (16,2 kB/s)                                              
Reading package lists... Done
Building dependency tree       
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.
```

And the simulation showed:
```
NOTE: This is only a simulation!
      apt-get needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Selected version '1:10.0-50~exp1' (Ubuntu:20.04/focal [amd64]) for 'libc++1'
The following additional packages will be installed:
  libc++1-10 libc++abi1-10
Suggested packages:
  clang
The following packages will be REMOVED:
  libc++1-9 libc++abi1-9
The following NEW packages will be installed:
  libc++1-10 libc++abi1-10
The following packages will be upgraded:
  libc++1
1 upgraded, 2 newly installed, 2 to remove and 0 not upgraded.
Inst libc++1 [1:9.0-49~exp1] (1:10.0-50~exp1 Ubuntu:20.04/focal [amd64]) []
Remv libc++1-9 [1:9.0.1-12] []
Remv libc++abi1-9 [1:9.0.1-12] []
Inst libc++abi1-10 (1:10.0.0-4ubuntu1 Ubuntu:20.04/focal [amd64]) []
Inst libc++1-10 (1:10.0.0-4ubuntu1 Ubuntu:20.04/focal [amd64])
Conf libc++1 (1:10.0-50~exp1 Ubuntu:20.04/focal [amd64])
Conf libc++abi1-10 (1:10.0.0-4ubuntu1 Ubuntu:20.04/focal [amd64])
Conf libc++1-10 (1:10.0.0-4ubuntu1 Ubuntu:20.04/focal [amd64])

```


So, I went ahead and installed it for real. Now APT seems to be at an happy place:
```
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Many thanks, I'll mark this one as solved.

---

