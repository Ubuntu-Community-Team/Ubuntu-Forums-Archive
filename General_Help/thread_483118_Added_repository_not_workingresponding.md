---
title: "Added repository not working/responding"
date: 2007-06-24
forum: General Help
---

### Post by JimNSB on 2007-06-24
Added medibuntu to my sources.list (then added gpg key & edited sources.list with new repo data), but now I'm seeing this with *sudo apt-get update*:> 
<snipped>
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages
  404 Not Found
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages
  404 Not Found
Get:7 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages [5483B]
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources
  404 Not Found
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources
  404 Not Found
Get:8 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages [2849B]
Fetched 10.7kB in 1s (7286B/s)
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

server problem, or did I goof-up somewhere?

---

### Post by JimNSB on 2007-06-24
disregard: tried it again and all worked fine

---

