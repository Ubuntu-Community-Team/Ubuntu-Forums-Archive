---
title: "package manager broken after trying to install maya on ubuntu"
date: 2021-05-21
forum: General Help
---

### Post by wakagashira893 on 2021-05-21
apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libc6 : Recommends: libnss-nis but it is not installable
         Recommends: libnss-nisplus but it is not installable
         Breaks: libc6:i386 (!= 2.31-12) but 2.31-0ubuntu9.2 is installed
 libc6:i386 : Breaks: libc6 (!= 2.31-0ubuntu9.2) but 2.31-12 is installed
 libc6-dbg : Depends: libc6 (= 2.31-0ubuntu9.2) but 2.31-12 is installed
 libc6-dev : Depends: libc6 (= 2.31-0ubuntu9.2) but 2.31-12 is installed
 libc6-i386 : Depends: libc6 (= 2.31-0ubuntu9.2) but 2.31-12 is installed
 libhogweed4 : Depends: libnettle6 (= 3.4.1-1) but it is not installable
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).


i have tried many things yet no success, can someone help me with this? 

this is the first time i broke ubuntu like this, can i fix this? or do i need to reinstall?

---

### Post by guiverc on 2021-05-21
You haven't provided your release, but picking a package

 ```
libc6 | 2.31-0ubuntu9     | focal            | amd64, arm64, armhf, i386, ppc64el, riscv64, s390x
libc6 | 2.31-0ubuntu9.2   | focal-updates    | amd64, arm64, armhf, i386, ppc64el, riscv64, s390x
```

it looks like you're using *focal* or 20.04, but have added 3rd party repositories, as 2.31-12 is not a Ubuntu package for 20.04/*focal*. I would `apt-cache policy libc6` and explore your sources to see what 3rd party sources you've added that have created the issue.

I did a `rmadison libnettle6` (CLI version of [https://packages.ubuntu.com/search?keywords=libnettle6&searchon=names&suite=all&section=all](https://packages.ubuntu.com/search?keywords=libnettle6&searchon=names&suite=all&section=all)) and looked up libnettle6 and it looks like it wants a 3rd party package, but the package is old (for *bionic possibly*) so providing your release is a start.  Again I'd `apt-cache policy` explore where you're getting packages from (an `sudo apt update` will tell you) and check they are appropriate (*safe, secure, maintained* etc) for your *unstated* release.

You shouldn't need to re-install; I'd likely reverse what you've done to make the mess.. you have your command `history`, apt logs & you know your Ubuntu release and can view your sources... (*details we don't have*)

---

### Post by wakagashira893 on 2021-05-21
lsb_release -a
LSB Version:	core-11.1.0ubuntu2-noarch:security-11.1.0ubuntu2-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 20.04.2 LTS
Release:	20.04
Codename:	focal

---

### Post by wakagashira893 on 2021-05-21
> **guiverc said:**
> You haven't provided your release, but picking a package

 ```
libc6 | 2.31-0ubuntu9     | focal            | amd64, arm64, armhf, i386, ppc64el, riscv64, s390x
libc6 | 2.31-0ubuntu9.2   | focal-updates    | amd64, arm64, armhf, i386, ppc64el, riscv64, s390x
```

it looks like you're using *focal* or 20.04, but have added 3rd party repositories, as 2.31-12 is not a Ubuntu package for 20.04/*focal*. I would `apt-cache policy libc6` and explore your sources to see what 3rd party sources you've added that have created the issue.

I did a `rmadison libnettle6` (CLI version of [https://packages.ubuntu.com/search?keywords=libnettle6&searchon=names&suite=all&section=all](https://packages.ubuntu.com/search?keywords=libnettle6&searchon=names&suite=all&section=all)) and looked up libnettle6 and it looks like it wants a 3rd party package, but the package is old (for *bionic possibly*) so providing your release is a start.  Again I'd `apt-cache policy` explore where you're getting packages from (an `sudo apt update` will tell you) and check they are appropriate (*safe, secure, maintained* etc) for your *unstated* release.

You shouldn't need to re-install; I'd likely reverse what you've done to make the mess.. you have your command `history`, apt logs & you know your Ubuntu release and can view your sources... (*details we don't have*)


would you like a bash history?

---

### Post by foxcbland on 2021-05-22
First result searching

[https://linuxhint.com/install_autodesk_maya_ubuntu/](https://linuxhint.com/install_autodesk_maya_ubuntu/)

---

### Post by wakagashira893 on 2021-05-22
> **foxcbland said:**
> First result searching

[https://linuxhint.com/install_autodesk_maya_ubuntu/](https://linuxhint.com/install_autodesk_maya_ubuntu/)


tried it, doesn't work

---

### Post by wakagashira893 on 2021-05-22
bump

---

### Post by ajgreeny on 2021-05-22
Where did you get your maya package?

It is not available in the standard repos so you must have enabled a third party repo, as suggested by **guiverc**, or downloaded it from somewhere, perhaps as a .deb package.

---

### Post by wakagashira893 on 2021-05-22
i downloaded it from the software creators at autodesk

---

### Post by deadflowr on 2021-05-22
Some of your problem packages don't exist in Ubuntu 20.04.
What repositories have been added?
Perhaps following guiverc's suggestion look at what
```
apt-cache policy libc6 libnss-nis libnss-nisplus libhogweed4 libnettle6
```
That should give some idea of where things are from.

Also, apt logs are at /var/log/apt.
look into the history.log files.
(and any subsequent history.log.gz archive files, if any, as sometimes the affected apt logs may have already been archived)

---

### Post by wakagashira893 on 2021-05-22
> **ajgreeny said:**
> Where did you get your maya package?

It is not available in the standard repos so you must have enabled a third party repo, as suggested by **guiverc**, or downloaded it from somewhere, perhaps as a .deb package.

from autodesk

---

### Post by wakagashira893 on 2021-05-22
> **deadflowr said:**
> Some of your problem packages don't exist in Ubuntu 20.04.
What repositories have been added?
Perhaps following guiverc's suggestion look at what
```
apt-cache policy libc6 libnss-nis libnss-nisplus libhogweed4 libnettle6
```
That should give some idea of where things are from.

Also, apt logs are at /var/log/apt.
look into the history.log files.
(and any subsequent history.log.gz archive files, if any, as sometimes the affected apt logs may have already been archived)

[ATTACH=CONFIG]288527[/ATTACH]

---

### Post by wakagashira893 on 2021-05-22
> **guiverc said:**
> You haven't provided your release, but picking a package

 ```
libc6 | 2.31-0ubuntu9     | focal            | amd64, arm64, armhf, i386, ppc64el, riscv64, s390x
libc6 | 2.31-0ubuntu9.2   | focal-updates    | amd64, arm64, armhf, i386, ppc64el, riscv64, s390x
```

it looks like you're using *focal* or 20.04, but have added 3rd party repositories, as 2.31-12 is not a Ubuntu package for 20.04/*focal*. I would `apt-cache policy libc6` and explore your sources to see what 3rd party sources you've added that have created the issue.

I did a `rmadison libnettle6` (CLI version of [https://packages.ubuntu.com/search?keywords=libnettle6&searchon=names&suite=all&section=all](https://packages.ubuntu.com/search?keywords=libnettle6&searchon=names&suite=all&section=all)) and looked up libnettle6 and it looks like it wants a 3rd party package, but the package is old (for *bionic possibly*) so providing your release is a start.  Again I'd `apt-cache policy` explore where you're getting packages from (an `sudo apt update` will tell you) and check they are appropriate (*safe, secure, maintained* etc) for your *unstated* release.

You shouldn't need to re-install; I'd likely reverse what you've done to make the mess.. you have your command `history`, apt logs & you know your Ubuntu release and can view your sources... (*details we don't have*)


would really like your help man, nobody seems to know how to fix this here... really would hate to have to format and start over.

---

### Post by wakagashira893 on 2021-05-24
bump

---

### Post by wakagashira893 on 2021-05-25
bump

---

### Post by deadflowr on 2021-05-25
You never posted what repositories have been added or removed.

---

### Post by grahammechanical on 2021-05-25
Here is something I have noticed. When I run lsb_release -a I get "No LSB modules are available." But when you run lsb_release -a you get

> LSB Version:    core-11.1.0ubuntu2-noarch:security-11.1.0ubuntu2-noarch

Until I looked it up I do not know what "lsb" was. Even now I am not sure that I understand it. I think that you have installed a lsb module that has altered the file system layout.

Information on Linux Standard Base

[https://en.wikipedia.org/wiki/Linux_Standard_Base](https://en.wikipedia.org/wiki/Linux_Standard_Base)

Information of the LSB module that is installed on your system.

[https://ubuntu.pkgs.org/20.04/ubuntu-universe-arm64/lsb-core_11.1.0ubuntu2_arm64.deb.html](https://ubuntu.pkgs.org/20.04/ubuntu-universe-arm64/lsb-core_11.1.0ubuntu2_arm64.deb.html)

I may be wrong about this. But it is a deviation from the standard Ubuntu that most of us are familiar with.

Regards

---

### Post by wakagashira893 on 2021-05-26
> **grahammechanical said:**
> Here is something I have noticed. When I run lsb_release -a I get "No LSB modules are available." But when you run lsb_release -a you get



Until I looked it up I do not know what "lsb" was. Even now I am not sure that I understand it. I think that you have installed a lsb module that has altered the file system layout.

Information on Linux Standard Base

[https://en.wikipedia.org/wiki/Linux_Standard_Base](https://en.wikipedia.org/wiki/Linux_Standard_Base)

Information of the LSB module that is installed on your system.

[https://ubuntu.pkgs.org/20.04/ubuntu-universe-arm64/lsb-core_11.1.0ubuntu2_arm64.deb.html](https://ubuntu.pkgs.org/20.04/ubuntu-universe-arm64/lsb-core_11.1.0ubuntu2_arm64.deb.html)

I may be wrong about this. But it is a deviation from the standard Ubuntu that most of us are familiar with.

Regards

is there a way to fix this?

---

### Post by Impavidus on 2021-05-27
> **grahammechanical said:**
> Here is something I have noticed. When I run lsb_release -a I get "No LSB modules are available." But when you run lsb_release -a you get

Until I looked it up I do not know what "lsb" was. Even now I am not sure that I understand it. I think that you have installed a lsb module that has altered the file system layout.

I don't think that's something to worry about. On my box I get```
$ lsb_release -a
LSB Version:    core-11.1.0ubuntu2-noarch:printing-11.1.0ubuntu2-noarch:security-11.1.0ubuntu2-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 20.10
Release:    20.10
Codename:    groovy
```This simply results from installing lsb from the official repositories. It's not installed by default, but some third-party .debs depend on it (in my case Google Earth).

@wakagashira893: You somehow got a strange version of libc6 installed and have no repository for it. It would be nice to know why it's there. It may be possible to tell the package manager to downgrade it to the official version.

---

### Post by wakagashira893 on 2021-05-27
> **Impavidus said:**
> I don't think that's something to worry about. On my box I get```
$ lsb_release -a
LSB Version:    core-11.1.0ubuntu2-noarch:printing-11.1.0ubuntu2-noarch:security-11.1.0ubuntu2-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 20.10
Release:    20.10
Codename:    groovy
```This simply results from installing lsb from the official repositories. It's not installed by default, but some third-party .debs depend on it (in my case Google Earth).

@wakagashira893: You somehow got a strange version of libc6 installed and have no repository for it. It would be nice to know why it's thre. It may be possible to tell the package manager to downgrade it to the official version.


save me please, i'll show you whatever you need to be shown

---

### Post by wakagashira893 on 2021-05-28
bump

---

### Post by wakagashira893 on 2021-05-28
bump

---

### Post by Impavidus on 2021-05-29
We've still no idea of what may be going wrong, but you might try downgrading libc6 to the official version:```
sudo apt reinstall libc6=2.31-0ubuntu9.2
```Maybe it works, maybe not.

---

### Post by monkeybrain20122 on 2021-05-29
Some third party software is very badly packaged or may depends on wrong versions of libs. Did you download a .deb or add a repository? If the former you may be able to run it locally like so: extract the deb and look whether there is a startup script or something in the bin folder and then change the LD_LIBRARY_PATH to somewhere in your $HOME, where you can download the proper version of the libs needed without installing (or alternatively you may change the version of libs to versions installable and still be able to run it). I tried it with some third party software which provides broken .debs and it works,  but I can't give more info since I can't test it with a maya deb.

EDITED: Well I tried to get the free trial version to see what is inside the .deb and check if can be run locally, it is ridiculous that they ask for so much personal information and want proof for all of that (just for a free trial). I won't buy anything from it even if I have the money,

---

### Post by SeijiSensei on 2021-05-29
Often third-party binary packages depend on a specific set of libraries, meaning it only works correctly on a particular Ubuntu release. What does Autodesk say about the compatibility of its binary and Ubuntu? Maybe it would work on 18.04 but not later releases?

If you have any experience with virtual machines, I'd use KVM or Virtualbox to create a virtual 18.04 machine. Then try the download there.

---

### Post by wakagashira893 on 2021-05-30
> **Impavidus said:**
> We've still no idea of what may be going wrong, but you might try downgrading libc6 to the official version:```
sudo apt reinstall libc6=2.31-0ubuntu9.2
```Maybe it works, maybe not.



sudo apt reinstall libc6=2.31-0ubuntu9.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libhogweed4 : Depends: libnettle6 (= 3.4.1-1) but it is not installable
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

---

### Post by Yellow Pasque on 2021-05-30
```
cat /etc/apt/sources.list.d/*
```

And please use code tags in the response instead of changing colors/fonts. Your last post is unreadable unless I highlight it.

---

### Post by wakagashira893 on 2021-05-30
> **Yellow Pasque said:**
> ```
cat /etc/apt/sources.list.d/*
```

And please use code tags in the response instead of changing colors/fonts. Your last post is unreadable unless I highlight it.


```
# deb [http://ppa.launchpad.net/darklin20/bomi/ubuntu](http://ppa.launchpad.net/darklin20/bomi/ubuntu) bionic main
# deb-src [http://ppa.launchpad.net/darklin20/bomi/ubuntu](http://ppa.launchpad.net/darklin20/bomi/ubuntu) bionic main
# deb [http://ppa.launchpad.net/darklin20/bomi/ubuntu](http://ppa.launchpad.net/darklin20/bomi/ubuntu) bionic main
# deb-src [http://ppa.launchpad.net/darklin20/bomi/ubuntu](http://ppa.launchpad.net/darklin20/bomi/ubuntu) bionic main
# deb [http://ppa.launchpad.net/darklin20/bomi/ubuntu](http://ppa.launchpad.net/darklin20/bomi/ubuntu) bionic main
# deb-src [http://ppa.launchpad.net/darklin20/bomi/ubuntu](http://ppa.launchpad.net/darklin20/bomi/ubuntu) bionic main
# deb [http://ppa.launchpad.net/enlightenment-git/ppa/ubuntu](http://ppa.launchpad.net/enlightenment-git/ppa/ubuntu) bionic main
# deb-src [http://ppa.launchpad.net/enlightenment-git/ppa/ubuntu](http://ppa.launchpad.net/enlightenment-git/ppa/ubuntu) bionic main
# deb [http://ppa.launchpad.net/enlightenment-git/ppa/ubuntu](http://ppa.launchpad.net/enlightenment-git/ppa/ubuntu) bionic main
# deb-src [http://ppa.launchpad.net/enlightenment-git/ppa/ubuntu](http://ppa.launchpad.net/enlightenment-git/ppa/ubuntu) bionic main
# deb [http://ppa.launchpad.net/enlightenment-git/ppa/ubuntu](http://ppa.launchpad.net/enlightenment-git/ppa/ubuntu) bionic main
# deb-src [http://ppa.launchpad.net/enlightenment-git/ppa/ubuntu](http://ppa.launchpad.net/enlightenment-git/ppa/ubuntu) bionic main
# deb [http://ppa.launchpad.net/exmplayer-dev/exmplayer/ubuntu](http://ppa.launchpad.net/exmplayer-dev/exmplayer/ubuntu) focal main
# deb-src [http://ppa.launchpad.net/exmplayer-dev/exmplayer/ubuntu](http://ppa.launchpad.net/exmplayer-dev/exmplayer/ubuntu) focal main
# deb [http://ppa.launchpad.net/exmplayer-dev/exmplayer/ubuntu](http://ppa.launchpad.net/exmplayer-dev/exmplayer/ubuntu) focal main
# deb-src [http://ppa.launchpad.net/exmplayer-dev/exmplayer/ubuntu](http://ppa.launchpad.net/exmplayer-dev/exmplayer/ubuntu) focal main
# deb [http://ppa.launchpad.net/exmplayer-dev/exmplayer-qt5/ubuntu](http://ppa.launchpad.net/exmplayer-dev/exmplayer-qt5/ubuntu) focal main
# deb-src [http://ppa.launchpad.net/exmplayer-dev/exmplayer-qt5/ubuntu](http://ppa.launchpad.net/exmplayer-dev/exmplayer-qt5/ubuntu) focal main
# deb [http://ppa.launchpad.net/exmplayer-dev/exmplayer-qt5/ubuntu](http://ppa.launchpad.net/exmplayer-dev/exmplayer-qt5/ubuntu) focal main
# deb-src [http://ppa.launchpad.net/exmplayer-dev/exmplayer-qt5/ubuntu](http://ppa.launchpad.net/exmplayer-dev/exmplayer-qt5/ubuntu) focal main
# deb [http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu](http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu) eoan main # disabled on upgrade to eoan
# deb-src [http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu](http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu) disco main
# deb [http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu](http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu) eoan main # disabled on upgrade to eoan
# deb-src [http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu](http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu) disco main
# deb [http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu](http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu) eoan main # disabled on upgrade to eoan
# deb-src [http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu](http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu) disco main
# deb [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) cosmic main # disabled on upgrade to cosmic
# deb-src [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) bionic main
# deb [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) cosmic main # disabled on upgrade to cosmic
# deb-src [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) bionic main
# deb [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) cosmic main # disabled on upgrade to cosmic
# deb-src [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) bionic main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
# deb [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) cosmic main # disabled on upgrade to cosmic
# deb-src [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) bionic main
# deb-src [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) bionic main
# deb [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) cosmic main # disabled on upgrade to cosmic
# deb-src [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) bionic main
# deb-src [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) bionic main
# deb [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) cosmic main # disabled on upgrade to cosmic
# deb-src [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) bionic main
# deb-src [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) bionic main
# deb [http://ppa.launchpad.net/iconnor/zoneminder-1.32/ubuntu](http://ppa.launchpad.net/iconnor/zoneminder-1.32/ubuntu) eoan main # disabled on upgrade to eoan
# deb-src [http://ppa.launchpad.net/iconnor/zoneminder-1.32/ubuntu](http://ppa.launchpad.net/iconnor/zoneminder-1.32/ubuntu) disco main
# deb [http://ppa.launchpad.net/iconnor/zoneminder-1.32/ubuntu](http://ppa.launchpad.net/iconnor/zoneminder-1.32/ubuntu) eoan main # disabled on upgrade to eoan
# deb-src [http://ppa.launchpad.net/iconnor/zoneminder-1.32/ubuntu](http://ppa.launchpad.net/iconnor/zoneminder-1.32/ubuntu) disco main
# deb [http://ppa.launchpad.net/iconnor/zoneminder-1.32/ubuntu](http://ppa.launchpad.net/iconnor/zoneminder-1.32/ubuntu) eoan main # disabled on upgrade to eoan
# deb-src [http://ppa.launchpad.net/iconnor/zoneminder-1.32/ubuntu](http://ppa.launchpad.net/iconnor/zoneminder-1.32/ubuntu) disco main
# deb [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) cosmic main
# deb-src [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) cosmic main
# deb [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) cosmic main
# deb-src [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) cosmic main
# deb [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) cosmic main
# deb-src [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) cosmic main
# deb [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) cosmic main
# deb-src [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) cosmic main
# deb [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) cosmic main
# deb-src [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) cosmic main
# deb [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) cosmic main
# deb-src [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu) cosmic main
# deb [http://ppa.launchpad.net/lightzone-team/lightzone/ubuntu](http://ppa.launchpad.net/lightzone-team/lightzone/ubuntu) cosmic main # disabled on upgrade to cosmic
# deb-src [http://ppa.launchpad.net/lightzone-team/lightzone/ubuntu](http://ppa.launchpad.net/lightzone-team/lightzone/ubuntu) bionic main
# deb [http://ppa.launchpad.net/lightzone-team/lightzone/ubuntu](http://ppa.launchpad.net/lightzone-team/lightzone/ubuntu) cosmic main # disabled on upgrade to cosmic
# deb-src [http://ppa.launchpad.net/lightzone-team/lightzone/ubuntu](http://ppa.launchpad.net/lightzone-team/lightzone/ubuntu) bionic main
# deb [http://ppa.launchpad.net/lightzone-team/lightzone/ubuntu](http://ppa.launchpad.net/lightzone-team/lightzone/ubuntu) cosmic main # disabled on upgrade to cosmic
# deb-src [http://ppa.launchpad.net/lightzone-team/lightzone/ubuntu](http://ppa.launchpad.net/lightzone-team/lightzone/ubuntu) bionic main
# deb [http://ppa.launchpad.net/mc3man/mpv-tests/ubuntu](http://ppa.launchpad.net/mc3man/mpv-tests/ubuntu) cosmic main # disabled on upgrade to cosmic
# deb-src [http://ppa.launchpad.net/mc3man/mpv-tests/ubuntu](http://ppa.launchpad.net/mc3man/mpv-tests/ubuntu) bionic main
# deb [http://ppa.launchpad.net/mc3man/mpv-tests/ubuntu](http://ppa.launchpad.net/mc3man/mpv-tests/ubuntu) cosmic main # disabled on upgrade to cosmic
# deb-src [http://ppa.launchpad.net/mc3man/mpv-tests/ubuntu](http://ppa.launchpad.net/mc3man/mpv-tests/ubuntu) bionic main
# deb [http://ppa.launchpad.net/mc3man/mpv-tests/ubuntu](http://ppa.launchpad.net/mc3man/mpv-tests/ubuntu) cosmic main # disabled on upgrade to cosmic
# deb-src [http://ppa.launchpad.net/mc3man/mpv-tests/ubuntu](http://ppa.launchpad.net/mc3man/mpv-tests/ubuntu) bionic main
# deb [http://ppa.launchpad.net/midori/ppa/ubuntu](http://ppa.launchpad.net/midori/ppa/ubuntu) cosmic main
# deb-src [http://ppa.launchpad.net/midori/ppa/ubuntu](http://ppa.launchpad.net/midori/ppa/ubuntu) cosmic main
# deb [http://ppa.launchpad.net/midori/ppa/ubuntu](http://ppa.launchpad.net/midori/ppa/ubuntu) cosmic main
# deb-src [http://ppa.launchpad.net/midori/ppa/ubuntu](http://ppa.launchpad.net/midori/ppa/ubuntu) cosmic main
# deb [http://ppa.launchpad.net/midori/ppa/ubuntu](http://ppa.launchpad.net/midori/ppa/ubuntu) cosmic main
# deb-src [http://ppa.launchpad.net/midori/ppa/ubuntu](http://ppa.launchpad.net/midori/ppa/ubuntu) cosmic main
# When enabling this repo please remember to add the PlexPublic.Key into the apt setup.
# wget -q [https://downloads.plex.tv/plex-keys/PlexSign.key](https://downloads.plex.tv/plex-keys/PlexSign.key) -O - | sudo apt-key add -
# deb [https://downloads.plex.tv/repo/deb/](https://downloads.plex.tv/repo/deb/) public main
# When enabling this repo please remember to add the PlexPublic.Key into the apt setup.
# wget -q [https://downloads.plex.tv/plex-keys/PlexSign.key](https://downloads.plex.tv/plex-keys/PlexSign.key) -O - | sudo apt-key add -
# deb [https://downloads.plex.tv/repo/deb/](https://downloads.plex.tv/repo/deb/) public main
# When enabling this repo please remember to add the PlexPublic.Key into the apt setup.
# wget -q [https://downloads.plex.tv/plex-keys/PlexSign.key](https://downloads.plex.tv/plex-keys/PlexSign.key) -O - | sudo apt-key add -
# deb [https://downloads.plex.tv/repo/deb/](https://downloads.plex.tv/repo/deb/) public main
# deb [http://ppa.launchpad.net/saiarcot895/chromium-beta/ubuntu](http://ppa.launchpad.net/saiarcot895/chromium-beta/ubuntu) eoan main # disabled on upgrade to eoan
# deb-src [http://ppa.launchpad.net/saiarcot895/chromium-beta/ubuntu](http://ppa.launchpad.net/saiarcot895/chromium-beta/ubuntu) disco main
# deb [http://ppa.launchpad.net/saiarcot895/chromium-beta/ubuntu](http://ppa.launchpad.net/saiarcot895/chromium-beta/ubuntu) eoan main # disabled on upgrade to eoan
# deb-src [http://ppa.launchpad.net/saiarcot895/chromium-beta/ubuntu](http://ppa.launchpad.net/saiarcot895/chromium-beta/ubuntu) disco main
# deb [http://ppa.launchpad.net/saiarcot895/chromium-beta/ubuntu](http://ppa.launchpad.net/saiarcot895/chromium-beta/ubuntu) eoan main # disabled on upgrade to eoan
# deb-src [http://ppa.launchpad.net/saiarcot895/chromium-beta/ubuntu](http://ppa.launchpad.net/saiarcot895/chromium-beta/ubuntu) disco main
# deb [http://ppa.launchpad.net/sview/stable/ubuntu](http://ppa.launchpad.net/sview/stable/ubuntu) focal main
# deb-src [http://ppa.launchpad.net/sview/stable/ubuntu](http://ppa.launchpad.net/sview/stable/ubuntu) focal main
# deb [http://ppa.launchpad.net/sview/stable/ubuntu](http://ppa.launchpad.net/sview/stable/ubuntu) focal main
# deb-src [http://ppa.launchpad.net/sview/stable/ubuntu](http://ppa.launchpad.net/sview/stable/ubuntu) focal main
# deb [http://ppa.launchpad.net/umang/indicator-stickynotes/ubuntu](http://ppa.launchpad.net/umang/indicator-stickynotes/ubuntu) disco main # disabled on upgrade to disco
# deb-src [http://ppa.launchpad.net/umang/indicator-stickynotes/ubuntu](http://ppa.launchpad.net/umang/indicator-stickynotes/ubuntu) cosmic main
# deb [http://ppa.launchpad.net/umang/indicator-stickynotes/ubuntu](http://ppa.launchpad.net/umang/indicator-stickynotes/ubuntu) disco main # disabled on upgrade to disco
# deb-src [http://ppa.launchpad.net/umang/indicator-stickynotes/ubuntu](http://ppa.launchpad.net/umang/indicator-stickynotes/ubuntu) cosmic main
# deb [http://ppa.launchpad.net/umang/indicator-stickynotes/ubuntu](http://ppa.launchpad.net/umang/indicator-stickynotes/ubuntu) disco main # disabled on upgrade to disco
# deb-src [http://ppa.launchpad.net/umang/indicator-stickynotes/ubuntu](http://ppa.launchpad.net/umang/indicator-stickynotes/ubuntu) cosmic main
# deb [http://ppa.launchpad.net/webupd8team/atom/ubuntu](http://ppa.launchpad.net/webupd8team/atom/ubuntu) cosmic main
# deb-src [http://ppa.launchpad.net/webupd8team/atom/ubuntu](http://ppa.launchpad.net/webupd8team/atom/ubuntu) cosmic main
# deb [http://ppa.launchpad.net/webupd8team/atom/ubuntu](http://ppa.launchpad.net/webupd8team/atom/ubuntu) cosmic main
# deb-src [http://ppa.launchpad.net/webupd8team/atom/ubuntu](http://ppa.launchpad.net/webupd8team/atom/ubuntu) cosmic main
# deb [http://ppa.launchpad.net/webupd8team/atom/ubuntu](http://ppa.launchpad.net/webupd8team/atom/ubuntu) cosmic main
# deb-src [http://ppa.launchpad.net/webupd8team/atom/ubuntu](http://ppa.launchpad.net/webupd8team/atom/ubuntu) cosmic main
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main restricted universe multiverse
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main restricted universe multiverse
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main restricted universe multiverse
/home/akira#
```

---

### Post by wakagashira893 on 2021-05-30
sigh... forget it. i'll install the newest version. 

thank you everyone for your time and energy. lesson learned lmao

---

