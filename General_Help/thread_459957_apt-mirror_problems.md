---
title: "apt-mirror problems"
date: 2007-05-31
forum: General Help
---

### Post by vdpollm on 2007-05-31
Hi there,

I have followed various links to create a local repository using apt-mirror.
"http://popey.com/Creating_an_Ubuntu_repository_mirror_with_apt-mirror"

That part seemed to be easy. I modified my mirror.list to update from za.archive.ubuntu.com (the local mirror in SA)

However, when i run apt-get update from a client machine, after making the necessary changes to sources.list, I get some errors:

Failed to fetch [http://myserver/mirror/archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.bz2](http://myserver/mirror/archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.bz2)  MD5Sum mismatch
Failed to fetch [http://myserver/mirror/archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.bz2](http://myserver/mirror/archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.bz2)  MD5Sum mismatch
Failed to fetch [http://myserver/mirror/archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/binary-i386/Packages.bz2](http://myserver/mirror/archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/binary-i386/Packages.bz2)  MD5Sum mismatch
Failed to fetch [http://myserver/mirror/archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.bz2](http://myserver/mirror/archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.bz2)  MD5Sum mismatch

When i ran apt-get upgrade, it upgraded a few of the files.

I changed the mirror.list to point to archive.ubuntu.com instead, and then moved za.archive.ubuntu.com to archive.ubuntu.com on my local hard drive, and re-ran apt-mirror. it found 101mb of additional files to download.

i changed my sources.list to point to the correct mirror on my server, and ran apt-get update, and apt-get upgrade, and there were no updates.

however, when i changed my sources.list to point to archive.ubuntu.com, and ran apt-get updated and apt-get upgrade, there were 30 updates that had to be applied, and there were no MD5Sum errors

The idea is to set up local repository, so that i only have to download once, and then update from my local server. But it seems that apt-mirror missed some files?

why would i get the MD5Sum error from my local repository? How do i fix

regards

Marc

---

