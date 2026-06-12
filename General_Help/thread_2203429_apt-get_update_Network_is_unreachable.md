---
title: "apt-get update Network is unreachable??"
date: 2014-02-03
forum: General Help
---

### Post by michaelmcole on 2014-02-03
[B]Trying to install php-ldap, first I run an update, and get these errors;

(BTW- I am SSH'd into this box and I can ping these addresses just fine)[/B]

Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release.gpg
  Cannot initiate the connection to security.ubuntu.com:80 (2001:67c:1562::15). - connect (101: Network is unreachable) [IP: 2001:67c:1562::15 80]
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release.gpg
  Could not connect to extras.ubuntu.com:80 (91.189.92.152). - connect (111: Connection refused)
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg
  Unable to connect to extras.ubuntu.com:http:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring Release.gpg
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::15). - connect (101: Network is unreachable) [IP: 2001:67c:1562::15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates Release.gpg
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::15). - connect (101: Network is unreachable) [IP: 2001:67c:1562::15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports Release.gpg
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::15). - connect (101: Network is unreachable) [IP: 2001:67c:1562::15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-proposed Release.gpg
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::15). - connect (101: Network is unreachable) [IP: 2001:67c:1562::15 80]
Ign [https://download.01.org](https://download.01.org) Ubuntu Release.gpg
Ign [https://download.01.org](https://download.01.org) Ubuntu Release
Ign [https://download.01.org](https://download.01.org) Ubuntu/13.04 amd64 Packages/DiffIndex
Ign [https://download.01.org](https://download.01.org) Ubuntu/13.04 i386 Packages/DiffIndex
Ign [https://download.01.org](https://download.01.org) Ubuntu/13.04 Translation-en_US
Ign [https://download.01.org](https://download.01.org) Ubuntu/13.04 Translation-en
Err [https://download.01.org](https://download.01.org) Ubuntu/13.04 amd64 Packages
  Failed connect to download.01.org:443; Connection refused
Err [https://download.01.org](https://download.01.org) Ubuntu/13.04 i386 Packages
  Failed connect to download.01.org:443; Connection refused
Err [http://archive.canonical.com](http://archive.canonical.com) raring Release.gpg
  Cannot initiate the connection to archive.canonical.com:80 (2001:67c:1360:8c01::1b). - connect (101: Network is unreachable) [IP: 2001:67c:1360:8c01::1b 80]
Err [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg
  Cannot initiate the connection to archive.canonical.com:80 (2001:67c:1360:8c01::1b). - connect (101: Network is unreachable) [IP: 2001:67c:1360:8c01::1b 80]
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/raring/Release.gpg)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::15). - connect (101: Network is unreachable) [IP: 2001:67c:1562::15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/Release.gpg)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::15). - connect (101: Network is unreachable) [IP: 2001:67c:1562::15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/Release.gpg)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::15). - connect (101: Network is unreachable) [IP: 2001:67c:1562::15 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/raring-security/Release.gpg)  Cannot initiate the connection to security.ubuntu.com:80 (2001:67c:1562::15). - connect (101: Network is unreachable) [IP: 2001:67c:1562::15 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/raring/Release.gpg](http://archive.canonical.com/ubuntu/dists/raring/Release.gpg)  Cannot initiate the connection to archive.canonical.com:80 (2001:67c:1360:8c01::1b). - connect (101: Network is unreachable) [IP: 2001:67c:1360:8c01::1b 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/Release.gpg](http://archive.canonical.com/ubuntu/dists/precise/Release.gpg)  Cannot initiate the connection to archive.canonical.com:80 (2001:67c:1360:8c01::1b). - connect (101: Network is unreachable) [IP: 2001:67c:1360:8c01::1b 80]

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/raring/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/raring/Release.gpg)  Could not connect to extras.ubuntu.com:80 (91.189.92.152). - connect (111: Connection refused)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring-proposed/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/raring-proposed/Release.gpg)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::15). - connect (101: Network is unreachable) [IP: 2001:67c:1562::15 80]

W: Failed to fetch [https://download.01.org/gfx/ubuntu/13.04/main/dists/Ubuntu/13.04/binary-amd64/Packages](https://download.01.org/gfx/ubuntu/13.04/main/dists/Ubuntu/13.04/binary-amd64/Packages)  Failed connect to download.01.org:443; Connection refused

W: Failed to fetch [https://download.01.org/gfx/ubuntu/13.04/main/dists/Ubuntu/13.04/binary-i386/Packages](https://download.01.org/gfx/ubuntu/13.04/main/dists/Ubuntu/13.04/binary-i386/Packages)  Failed connect to download.01.org:443; Connection refused

W: Some index files failed to download. They have been ignored, or old ones used instead.

================================================================================================

_**and, here is my sources.list:**_
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted


# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner


## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-proposed restricted main multiverse universe

---

### Post by michaelmcole on 2014-02-03
wow, nevermind, it was my own stupid fault...  box is on the wrong network...

---

### Post by deadflowr on 2014-02-03
raring is dead.
The repos are gone.
Upgrade to a supported release.
12.04, 12.10, 13.10, or the beta 14.04.
(Okay, technically 12.04 and 12.10 are downgrades)

---

