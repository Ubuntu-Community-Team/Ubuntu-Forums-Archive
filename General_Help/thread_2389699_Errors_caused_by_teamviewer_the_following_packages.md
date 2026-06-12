---
title: "Errors caused by teamviewer: the following packages have unmet dependencies"
date: 2018-04-20
forum: General Help
---

### Post by wanda.fiat on 2018-04-20
Hi everyone,

I struggled with Teamviewer 13 and then 12 on Ubuntu 16.04.
FYI I am rather new to Ubuntu and i switched bc of deep learning.

The first installation of teamviewer 13 didn't work, there are a lot of discussions around about this. Then I tried with 12 and after removing it with **sudo apt-get remove teamviewer** I remained with some errors, more specifically unmet dependencies:

[COLOR=#ff0000]The following packages have unmet dependencies:[/COLOR]
[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]libpng12-0: Depends: libc6 (>= 2.14) but 2.23-0ubuntu10 is installed[/COLOR]
[COLOR=#ff0000]            Depends: zlib1g (>= 1:1.1.4) but 1:1.2.8.dfsg-2ubuntu4.1 is installed[/COLOR]
[COLOR=#ff0000]libpng12-0:i386: Depends: libc6 (>= 2.11) but 2.23-0ubuntu10 is installed[/COLOR]
[COLOR=#ff0000]                 Depends: zlib1g (>= 1:1.1.4) but 1:1.2.8.dfsg-2ubuntu4.1 is installed[/COLOR]

I ran the following in a terminal based on an older thread:
$ **grep -v ^# /etc/apt/sources.list /etc/apt/sources.list.d/***
/etc/apt/sources.list:
/etc/apt/sources.list:deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) xenial main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) xenial universe
/etc/apt/sources.list:deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) xenial-updates universe
/etc/apt/sources.list:
/etc/apt/sources.list:deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) xenial multiverse
/etc/apt/sources.list:deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
/etc/apt/sources.list:deb [arch=i386,amd64] [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) xenial main
/etc/apt/sources.list.d/cuda.list:deb [http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64](http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64) /
/etc/apt/sources.list.d/dropbox.list:deb [arch=i386,amd64] [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) wily main
/etc/apt/sources.list.d/graphics-drivers-ubuntu-ppa-xenial.list:deb [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) xenial main
/etc/apt/sources.list.d/teamviewer.list.dpkg-new:
/etc/apt/sources.list.d/teamviewer.list.dpkg-new:
/etc/apt/sources.list.d/teamviewer.list.dpkg-new:
/etc/apt/sources.list.d/teamviewer.list.dpkg-new:
/etc/apt/sources.list.d/teamviewer.list.dpkg-new:
/etc/apt/sources.list.d/teamviewer.list.dpkg-new:
/etc/apt/sources.list.d/teamviewer.list.dpkg-new:deb [http://linux.teamviewer.com/deb](http://linux.teamviewer.com/deb) stable main
/etc/apt/sources.list.d/teamviewer.list.dpkg-new:deb [http://linux.teamviewer.com/deb](http://linux.teamviewer.com/deb) preview main
/etc/apt/sources.list.d/teamviewer.list.dpkg-new:


I've tried **sudo apt-get -f install **and I get:
Preparing to unpack .../libpng12-0_1.2.54-1ubuntu1_i386.deb ...
Unpacking libpng12-0:i386 (1.2.54-1ubuntu1) over (1.2.50-2+deb8u3) ...
dpkg: error processing archive /var/cache/apt/archives/libpng12-0_1.2.54-1ubuntu1_i386.deb (--unpack):
 trying to overwrite shared '/usr/share/doc/libpng12-0/KNOWNBUG', which is different from other instances of package libpng12-0:i386
Processing triggers for libc-bin (2.23-0ubuntu10) ...
[COLOR=#ff0000]Errors were encountered while processing:[/COLOR]
[COLOR=#ff0000] /var/cache/apt/archives/libpng12-0_1.2.54-1ubuntu1_i386.deb[/COLOR]
[COLOR=#ff0000]E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]


Any ideas? 
Thanks in advance.

---

