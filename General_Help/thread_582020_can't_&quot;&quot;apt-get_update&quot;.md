---
title: "can't &quot;&quot;apt-get update&quot;"
date: 2007-10-19
forum: General Help
---

### Post by nermalthecat on 2007-10-19
hi, i've been running gutsy since tribe 5, but after the release I wanted to upgrade to it. 
When I type apt-get update, i get the following errors:

[B]90% [6 Packages bzip2 0] [7 Packages 1914/175kB 1%]                 21.7kB/s 7sbzip2: (stdin) is not a bzip2 file.
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/main Packages
  Sub-process bzip2 returned an error code (2)
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/multiverse Packages
99% [7 Packages bzip2 0]                                            13.9kB/s 0sbzip2: (stdin) is not a bzip2 file.
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/restricted Packages
  Sub-process bzip2 returned an error code (2)
Fetched 1781kB in 2m21s (12.6kB/s)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
[/B]

Thanks, in advance.

---

### Post by dayvy on 2007-10-19
My advice is to try another mirror as I've been having problems with that same mirror that last day or so. I think a lot of the mirrors are swamped right now and causing problems for people. Make sure to reload the packages before upgrading i.e aptitude update then aptitude upgrade.

---

