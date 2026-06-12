---
title: "packages not found 404 - Multiarch"
date: 2016-10-02
forum: General Help
---

### Post by raymonde1323 on 2016-10-02
Hello Community.

I have been trying to install some armhf packages on my ubuntu 16 64 bit desktop. 

I've found many pages with the same instructions and also followed the Debian how to guide [https://wiki.debian.org/Multiarch/HOWTO](https://wiki.debian.org/Multiarch/HOWTO) 

**What I have done: **

sudo dpkg --add-architecture armhf
sudo apt-get update
sudo apt-get install libc6:armhfProblem: 

During apt-get update I get a bunch of 404 errors for arm packages

**Example: ** 

```
Err:10 http://us.archive.ubuntu.com/ubuntu xenial/main armhf Packages404  Not Found [IP: 91.189.91.23 80]

```
Then I try ```
apt-get install libc6:armhf
```

but it returns ```
E: Unable to locate package libc6:armhf

```

[B]I tried adding the following to the top of my sources.list
[/B]
deb [arch=amd64,i386] [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main universe
deb [arch=armel,armhf] [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial main universe

But still the same problems. 

**What am I missing?** Any Ideas?

---

### Post by howefield on 2016-10-03
I believe armhf packages are found in the ports.ubuntu.com repository...

```
hugh@yakkety-laptop:~$ echo "deb [arch=armhf] http://ports.ubuntu.com/ubuntu-ports/ xenial main" | sudo tee -a /etc/apt/sources.listdeb [arch=armhf] http://ports.ubuntu.com/ubuntu-ports/ xenial main
hugh@yakkety-laptop:~$ sudo apt update
Hit:1 http://archive.canonical.com/ubuntu yakkety InRelease
Get:2 http://gb.archive.ubuntu.com/ubuntu yakkety InRelease [247 kB]                                                                      
Get:3 http://ports.ubuntu.com/ubuntu-ports xenial InRelease [247 kB]                                                                       
Hit:4 http://security.ubuntu.com/ubuntu yakkety-security InRelease                                                                         
Hit:5 http://gb.archive.ubuntu.com/ubuntu yakkety-updates InRelease                      
Hit:6 http://gb.archive.ubuntu.com/ubuntu yakkety-backports InRelease               
Get:7 http://ports.ubuntu.com/ubuntu-ports xenial/main armhf Packages [1,145 kB]
Get:8 http://ports.ubuntu.com/ubuntu-ports xenial/main Translation-en_GB [426 kB]
Get:9 http://ports.ubuntu.com/ubuntu-ports xenial/main Translation-en [568 kB]
Get:10 http://ports.ubuntu.com/ubuntu-ports xenial/main amd64 DEP-11 Metadata [733 kB]
Get:11 http://ports.ubuntu.com/ubuntu-ports xenial/main DEP-11 64x64 Icons [409 kB]
Fetched 3,774 kB in 2s (1,535 kB/s)                                   
Reading package lists... Done
Building dependency tree       
Reading state information... Done
26 packages can be upgraded. Run 'apt list --upgradable' to see them.
```
```
hugh@yakkety-laptop:~$ apt-cache policy libc6:armhf
libc6:armhf:
  Installed: (none)
  Candidate: 2.23-0ubuntu3
  Version table:
     2.23-0ubuntu3 500
        500 http://ports.ubuntu.com/ubuntu-ports xenial/main armhf Packages
hugh@yakkety-laptop:~$
```

---

### Post by raymonde1323 on 2016-10-05
@Howefield **Thank you for your response**. Sadly the first command you suggested did not work for me. 


> echo "deb [arch=armhf] [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) xenial main" | sudo tee -a /etc/apt/sources.listdeb [arch=armhf] [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) xenial main


This returns 


> 
tee: 'http://ports.ubuntu.com/ubuntu-ports/': No such file or directory
deb [arch=armhf] [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) xenial main


I Also Tried


> echo "deb [arch=armhf] [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) xenial main" | sudo tee -a /etc/apt/sources.list deb [arch=armhf] [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) xenial main


(space between "sources.list" & "deb [arch=armhf] http://ports...")


Same result as above.


**Any more Ideas? **


I am trying to use Qemu in order to compile  a binary for armhf as described here [https://wiki.debian.org/QemuUserEmulation](https://wiki.debian.org/QemuUserEmulation)


Here is my current sources.list file. [B]Thank you for your time. 
[/B]
> #deb cdrom:[Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)]/ xenial main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse

---

### Post by howefield on 2016-10-06
Many apologies, my mistake. 

Can't understand how I managed to copy/paste from my terminal so badly :)

The command should be..

```
echo "deb [arch=armhf] http://ports.ubuntu.com/ubuntu-ports/ xenial main" | sudo tee -a /etc/apt/sources.list
```

Eg,
```
hugh@yakkety-laptop:~$ echo "deb [arch=armhf] http://ports.ubuntu.com/ubuntu-ports/ xenial main" | sudo tee -a /etc/apt/sources.list
[sudo] password for hugh: 
deb [arch=armhf] http://ports.ubuntu.com/ubuntu-ports/ xenial main
hugh@yakkety-laptop:~$
```
```
hugh@yakkety-laptop:~$ apt-cache policy libc6:armhf
libc6:armhf:
  Installed: (none)
  Candidate: 2.23-0ubuntu3
  Version table:
     2.23-0ubuntu3 500
        500 http://ports.ubuntu.com/ubuntu-ports xenial/main armhf Packages
hugh@yakkety-laptop:~$
```

---

### Post by raymonde1323 on 2016-10-07
Thank you very much!!! That command worked good and lib6:armhf installed successfully.:D

I will now go on to trying to figure out the rest about using qemu to cross compile. Sadly the the documentation seems a bit outdated.

---

### Post by howefield on 2016-10-08
Cool, glad you got it, feel free to mark the thread as solved :)

---

