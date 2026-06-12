---
title: "LUKS encryption password not working after Laptop runs out of battery"
date: 2007-11-11
forum: General Help
---

### Post by Meson on 2007-11-11
I used the alternate installation CD For 7.10 and encrypted my laptop hard disk with LUKS.  I was using the laptop when it suddenly ran out of juice and shut down.  Once I plugged it in I was unable to unlock the partition with my password.

I don't often finish my posts with this but: Please help!

---

### Post by Meson on 2007-11-11
Also, is there any way I can determine for sure if the header/entire partition is corrupt?

---

### Post by HermanAB on 2007-11-11
Usually, when an encrypted partition gets damaged, the whole thing is lost.  Try the Ubuntu Live CD and see if that can mount and read the encrypted HDD partitions.

Cheers,

Herman

---

### Post by loko on 2007-11-11
we need information.

how did you try to mount it?
which partition, where do you want to mount it etc.

---

### Post by Meson on 2007-11-11
I believe the hard disk is formatted into a boot partition and an encrypted logical volume.  Then the LVM is divided into the root partition and a swap partition.  Grub boots from the unencrypted boot partition and asks me for my password, then opens up the encrypted volume.

Good news though, for some reason this morning it worked fine ?!  I don't know why it suddenly worked.

I supposed it doesn't matter anyway because I have a pretty thorough backup strategy.  But I think it should also now include my headers!

---

