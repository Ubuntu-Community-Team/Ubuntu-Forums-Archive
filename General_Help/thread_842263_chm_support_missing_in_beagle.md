---
title: "chm support missing in beagle"
date: 2008-06-27
forum: General Help
---

### Post by nicolas314 on 2008-06-27
Just installed the latest beagle in Hardy and found out there is no support for CHM files. The beagle web site claims support for these, but the filter is not installed on Hardy.

As far as I know, 'tracker' does not support CHM files at all.

Any help on getting full-text search on CHM files on Hardy would be greatly appreciated.

---

### Post by dbera on 2008-06-27
Debian, from which Ubuntu gets most of its packages, had CHM indexing disabled. The bug was filed recently and last I checked Debian had fixed their package. Don't know if the Ubuntu package was fixed too. A bug might help.

---

### Post by nicolas314 on 2008-06-27
Thanks for pointing this out!
I just filed Bug #243490 in beagle (Ubuntu) to report this.

Maybe somebody knows about other search tools supporting CHM files? I tried chm2pdf (PDFs are easily indexed) but it barfed on all my CHM files.

---

