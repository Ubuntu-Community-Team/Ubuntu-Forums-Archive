---
title: "keith@keith-Desktop:~$ sudo apt update [sudo] password for keith:  E: Type ‘sudo’ is"
date: 2018-07-31
forum: General Help
---

### Post by Frogster on 2018-07-31
Trying to Install some software and I have this message in the terminal and software center. Ubuntu 18.04

How do I correct this? Sorry I am a little rusty as Ubuntu has been so good to me over the last few years

keith@keith-Desktop:~$ sudo apt update
[sudo] password for keith: 
E: Type &#8216;sudo&#8217; is not known on line 52 in source list /etc/apt/sources.list
E: The list of sources could not be read.

---

### Post by sisco311 on 2018-07-31
What is the content of the */etc/apt/sources.list* file?
```
cat /etc/apt/sources.list
```

Please post it between ```
 tags:
[noparse][code]...
```[/noparse]

---

### Post by Frogster on 2018-07-31
```
keith@keith-Desktop:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 18.04.1 LTS _Bionic Beaver_ - Release amd64 (20180725)]/ bionic main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ bionic main restricted
# deb-src http://gb.archive.ubuntu.com/ubuntu/ bionic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
# deb-src http://gb.archive.ubuntu.com/ubuntu/ bionic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ bionic universe
# deb-src http://gb.archive.ubuntu.com/ubuntu/ bionic universe
deb http://gb.archive.ubuntu.com/ubuntu/ bionic-updates universe
# deb-src http://gb.archive.ubuntu.com/ubuntu/ bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ bionic multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ bionic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu bionic partner
# deb-src http://archive.canonical.com/ubuntu bionic partner

deb http://security.ubuntu.com/ubuntu bionic-security main restricted
# deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
deb http://security.ubuntu.com/ubuntu bionic-security universe
# deb-src http://security.ubuntu.com/ubuntu bionic-security universe
deb http://security.ubuntu.com/ubuntu bionic-security multiverse
# deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse
sudo apt-get update

deb http://downloads.sourceforge.net/project/xenlism-wildfire/repo deb/
keith@keith-Desktop:~$
``` 

As I say I am a little rusty! I hope i have provided you with whats needed and in the correct manner.

I am guessing that the last entry is what has caused this 

Thank you for your quick reply

---

### Post by sisco311 on 2018-07-31
Somehow you managed to add the `**sudo apt-get update**' line to the file which is causing your problems. Delete it and you should be fine.

---

### Post by Frogster on 2018-07-31
Thank you for your help and spotting that.

How do I get around it being a read only file? I seem to recall using gedit in the past to open and amend but cant for the life of me remember how to alter the permissions?

Many thanks

---

### Post by sisco311 on 2018-07-31
You have to edit the file as root. There are many ways to accomplish this.

In Ubuntu 18.04, I would try the latest method:
```
gedit admin:///etc/apt/sources.list
```

But you can use the good old `sudo'  command as well:```
sudo -H gedit /etc/apt/sources.list
```

---

### Post by Frogster on 2018-07-31
Thank you so much. Your help and patience is greatly appreciated.

I went with the "sudo" option and all now seems fine.

It has been a wake up call and reminder of how far Ubuntu has come since 2007

---

### Post by sisco311 on 2018-07-31
It was my pleasure.

Happy Ubuntuing. :)

---

