---
title: "What is This...."
date: 2013-01-28
forum: General Help
---

### Post by LinXNut on 2013-01-28
So I went to upgrade my system the other day, and noticed while the updates were installing it replaced my "Fglrx-updates" with something weird. ( I don't remember the name). But after I rebooted, the only driver I had in use was "radeon" which is no good. I proceeded to additional drivers and installed the original "Fglrx" driver, but noticed the "Fglrx-updates" driver was missing. I tested something in the terminal, and this is what I get...

```
jonathan@jonathan-Lappy:~$ sudo apt-get install fglrx*
[sudo] password for jonathan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'fglrx-updates' for regex 'fglrx*'
Note, selecting 'fglrx-driver-dev' for regex 'fglrx*'
Note, selecting 'fglrx-amdcccle-updates' for regex 'fglrx*'
Note, selecting 'fglrx-amdcccle-experimental-9' for regex 'fglrx*'
Note, selecting 'fglrx' for regex 'fglrx*'
Note, selecting 'fglrx-driver' for regex 'fglrx*'
Note, selecting 'fglrx-experimental-9-dev' for regex 'fglrx*'
Note, selecting 'fglrx-experimental-9' for regex 'fglrx*'
Note, selecting 'xfree86-driver-fglrx-dev' for regex 'fglrx*'
Note, selecting 'fglrx-control' for regex 'fglrx*'
Note, selecting 'fglrx-amdcccle' for regex 'fglrx*'
Note, selecting 'fglrx-dev' for regex 'fglrx*'
Note, selecting 'fglrx-modaliases' for regex 'fglrx*'
Note, selecting 'fglrx-glx' for regex 'fglrx*'
Note, selecting 'fglrx-kernel-source' for regex 'fglrx*'
Note, selecting 'xorg-driver-fglrx' for regex 'fglrx*'
Note, selecting 'fglrx-control-qt2' for regex 'fglrx*'
Note, selecting 'fglrx-updates-dev' for regex 'fglrx*'
Note, selecting 'xorg-driver-fglrx-dev' for regex 'fglrx*'
Note, selecting 'xfree86-driver-fglrx' for regex 'fglrx*'
fglrx is already the newest version.
fglrx-amdcccle is already the newest version.
fglrx-amdcccle set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 fglrx : Conflicts: fglrx-driver
 fglrx-amdcccle : Conflicts: fglrx-control
 fglrx-amdcccle-experimental-9 : Conflicts: fglrx-control
 fglrx-amdcccle-updates : Conflicts: fglrx-control
 fglrx-dev : Conflicts: fglrx-driver-dev
 fglrx-experimental-9 : Conflicts: fglrx-driver
 fglrx-experimental-9-dev : Conflicts: fglrx-driver-dev
 fglrx-updates : Conflicts: fglrx-driver
 fglrx-updates-dev : Conflicts: fglrx-driver-dev
E: Unable to correct problems, you have held broken packages.
jonathan@jonathan-Lappy:~$ 

```So do I have broken packages? My graphics are a little slower, and I think it had something to do with that update. Any help would be greatly appreciated!
:popcorn:

LinXNut

---

