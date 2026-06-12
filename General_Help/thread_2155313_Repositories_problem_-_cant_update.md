---
title: "Repositories problem - cant update"
date: 2013-06-17
forum: General Help
---

### Post by gareththomasnz on 2013-06-17
Sorry folks I know I need to fix the repositories but thought I would ask for advise first

This is the error from the "check for updates"

W:Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/precise/Release](http://download.virtualbox.org/virtualbox/debian/dists/precise/Release)  Unable to find expected entry 'contrib/source/Sources' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://ppa.launchpad.net/openjdk/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/openjdk/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/openjdk/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/openjdk/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/openjdk/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/openjdk/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

I installed 12.04 LTS about a month ago

---

### Post by plucky on 2013-06-18
> W:Failed to fetch [http://download.virtualbox.org/virtu...recise/Release](http://download.virtualbox.org/virtu...recise/Release) Unable to find expected entry 'contrib/source/Sources' in Release file (Wrong sources.list entry or malformed file)


That entry in your sources.list is pointing to [http://download.virtualbox.org/virtualbox/debian/dists/precise/Release](http://download.virtualbox.org/virtualbox/debian/dists/precise/Release) instead of [http://download.virtualbox.org/virtualbox/debian/dists/precise/contrib/binary-i386/](http://download.virtualbox.org/virtualbox/debian/dists/precise/contrib/binary-i386/) so it needs to be corrected or disabled.

> W:Failed to fetch [http://ppa.launchpad.net/openjdk/ppa...source/Sources](http://ppa.launchpad.net/openjdk/ppa...source/Sources) 404 Not Found


That PPA is looking for an Oneric repository which doesn't exist on the server [http://ppa.launchpad.net/openjdk/ppa/ubuntu/dists/](http://ppa.launchpad.net/openjdk/ppa/ubuntu/dists/) so I would delete the entry from your sources.list.

Good Luck

---

