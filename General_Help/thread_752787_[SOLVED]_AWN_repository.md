---
title: "[SOLVED] AWN repository"
date: 2008-04-12
forum: General Help
---

### Post by agaudio on 2008-04-12
As of yesterday, when I run Update Manager, I get an error that the system could not download all repository indexes. The problem seems to be with the AWN repositories. 

[http://download.tuxfamily.org/syzygy42/dists/gutsy/avant-window-navigator/binary-i386/Packages.gz:](http://download.tuxfamily.org/syzygy42/dists/gutsy/avant-window-navigator/binary-i386/Packages.gz:) 404 Not Found
[http://download.tuxfamily.org/syzygy42/dists/gutsy/avant-window-navigator/source/Sources.gz:](http://download.tuxfamily.org/syzygy42/dists/gutsy/avant-window-navigator/source/Sources.gz:) 404 Not Found


Anyone else experiencing this?

---

### Post by panks on 2008-04-14
yes... I had the same problem.

At awn wiki they say to use the "Unsupported updates (gutsy-backports)" repository index
[http://wiki.awn-project.org/DistributionGuides#Gutsy_Gibbon_.287.10.29]("http://wiki.awn-project.org/DistributionGuides#Gutsy_Gibbon_.287.10.29")

I removed the old entries

[http://download.tuxfamily.org/syzygy...6/Packages.gz:](http://download.tuxfamily.org/syzygy...6/Packages.gz:) 404 Not Found
[http://download.tuxfamily.org/syzygy...ce/Sources.gz:](http://download.tuxfamily.org/syzygy...ce/Sources.gz:) 404 Not Found

to avoid that error message.

---

