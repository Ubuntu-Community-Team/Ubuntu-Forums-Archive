---
title: "Samba install  some packages could not be installed  libldb1 Ubuntu 16.04.1 LTS"
date: 2016-12-12
forum: General Help
---

### Post by markbann on 2016-12-12
Can't install Samba, new install VMware Hypervision  64 bit

```
 sudo apt-get install samba
...

The following packages have unmet dependencies:
 samba : Depends: python-samba but it is not going to be installed
         Depends: samba-common-bin (= 3:4.1.9+dfsg-1~zentyal2~84) but it is not going to be installed
         Depends: samba-dsdb-modules (= 3:4.1.9+dfsg-1~zentyal2~84) but it is not going to be installed
         Depends: samba-libs (= 3:4.1.9+dfsg-1~zentyal2~84) but it is not going to be installed
         Recommends: samba-vfs-modules but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

If I just try to install Samba-libs
```
The following packages have unmet dependencies:
 samba-libs : Depends: libldb1 (< 1:1.1.17~) but 2:1.1.24-1ubuntu3 is to be installed
              Depends: libgcrypt11 (>= 1.5.1) but it is not installable
              Depends: libgnutls26 (>= 2.12.17-0) but it is not installable
E: Unable to correct problems, you have held broken packages.
```

There are not broken packages as far as I can tell.
```
 sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```


Edit 1:
So the problem is one of Samba being dependent on the old libldb1 and libgcrypt11.  Oddly if this is true no one can install Samba on Ubuntu 16 lts without either facing this issue or am I missing something?

Edit 2: 
So starting trying to just get samba-libs installed.  And for that I needed libgnutls26 and libldb1 version 1:1.1.16-1.  I got them from Trusty by adding these to my sources list

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty trusty-security main

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)  trusty main


I had to do a  little cleaning and purging to get it to work but then I was able to install samba-libs
```
 sudo apt-get install samba-libs
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following additional packages will be installed:
  libntdb1 libpython2.7 libwbclient0 python-talloc samba-dsdb-modules
The following NEW packages will be installed:
  libntdb1 libpython2.7 libwbclient0 python-talloc samba-dsdb-modules samba-libs
0 upgraded, 6 newly installed, 0 to remove and 1 not upgraded.
Need to get 5,739 kB of archives.
After this operation, 23.6 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/universe amd64 libntdb1 amd64 1.0-9 [39.6 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libpython2.7 amd64 2.7.12-1ubuntu0~16.04.1 [1,070 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main amd64 python-talloc amd64 2.1.5-2 [7,506 B]
Get:4 [http://archive.zentyal.org/zentyal](http://archive.zentyal.org/zentyal) 3.5/main amd64 libwbclient0 amd64 3:4.1.9+dfsg-1~zentyal2~84 [113 kB]
Get:5 [http://archive.zentyal.org/zentyal](http://archive.zentyal.org/zentyal) 3.5/main amd64 samba-dsdb-modules amd64 3:4.1.9+dfsg-1~zentyal2~84 [310 kB]
Get:6 [http://archive.zentyal.org/zentyal](http://archive.zentyal.org/zentyal) 3.5/main amd64 samba-libs amd64 3:4.1.9+dfsg-1~zentyal2~84 [4,199 kB]
...

```

But now Samba still won't install.  It's stuck on python-samba that depends on samba-libs (= 3:4.1.9+dfsg-1~zentyal2~84)   -- but I was able to install samba-libs
```

apt-cache policy samba-libs
samba-libs:
  Installed: 3:4.1.9+dfsg-1~zentyal2~84

```

**Edit 3**
Finally got it to work.  Uninstalled everything.  Apt kept upgrading the packages I needed to stay at old versions.
Switched to aptitude and made sure when selecting options to keep the old libraries.  This seems like a bad idea to me but not sure what else to do.

---

