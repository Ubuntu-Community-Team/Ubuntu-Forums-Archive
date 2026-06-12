---
title: "alternate iso"
date: 2007-08-07
forum: General Help
---

### Post by dddexter on 2007-08-07
My alternate iso situation is to similar to but different from others listed here. Installing Wubi on XP Pro, I have a satellite (i.e.slow and constrained) connection so that downloading an iso is not possible. Therefore, purchased a CD of the Alternate 7.04 version. First tried to use dd to prepare an acceptable iso file on my Ubuntu system but dd did not know when to stop and had produced a 56 gb (!!) file by the time I gave up. Then used WinISO to produce an iso file from the CD. Copied that file into a folder with the install .exe as directed in the Wubi guide. The install program still does not recognize the iso file and tries to download.

Suggestions??

---

### Post by ago on 2007-08-07
the dd command is

sudo dd if=/dev/cdrom of=ubuntu-7.04-alternate.iso

---

