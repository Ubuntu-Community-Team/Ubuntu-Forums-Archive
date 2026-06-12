---
title: "Launchpad keeps giving errors on updates - is something wrong?"
date: 2021-01-04
forum: General Help
---

### Post by GhX6GZMB on 2021-01-04
Trying to run sudo update, I keep getting this in the last days:

```
Err:27 http://ppa.launchpad.net/kicad/kicad-5.1-releases/ubuntu focal InRelease                                                             
  Could not connect to ppa.launchpad.net:80 (2001:67c:1560:8008::19), connection timed out Could not connect to ppa.launchpad.net:80 (91.189.95.85), connection timed out
Err:28 http://ppa.launchpad.net/libreoffice/ppa/ubuntu focal InRelease
  Unable to connect to ppa.launchpad.net:http:
Fetched 5.094 kB in 31s (166 kB/s)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
11 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: Failed to fetch http://ppa.launchpad.net/kicad/kicad-5.1-releases/ubuntu/dists/focal/InRelease  Could not connect to ppa.launchpad.net:80 (2001:67c:1560:8008::19), connection timed out Could not connect to ppa.launchpad.net:80 (91.189.95.85), connection timed out
W: Failed to fetch http://ppa.launchpad.net/libreoffice/ppa/ubuntu/dists/focal/InRelease  Unable to connect to ppa.launchpad.net:http:
W: Some index files failed to download. They have been ignored, or old ones used instead.

```
Anyone else have this?
Or do I have a configuration error somewhere?

---

