---
title: "Could not download all repository indexes"
date: 2007-08-25
forum: General Help
---

### Post by dhalexos on 2007-08-25
Hello,

When I open my Synaptic Package Manager, I always receive a error box: "Could not download all repository indexes". I'm use Ubuntu Breezy 5.10. Can somebody help me fix it?

> The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz:) 404 Not Found
[http://be.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz:](http://be.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz:) 404 Not Found
[http://be.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz:](http://be.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz:) 404 Not Found
[http://be.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz:](http://be.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz:) 404 Not Found
[http://be.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz:](http://be.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz:) 404 Not Found
[http://be.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz:](http://be.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz:) 404 Not Found
[http://be.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz:](http://be.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://be.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz:](http://be.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz:) 404 Not Found
[http://be.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz:](http://be.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz:) 404 Not Found



Thanks

Dhalexos

---

### Post by apetresc on 2007-08-25
Those are some weeeird entries. What are the contents of your /etc/apt/sources.list file?

---

### Post by dhalexos on 2007-08-25
Excuse me, I copied the wrong section. I updated the first post with the good content.

The content of my /etc/apt/sources.list is:

> 
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe



Thanks

Dhalexos

---

### Post by davidjmayo on 2007-08-25
Breezy Badger
	

Version 5.10
	

Released October 13, 2005
	

Unsupported as of April 2007 

from

[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)

---

