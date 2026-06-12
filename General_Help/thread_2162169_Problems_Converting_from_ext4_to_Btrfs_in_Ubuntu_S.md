---
title: "Problems Converting from ext4 to Btrfs in Ubuntu Server 13.10"
date: 2013-07-13
forum: General Help
---

### Post by King Dude on 2013-07-13
I've recently installed Ubuntu Server 13.10, and even though everything seems to work I'd like to convert my ext4 file system to Btrfs.

I try running file system check before I convert:

```

fsck -f /dev/sda1
```

It tells me that I cannot check it because it is mounted. Afterwards, I just went straight into trying to convert it, but it won't let me do that either even if I am root.

It feels like I've tried everything. Somebody help me before I rip my hair out.

-----------------------------------------
OS: Ubuntu Server 13.10 (Development Branch) i386 32bit
Processor: Intel Pentium 3 550Mhz

---

### Post by tgalati4 on 2013-07-13
Typically you check the root file system from a Live DVD/USB session (where the disk is not mounted) or boot into recovery mode and select the option, "Mount R/W and check disk".  If this is a new install, is there not an option to partition the root file system directly with btrfs?

---

### Post by King Dude on 2013-07-13
No, there was not an option during installation to format my system with btrfs right off the bat. And how do I boot recovery mode exactly? I've tried selecting "Rescue a Broken System", but it tries to guide me through what looks like a reinstallation.

[IMG]http://maas.ubuntu.com/docs/_images/install_02.png[/IMG]

I used an Ubuntu Server 12.04 install disk, though. Should I make a new disk with 13.10?

---

