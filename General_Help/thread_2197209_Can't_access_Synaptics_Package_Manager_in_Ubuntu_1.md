---
title: "Can't access Synaptics Package Manager in Ubuntu 12.04"
date: 2014-01-02
forum: General Help
---

### Post by carla.debeer.uk on 2014-01-02
I have Ubuntu 12.04 installed on my PC via Oracle's VirtualBox and need to remove software from Linux. I am not having any success with sudo apt-get remove <name> so I tried to access Synaptics Package Manager but got this message when I tried to open it:

[I]E: Malformed line 54 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.[/I]

I ran 

gksu gedit /etc/apt/sources.list

and this was the feedback:

[I]# deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/)[ distro] partner
deb [http://archive.canonical.com/](http://archive.canonical.com/)[ distro] partner
deb [http://archive.canonical.com/](http://archive.canonical.com/)[ distro] partner[/I]

Might anyone know what it is I need to amend in order to be able to access Synaptics Package Manager?

---

### Post by deadflowr on 2014-01-02
Your sources.list says lucid, which is 10.04, not 12.04.
But beside that, I would comment out the last three entries at the bottom.
Add a # symbol to the front.
It would be the three lines that have [distro] in them.
Then try 
```
sudo apt-get update
```
And see what happens.

---

### Post by Bucky Ball on 2014-01-02
Welcome. Try what deadflowr says, but yep, that's 10.04 LTS. No longer supported.

BTW, if apt-get is not working in a terminal, there's no way you'd be able to use Synaptics even if it would open. That is a front end for apt-get. Need to fix whatever is wrong with apt-get.

Suggest you try reinstalling the supported 12.04 LTS.

---

### Post by chkneater on 2014-01-02
Wouldn't 'dpkg --reconfigure' fix depencies and get synaptic working again?

---

### Post by deadflowr on 2014-01-02
Yeah, lucid is a mixed bag.
Unlike other releases, like 11.04 or 11.10, lucid has a different life cycle for the desktop version and the server version.
Unfortunately, it shares the same repositories for both, so even though the desktop packages are available and the repos are fetchable on the desktop, they DO NOT get any support, which in turn leaves the desktop user with potential vulnerabilities/bugs.
Vulnerabilities/bugs the end user might not ever realize, because the repos are still there.
Luckily, lucid is the last version of Ubuntu that will be like that.
All newer LTS release will run both desktop and server version the same length.
(Now at 5 years)

---

