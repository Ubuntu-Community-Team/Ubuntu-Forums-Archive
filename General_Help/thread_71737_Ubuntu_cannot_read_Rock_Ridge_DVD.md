---
title: "Ubuntu cannot read Rock Ridge DVD"
date: 2005-10-04
forum: General Help
---

### Post by pravda on 2005-10-04
Hi

I've just written a DVD using K3B, filesystem is Rock Ridge Extensions. But KDE cannot mount it. When I have my drive declared as auto in fstab I get the following error:
***
mount: I could not determine the filesystem type, and none was specified
***

When I change the auto to iso9660,ufs in fstab I get the following error:
***
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so
***

The DVD is perfectly readable in my Windows machine, detected as CDFS.

Anybody know how I can get Ubuntu to read this DVD?

---

### Post by pravda on 2005-10-04
Solved the problem by selecting all three file type boxes in K3B when writing, Rock Ridge, Joliet and UDF.

But still cannot read the DVD written using only Rock Ridge in Linux.

---

