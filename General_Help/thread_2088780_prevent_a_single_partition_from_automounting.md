---
title: "prevent a single partition from automounting"
date: 2012-11-27
forum: General Help
---

### Post by markosjal on 2012-11-27
I have a USB Thumb drive that boots linux. It will also boot an appleTV. The for booting Apple TV it uses HFS partition labeled "Recovery" with the "atvrec" flag set. 

When the system has booted linux it does not need to read or write to this disk. 

All of the utilities I tried would not show me a UUID for an HFS PLUS disk, so I tried putting this in the /etc/fstab

LABEL=Recovery  none  hfsplus  r,noauto

The partition still mounted automacially at boot.

I want this partition to NOT MOUNT unless I manually mount it.

What have I done wrong here?

---

