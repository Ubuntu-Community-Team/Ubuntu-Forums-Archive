---
title: "Disks (palimpsest) formated exFAT drive &amp; Mac says &quot;...not readable by this computer&quot;"
date: 2014-12-10
forum: General Help
---

### Post by jamesisin on 2014-12-10
I have a thumdrive.  I added exfat support to Ubuntu 14.04 and used Disks (palimpsest) to format that with exFAT (choose Custom and specify exfat).

Windows and Ubuntu love that drive just fine.

The Mac (tested Mavericks and Yosemite) OS tells me "The disk you inserted was not readable by this computer."  (I am offered to "Initialize...", "Ignore", or "Eject".)

This does not happen if I format the drive using Windows.

Any suggestions?

---

### Post by jamesisin on 2014-12-11
Anybody?

---

### Post by jamesisin on 2014-12-16
exFAT sux?

---

### Post by jamesisin on 2014-12-17
Hi?

---

### Post by sudodus on 2014-12-17
exfat is a proprietary file system owned by Microsoft. It is better than fat32 in some ways. I would suggest that you make a fat32 file system in Ubuntu, unless you know, that it will not work (for example, if you have files bigger than 4 GB).

Or even better, that you make an exfat system using Windows. In general, it is best to use Windows to create and repair Windows tools (in this case the exfat file system), and to use linux to create and repair linux tools.

---

### Post by jamesisin on 2014-12-17
Is there a place where I can file a bug for the maintainers of exFAT Linux?

---

### Post by sudodus on 2014-12-17
1. Are you sure you formatted to exfat (and not to vfat or something similar)?

2. How did you add exfat support? I guess those who supply it are also interested in bug reports.

---

### Post by jamesisin on 2014-12-17
It is definitely exFAT.

In the standard repos are exfat-fuse and exfat-utils.

---

### Post by sudodus on 2014-12-18
Maybe these links will help you reach the person(s) responsible for the exfat tools for linux

[https://packages.debian.org/unstable/exfat-utils](https://packages.debian.org/unstable/exfat-utils)

[https://bugs.debian.org/cgi-bin/pkgreport.cgi?pkg=exfat-utils;dist=unstable](https://bugs.debian.org/cgi-bin/pkgreport.cgi?pkg=exfat-utils;dist=unstable)

---

