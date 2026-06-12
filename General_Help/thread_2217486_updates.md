---
title: "updates"
date: 2014-04-17
forum: General Help
---

### Post by john_burns2 on 2014-04-17
I have a red warning triangle at the top of my display telling me the update information is outdated. When I check for updates I get this message (after it's looked for updates)
> W:Failed to fetch [http://ppa.launchpad.net/cinelerra-ppa/cinelerra-cv/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/cinelerra-ppa/cinelerra-cv/ubuntu/dists/precise/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/cinelerra-ppa/cinelerra-cv/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/cinelerra-ppa/cinelerra-cv/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
  It tells me to check my internet connection (but I know it's fine)  Is anyone else having these problems with cinelerra updates ??

---

### Post by ajgreeny on 2014-04-17
Open up your software-sources and remove those ppa repos as they do not exist.

---

### Post by slickymaster on 2014-04-17
> **ajgreeny said:**
> Open up your software-sources and remove those ppa repos as they do not exist.

+1

Presently, cinelerra, holds the following PPA's at Launchpad: [Index of /cinelerra-ppa]("http://ppa.launchpad.net/cinelerra-ppa/")

---

