---
title: "Help!"
date: 2007-11-01
forum: General Help
---

### Post by The Wisedude on 2007-11-01
I get this error when I try to update Ubuntu to 7.10.

> Failed to fetch [http://download.tuxfamily.org/3v1deb/dists/feisty/eyecandy/binary-i386/Packages.bz2](http://download.tuxfamily.org/3v1deb/dists/feisty/eyecandy/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://download.tuxfamily.org/3v1deb/dists/feisty/eyecandy/binary-i386/Packages.bz2](http://download.tuxfamily.org/3v1deb/dists/feisty/eyecandy/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 404 Not Found


---

### Post by Maestro23 on 2007-11-01
Post your /etc/apt/sources.list

> cat /etc/apt/sources.list

All you need to do is delete or comment out (#) those entries in your list. Then:

> sudo apt-get update

sudo apt-get upgrade

---

### Post by daengbo on 2007-11-01
You can also use System -> Administration -> Software Sources and uncheck the third-party software for tuxfamily and medibuntu. After the upgrade, you might try editing them to change feisty to gutsy and re-enable.

---

