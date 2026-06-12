---
title: "Best way to update LVM2 (trusty)"
date: 2015-07-24
forum: General Help
---

### Post by SirTempest on 2015-07-24
I'm setting up a new server that has 6 HDDs and an internal PCI-E SSD as a caching layer for the drives. I intend to setup the SSD as a cache via dm-cache and the lvm front end for dm-cache. However, the lvm packages for Trusty 14.04 are too old and don't support caching (or thin provisioning for that matter), 2.02.98, whereas the earliest lvm with stable cache support seems is much newer, 2.02.106 (from man pages). 

So what's the best way to go about updating LVM? I can build from source/package a DEB, and I already have, but GRUB dropped into rescue on reboot. Is their a PPA I missed, or an easy way to backport a new deb? Vivid has the needed package, so is there a way to just install the updated LVM package from the Vivid repos without breaking everything?

---

### Post by SirTempest on 2015-07-24
Woops. Seems there was a PPA I missed: [https://launchpad.net/~sbv/+archive/ubuntu/lvm-backports](https://launchpad.net/~sbv/+archive/ubuntu/lvm-backports)

Still, is it possible to backport the official packages myself?

---

