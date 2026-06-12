---
title: "&quot;Failed to fetch&quot; message after updating"
date: 2013-06-29
forum: General Help
---

### Post by dieuwke on 2013-06-29
I have seen several posts on similar issues on the forum but yet I can't seem to figure out how to solve my problem. 
When I try to update with sudo apt-get update I get the following messages

W: Failed to fetch [http://nl.archive.ubuntu.com/ubuntu/dists/raring/Release](http://nl.archive.ubuntu.com/ubuntu/dists/raring/Release)  Unable to find expected entry 'main/binary-1386/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/raring/Release](http://extras.ubuntu.com/ubuntu/dists/raring/Release)  Unable to find expected entry 'main/binary-1386/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/raring/Release](http://archive.canonical.com/ubuntu/dists/raring/Release)  Unable to find expected entry 'partner/binary-1386/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch [http://nl.archive.ubuntu.com/ubuntu/dists/raring-updates/Release](http://nl.archive.ubuntu.com/ubuntu/dists/raring-updates/Release)  Unable to find expected entry 'main/binary-1386/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch [http://archive.canonical.com/dists/raring/Release](http://archive.canonical.com/dists/raring/Release)  Unable to find expected entry 'partner/binary-1386/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch [http://nl.archive.ubuntu.com/ubuntu/dists/raring-backports/Release](http://nl.archive.ubuntu.com/ubuntu/dists/raring-backports/Release)  Unable to find expected entry 'main/binary-1386/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch [http://nl.archive.ubuntu.com/ubuntu/dists/raring-security/Release](http://nl.archive.ubuntu.com/ubuntu/dists/raring-security/Release)  Unable to find expected entry 'main/binary-1386/Packages' in Release file (Wrong sources.list entry or malformed file)


E: Some index files failed to download. They have been ignored, or old ones used instead.




The content of my source.list file:

# deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)]/ raring main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) raring main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) raring main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) raring-updates main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) raring-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) raring universe
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) raring universe
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) raring-updates universe
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) raring-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) raring multiverse
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) raring multiverse
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) raring-updates multiverse
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) raring-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) raring-backports main restricted universe multiverse
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) raring-backports main restricted universe multiverse


deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) raring-security main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) raring-security main restricted
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) raring-security universe
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) raring-security universe
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) raring-security multiverse
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) raring-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
deb [http://archive.canonical.com/](http://archive.canonical.com/) raring partner
# deb-src [http://archive.canonical.com/](http://archive.canonical.com/) raring partner
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main



Help would be very much appreciated. Thank you!

---

### Post by ajgreeny on 2013-06-29
It may be worth going to [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/) and making a new sources list from there.

Don't worry, at this stage nothing in your current version is replaced, but it will generate a default new one which you can compare with the one you have at present.  You can even choose to add several of the available ppa repos if you wish.

Having made this simply backup your old sources list and replace it with the new one, as root of course, run **sudo apt-get update** and see if that works for you.

---

### Post by dieuwke on 2013-06-30
Thanks for your reply, the source list I generated with that website was indeed different from the one on my computer, but even with this one I still got a bunch of 'failed to fetch' messages, so unfortunately this does not seem the solution for my problem. Any other suggestions? Thanks

---

### Post by dieuwke on 2013-07-01
Saved my problem. Apparently I added an architecture that caused problems, I found outt on [http://askubuntu.com/questions/256260/how-to-fix-failed-to-download-repository-information-error-while-updating](http://askubuntu.com/questions/256260/how-to-fix-failed-to-download-repository-information-error-while-updating).

---

