---
title: "jigdo for desktop edition"
date: 2007-04-21
forum: General Help
---

### Post by alexandrul on 2007-04-21
could someone generate the jigdo files for the desktop 7.04 i386 editions of ubuntu, kubuntu and xubuntu? i started with ubuntu server (from the torrent), and then the alternate editions of ubuntu, kubuntu and xubuntu, but for desktop editions there are no jigdo files.

---

### Post by cramm on 2007-04-22
I had been asking myself the same question, and now I think I know the answer.

I had downloaded the .iso file for the RC i386 desktop CD using the good old wget method
and wanted to avoid having to re-download all the files but when I compared the md5sums I 
realized the RC got promoted to final release so no download was necessary (just rename the .iso file).

Later (again, trying to avoid lengthy downloads), I wanted to use jigdo to create the alternate 
CD .iso image starting from the desktop .iso file: loopback mounting it and pointing ligdo-lite
to the mount point so it could find all the files that are common to both CDs and then I realized 
why there is no jigdo files for the desktop CD:

Desktop CDs are live CDs so they have a big (631 MiB, compare it to the 700 MiB
total CD size) file containing a casper/filesystem.squashfs squashfs filesystem that
contains the most part of the .deb package files.

Now the jigdo magic is possible because you can download (one by one) the files cointained
in a CD, jigdo-lite fleshes the "skeleton" (the .tempalte file) using these files. The granularity of 
jigdo is at the file level.

But in this case almost all the CD space is occupied by this opaque .squashfs file. So... why 
bother using jigdo to distribute it? if a users's download gets interrupted while jigdo-lite
is wgetting that file, next time it will have to start the download from the start. With such a
big file the file-level granularity of jigdo is of no help, other methods (BitTorrent that
works with a block granularity and knows nothing about file boundaries) or 
directly download the 700 MiB file using your  favorite HTTP/FTP download utility will be
better.

Alternate and server are more "traditional" CDs so they can be download using jigdo.

HTH

---

### Post by alexandrul on 2007-04-22
thank you for your answer, I never used the desktop cds before, only the alternate ones, and you are right :D

---

