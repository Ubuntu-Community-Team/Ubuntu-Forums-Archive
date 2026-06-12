---
title: "VirtualBox install gone wrong"
date: 2016-02-22
forum: General Help
---

### Post by Woovie on 2016-02-22
Hello, a colleague of mine tried to install VirtualBox, and then proceeded to fix the initial error by running further apt-gets and eventually got to this point, which I tried to resolve but I am stuck myself at this point. I'd rather not try anything further to avoid possible issues.

```
root@woovie:~# sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gcc-4.9-base:i386 libboost-date-time1.54.0 libclucene-contribs1
  libclucene-core1 libcmis-0.4-4 libexttextcat-2.0-0 libexttextcat-data
  libhyphen0 liblangtag-common liblangtag1 libmythes-1.2-0 libneon27-gnutls
  libreoffice-common libreoffice-core libreoffice-style-galaxy python3-uno
  uno-libs3 ure xfonts-mathml
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  avahi-daemon colord libnss-mdns libsane libsane-common
Suggested packages:
  avahi-autoipd hplip hpoj libsane-extras sane-utils
The following packages will be REMOVED:
  bluez-cups language-pack-en language-pack-en-base printer-driver-gutenprint
  printer-driver-splix
The following NEW packages will be installed:
  avahi-daemon colord libnss-mdns libsane libsane-common
0 upgraded, 5 newly installed, 5 to remove and 12 not upgraded.
5 not fully installed or removed.
Need to get 0 B/2673 kB of archives.
After this operation, 8759 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
dpkg: warning: 'ldconfig' not found in PATH or not executable
dpkg: error: 1 expected program not found in PATH or not executable
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

```
root@woovie:~# echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
```

```
root@woovie:~# cat /etc/apt/sources.list
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ubuntu.bhs.mirrors.ovh.net/ubuntu trusty main restricted
deb-src http://ubuntu.bhs.mirrors.ovh.net/ubuntu trusty main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://ubuntu.bhs.mirrors.ovh.net/ubuntu trusty-updates main restricted
deb-src http://ubuntu.bhs.mirrors.ovh.net/ubuntu trusty-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ubuntu.bhs.mirrors.ovh.net/ubuntu trusty universe
deb-src http://ubuntu.bhs.mirrors.ovh.net/ubuntu trusty universe
deb http://ubuntu.bhs.mirrors.ovh.net/ubuntu trusty-updates universe
deb-src http://ubuntu.bhs.mirrors.ovh.net/ubuntu trusty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ubuntu.bhs.mirrors.ovh.net/ubuntu trusty multiverse
deb-src http://ubuntu.bhs.mirrors.ovh.net/ubuntu trusty multiverse
deb http://ubuntu.bhs.mirrors.ovh.net/ubuntu trusty-updates multiverse
deb-src http://ubuntu.bhs.mirrors.ovh.net/ubuntu trusty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ubuntu.bhs.mirrors.ovh.net/ubuntu trusty-backports main restricted universe multiverse
deb-src http://ubuntu.bhs.mirrors.ovh.net/ubuntu trusty-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main


# Experimental/unstable (sid) repositories
#deb http://ftp.debian.org/debian experimental main
#deb http://ftp.debian.org/debian sid main


# virtual box
#deb http://download.virtualbox.org/virtualbox/debian trusty contrib
```

Thanks for any assistance.

**EDIT:**

[http://itsfoss.com/fix-exec-locale-file-directory/](http://itsfoss.com/fix-exec-locale-file-directory/)

Solved. Nevermind!

---

