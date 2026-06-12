---
title: "Synaptic Package Manager Crash"
date: 2008-06-07
forum: General Help
---

### Post by miteshanand1729 on 2008-06-07
Today I install Alien Arena Game in Ububtu 8.04.After installation my Synaptic Package Manage crash every time and i m unable to update anything.When i try to update via Terminal it give following Error...

mitesh@Mitesh-Desktop:~$ sudo apt-get update
[sudo] password for mitesh: 
Hit [http://mirrors.nic.funet.fi](http://mirrors.nic.funet.fi) hardy Release.gpg
Ign [http://mirrors.nic.funet.fi](http://mirrors.nic.funet.fi) hardy/main Translation-en_IN
Ign [http://mirrors.nic.funet.fi](http://mirrors.nic.funet.fi) hardy/restricted Translation-en_IN
Ign [http://mirrors.nic.funet.fi](http://mirrors.nic.funet.fi) hardy/universe Translation-en_IN
Ign [http://mirrors.nic.funet.fi](http://mirrors.nic.funet.fi) hardy/multiverse Translation-en_IN
Hit [http://mirrors.nic.funet.fi](http://mirrors.nic.funet.fi) hardy-updates Release.gpg
Ign [http://mirrors.nic.funet.fi](http://mirrors.nic.funet.fi) hardy-updates/main Translation-en_IN
Ign [http://mirrors.nic.funet.fi](http://mirrors.nic.funet.fi) hardy-updates/restricted Translation-en_IN
Ign [http://mirrors.nic.funet.fi](http://mirrors.nic.funet.fi) hardy-updates/universe Translation-en_IN
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_IN
Ign [http://mirrors.nic.funet.fi](http://mirrors.nic.funet.fi) hardy-updates/multiverse Translation-en_IN
Hit [http://mirrors.nic.funet.fi](http://mirrors.nic.funet.fi) hardy-security Release.gpg
Ign [http://mirrors.nic.funet.fi](http://mirrors.nic.funet.fi) hardy-security/main Translation-en_IN
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release 
Ign [http://mirrors.nic.funet.fi](http://mirrors.nic.funet.fi) hardy-security/restricted Translation-en_IN
Ign [http://mirrors.nic.funet.fi](http://mirrors.nic.funet.fi) hardy-security/universe Translation-en_IN
Ign [http://mirrors.nic.funet.fi](http://mirrors.nic.funet.fi) hardy-security/multiverse Translation-en_IN
Hit [http://mirrors.nic.funet.fi](http://mirrors.nic.funet.fi) hardy Release
Hit [http://mirrors.nic.funet.fi](http://mirrors.nic.funet.fi) hardy-updates Release
Hit [http://mirrors.nic.funet.fi](http://mirrors.nic.funet.fi) hardy-security Release              
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages             
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources
Hit [http://mirrors.nic.funet.fi](http://mirrors.nic.funet.fi) hardy/main Packages
Hit [http://mirrors.nic.funet.fi](http://mirrors.nic.funet.fi) hardy/restricted Packages
Hit [http://mirrors.nic.funet.fi](http://mirrors.nic.funet.fi) hardy/universe Packages
Hit [http://mirrors.nic.funet.fi](http://mirrors.nic.funet.fi) hardy/multiverse Packages
Hit [http://mirrors.nic.funet.fi](http://mirrors.nic.funet.fi) hardy-updates/main Packages
Hit [http://mirrors.nic.funet.fi](http://mirrors.nic.funet.fi) hardy-updates/restricted Packages
Hit [http://mirrors.nic.funet.fi](http://mirrors.nic.funet.fi) hardy-updates/universe Packages
Hit [http://mirrors.nic.funet.fi](http://mirrors.nic.funet.fi) hardy-updates/multiverse Packages
Hit [http://mirrors.nic.funet.fi](http://mirrors.nic.funet.fi) hardy-security/main Packages
Hit [http://mirrors.nic.funet.fi](http://mirrors.nic.funet.fi) hardy-security/restricted Packages
Hit [http://mirrors.nic.funet.fi](http://mirrors.nic.funet.fi) hardy-security/universe Packages
Hit [http://mirrors.nic.funet.fi](http://mirrors.nic.funet.fi) hardy-security/multiverse Packages
Reading package lists... Done
mitesh@Mitesh-Desktop:~$ sudo apt-get upgrade
Reading package lists... Done
**_Segmentation faulty tree... 50%_**
mitesh@Mitesh-Desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
**_Segmentation faulty tree... 50%_**


What is this .??? Help please...??

---

### Post by LoneWolfJack on 2008-06-07
Take a look here and let us know if it solved your problem:

[http://ubuntuforums.org/showthread.php?t=60499]("http://ubuntuforums.org/showthread.php?t=60499")

---

### Post by Nikitas350 on 2008-06-07
Open /etc/apt/sources.list and post it here. You can also see this [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by miteshanand1729 on 2008-06-07
> **Nikitas350 said:**
> Open /etc/apt/sources.list and post it here. You can also see this [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)
Here is my sources.list...

mitesh@Mitesh-Desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mirrors.nic.funet.fi/ubuntu/](http://mirrors.nic.funet.fi/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirrors.nic.funet.fi/ubuntu/](http://mirrors.nic.funet.fi/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://mirrors.nic.funet.fi/ubuntu/](http://mirrors.nic.funet.fi/ubuntu/) hardy universe
deb [http://mirrors.nic.funet.fi/ubuntu/](http://mirrors.nic.funet.fi/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirrors.nic.funet.fi/ubuntu/](http://mirrors.nic.funet.fi/ubuntu/) hardy multiverse
deb [http://mirrors.nic.funet.fi/ubuntu/](http://mirrors.nic.funet.fi/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://mirrors.nic.funet.fi/ubuntu/](http://mirrors.nic.funet.fi/ubuntu/) hardy-security main restricted
deb [http://mirrors.nic.funet.fi/ubuntu/](http://mirrors.nic.funet.fi/ubuntu/) hardy-security universe
deb [http://mirrors.nic.funet.fi/ubuntu/](http://mirrors.nic.funet.fi/ubuntu/) hardy-security multiverse
mitesh@Mitesh-Desktop:~$

---

### Post by Nikitas350 on 2008-06-07
Try changing it with the default one (run gksudo gedit /etc/apt/sources.list):

-----START---- (do not include this line)
# 
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---END----(do not include this line)

Then run sudo apt-get update

---

### Post by miteshanand1729 on 2008-06-07
Thanx.. Problem solved... Now i m able to use Synaptic Package Manager..

---

