---
title: "LiveCDs always dump me into a root shell in QEMU"
date: 2007-11-11
forum: General Help
---

### Post by CSMatt on 2007-11-11
Ever since I upgraded to Gutsy I can't get QEMU to work right with my LiveCDs.  Every time I try to boot into one the LiveCD always dumps me into an emergency shell, usually because it says that it can't find root or something similar.  I've attached screen shots for the Ubuntu 7.10 LiveCD and the Fedora 8 LiveCD with GNOME, both with "quiet" turned off and "verbose" turned on in the boot options.  These are not corrupted ISOs so it isn't the file that's the problem here.

---

### Post by CSMatt on 2007-11-15
I've also tried to install Fluxbuntu 7.10 in QEMU and the installer wasn't able to detect the CD-ROM drivers.  Is it possible that the CD-ROM component is defective, and that this is also causing the errors in the liveCDs?

---

### Post by odzx on 2007-12-31
same problem here

---

### Post by abhi.datt on 2008-02-11
This is a known bug and the solution is to install this package
[http://archive.ubuntu.com/ubuntu/pool/universe/b/bochs/bochsbios_2.3.5-1ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/b/bochs/bochsbios_2.3.5-1ubuntu1_all.deb)

For more details for this solution view this
[https://bugs.launchpad.net/ubuntu/+source/bochs/+bug/123185](https://bugs.launchpad.net/ubuntu/+source/bochs/+bug/123185)

---

