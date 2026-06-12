---
title: "Got a question, noobish one"
date: 2008-05-31
forum: General Help
---

### Post by LiNuXxToOthEMaX on 2008-05-31
OK, I have two Harddrives, one with Ubuntu, and one with Windows Vista, I want to remove Windows Vista from that second HDD, and put another distro of linux, is that possible? And what about GRUB, would it adjust? or would I have to manually do it.

thanks!

---

### Post by EXCiD3 on 2008-05-31
Just format the partition for the vista hdd and the distro you install should automatically detect the Ubuntu installation and add entries to its grub that it will install.

---

### Post by LiNuXxToOthEMaX on 2008-05-31
> **EXCiD3 said:**
> Just format the partition for the vista hdd and the distro you install should automatically detect the Ubuntu installation and add entries to its grub that it will install.

How would I go about formatting the Vista partition? It's really not a partition, I have 2 Harddrives.

---

### Post by EXCiD3 on 2008-05-31
Well you have the ENTIRE drive as a single partition. Just use the partition managers included with the distro you are using, or install GParted in Ubuntu to format the drive/partition.

---

### Post by Lord Xeb on 2008-05-31
This.

It will likely be /dev/sdb

---

### Post by LiNuXxToOthEMaX on 2008-05-31
> **EXCiD3 said:**
> Well you have the ENTIRE drive as a single partition. Just use the partition managers included with the distro you are using, or install GParted in Ubuntu to format the drive/partition.

Could I technically boot into the Vista partition with the Distro I want, and reformat it from therE?

For example, I put in my Fedora CD or Sabayon or w/e distro, and I could format it from there?

---

### Post by EXCiD3 on 2008-05-31
Its best that you just use the LiveCD from whichever distro you use to format the partition. If you boot into Windows to format its own partition it wont let you. GParted from inside Ubuntu will work fine as long as the drive isnt mounted anywhere. Its just easier with a LiveCD because no partitions are mounted until you actually start the installation.

---

