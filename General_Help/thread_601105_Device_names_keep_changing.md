---
title: "Device names keep changing"
date: 2007-11-02
forum: General Help
---

### Post by sw1ng on 2007-11-02
I have two SATA drives in my computer, one with windows and one with Ubuntu 7.10.

About half the time when I bootup, my linux drive is sda and my windows drive is sdb, but the other half of the time, they switch!

This doesn't screw up my root mounting, because my root is on LVM, but my boot partition is not (it's normally sda1). So I get errors half the time when I try to boot saying no ext2 partition is found and failing to mount /boot.

Now, for those who are not using LVM, you can mount drives by label or UUID instead of device name. There are symlinks in /dev/disk. But for some reason using LVM, I now have to mount the drives from /dev/evms/sda1 or /dev/mapper/sda1. Using /dev/sda1 doesn't work, and since the symlinks for mounting by label and UUID point to the entries in /dev, I can't use that option.

Neither of these problems occurred before I upgraded to 7.10, so I'm guessing it has something to do with  the new kernel (or maybe new udevd?). Can anybody help?

Thanks.

---

