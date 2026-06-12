---
title: "Dependency problem aria2 installation."
date: 2015-04-03
forum: General Help
---

### Post by itsnedd on 2015-04-03
Hello, when im installing aria2 which is the download accelerator i seem to have problem about the dependencies.

[ATTACH=CONFIG]261061[/ATTACH][ATTACH=CONFIG]261062[/ATTACH][ATTACH=CONFIG]261063[/ATTACH]


Here's the error code on the terminal:
```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 aria2 : Depends: libc-ares2 (>= 1.7.1) but it is not installable
E: Unable to correct problems, you have held broken packages.

```

Please also see my attachments for more info, Thank you!

---

### Post by dino99 on 2015-04-03
just tested intallation on vivid i386: no problem

so you might have some non genuine entry into /etc/apt/sources.list and/or installed some untrusted packages

---

### Post by ian-weisser on 2015-04-03
The attachment links don't seem to work for me. "Invalid Attachment specified".

Please try the following command and paste the complete output here (inside CODE tags)
```
apt-cache policy aria2 libc-ares2
```

---

### Post by itsnedd on 2015-04-04
Still The Same bro:
```
neddyr@neddyr-CR643:~$ apt-cache policy aria2 libc-ares2aria2:
  Installed: (none)
  Candidate: 1.18.1-1
  Version table:
     1.18.1-1 0
        500 http://ph.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
libc-ares2:
  Installed: (none)
  Candidate: (none)
  Version table:

```

---

### Post by itsnedd on 2015-04-04
How do i verify or remove that.

---

### Post by ian-weisser on 2015-04-04
Need to do a little digging:

Try:
```
sudo apt-get install libc-ares2
```
We already know it probably won't work. The error message should be helpful.

---

### Post by mc4man on 2015-04-04
Maybe check Software & Updates to make sure the main repo is enabled.

---

### Post by itsnedd on 2015-04-05
Here's the error message bro:
```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Package libc-ares2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'libc-ares2' has no installation candidate

```

---

### Post by ian-weisser on 2015-04-05
> **itsnedd said:**
> E: Package 'libc-ares2' has no installation candidate
mc4man is right. You have disabled or deleted your 'main' repository from your software sources.
Restore it.

If you need help restoring it, then copy-and-paste the contents of your /etc/apt/sources.list file here.

---

### Post by itsnedd on 2015-04-05
Hi this is the sources.list file:
```
# deb cdrom:[Ubuntu 14.04.2 LTS _Trusty Tahr_ - Release amd64 (20150218.1)]/ trusty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ph.archive.ubuntu.com/ubuntu/ trusty restricted
deb-src http://ph.archive.ubuntu.com/ubuntu/ trusty restricted


## Major bug fix updates produced after the final release of the
## distribution.


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ph.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://ph.archive.ubuntu.com/ubuntu/ trusty universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ph.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://ph.archive.ubuntu.com/ubuntu/ trusty multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ph.archive.ubuntu.com/ubuntu/ trusty-backports restricted universe multiverse
deb-src http://ph.archive.ubuntu.com/ubuntu/ trusty-backports restricted universe multiverse


deb http://ph.archive.ubuntu.com/ubuntu/ trusty-security restricted
deb-src http://ph.archive.ubuntu.com/ubuntu/ trusty-security restricted
deb http://ph.archive.ubuntu.com/ubuntu/ trusty-security universe
deb-src http://ph.archive.ubuntu.com/ubuntu/ trusty-security universe
deb http://ph.archive.ubuntu.com/ubuntu/ trusty-security multiverse
deb-src http://ph.archive.ubuntu.com/ubuntu/ trusty-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu trusty partner
deb-src http://archive.canonical.com/ubuntu trusty partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb http://ph.archive.ubuntu.com/ubuntu/ trusty-updates restricted universe multiverse
deb http://repository.spotify.com stable non-free
# deb-src http://repository.spotify.com stable non-free
deb-src http://extras.ubuntu.com/ubuntu trusty main
deb http://ph.archive.ubuntu.com/ubuntu/ trusty-proposed restricted multiverse universe
```

Guys thank you for all of your help.

---

### Post by ian-weisser on 2015-04-05
Add the following lines to /etc/apt/sources.list to add the main repository:
```
deb http://ph.archive.ubuntu.com/ubuntu/ trusty main
deb http://ph.archive.ubuntu.com/ubuntu/ trusty-security main
deb http://ph.archive.ubuntu.com/ubuntu/ trusty-updates main
```

FYI, you should probably disable:
```
deb http://ph.archive.ubuntu.com/ubuntu/ trusty-proposed restricted multiverse universe
```
Running -proposed is a good way to break your system.

After you edit /etc/apt/sources.list, you should be able to install aria2
```
sudo apt-get update          ## Refresh the package database first, since you changed sources!
sudo apt-get upgrade         ## Make sure you didn't miss any security updates
sudo apt-get install aria2
```

---

