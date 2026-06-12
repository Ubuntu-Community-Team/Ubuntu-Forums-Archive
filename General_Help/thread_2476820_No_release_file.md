---
title: "No release file"
date: 2022-07-08
forum: General Help
---

### Post by jgw on 2022-07-08
I got the following on a "sudo apt update", did what it said but there was nothing on creating a release file.  I think I have to do that but have no idea how.
 
The repository 'https://download.mono-project.com/repo/ubuntu>https://download.mono-project.com/repo/ubuntu</a> stable-bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

Thank you............

---

### Post by Holger_Gehrke on 2022-07-08
The file "Release" is a file on the server. If apt complains about not finding it, then either the server doesn't have any files for your release of Ubuntu or there is a typo in your '/etc/apt/sources.list' or in the file for the repo in '/etc/apt/sources.list.d/'.

Holger

---

### Post by jgw on 2022-07-09
Thank you for the reply.

Below is /etc/apt/sources.list   I think this is the culprit but am not sure (towards the end of the file).  Could you tell me if removing the # from in front of these things might fix it and which ones to do as I am ignorant on this.

Thank you...........

[HTML]# deb cdrom:[Ubuntu 20.04.4 LTS _Focal Fossa_ - Release amd64 (20220223)]/ focal main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ focal main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ focal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ focal-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ focal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ focal universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ focal universe
deb http://us.archive.ubuntu.com/ubuntu/ focal-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ focal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ focal multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ focal multiverse
deb http://us.archive.ubuntu.com/ubuntu/ focal-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ focal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu focal partner
# deb-src http://archive.canonical.com/ubuntu focal partner

deb http://security.ubuntu.com/ubuntu focal-security main restricted
# deb-src http://security.ubuntu.com/ubuntu focal-security main restricted
deb http://security.ubuntu.com/ubuntu focal-security universe
# deb-src http://security.ubuntu.com/ubuntu focal-security universe
deb http://security.ubuntu.com/ubuntu focal-security multiverse
# deb-src http://security.ubuntu.com/ubuntu focal-security multiverse

# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,
# see the sources.list(5) manual.
# deb <a href="https://download.mono-project.com/repo/ubuntu">https://download.mono-project.com/repo/ubuntu</a> stable-bionic main
# deb-src <a href="https://download.mono-project.com/repo/ubuntu">https://download.mono-project.com/repo/ubuntu</a> stable-bionic main
deb "https://download.mono-project.com/repo/ubuntu">https://download.mono-project.com/repo/ubuntu</a> stable-bionic main
# deb-src "https://download.mono-project.com/repo/ubuntu">https://download.mono-project.com/repo/ubuntu</a> stable-bionic main
# deb "https://download.mono-project.com/repo/ubuntu stable-bionic main
# deb-src "https://download.mono-project.com/repo/ubuntu stable-bionic main
deb https://download.mono-project.com/repo/ubuntu stable-focal main
# deb-src https://download.mono-project.com/repo/ubuntu stable-focal main[/HTML]

---

### Post by deadflowr on 2022-07-09
Try removing what I've bolded below from your output.
```
# deb **<a href="https://download.mono-project.com/repo/ubuntu">**https://download.mono-project.com/repo/ubuntu**</a>** stable-bionic main
# deb-src **<a href="https://download.mono-project.com/repo/ubuntu">**https://download.mono-project.com/repo/ubuntu**</a>** stable-bionic main
deb **"https://download.mono-project.com/repo/ubuntu">**https://download.mono-project.com/repo/ubuntu**</a> **stable-bionic main
# deb-src **"https://download.mono-project.com/repo/ubuntu">**https://download.mono-project.com/repo/ubuntu**</a>** stable-bionic main
```

Edit:
Actually, you only need to do so for the 3rd line as the other are commented out and do nothing.

---

### Post by jgw on 2022-07-09
Thank you for all the help!

Its fixed!

---

