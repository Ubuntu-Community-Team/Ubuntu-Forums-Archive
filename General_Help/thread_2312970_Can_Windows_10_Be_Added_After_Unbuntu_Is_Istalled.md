---
title: "Can Windows 10 Be Added After Unbuntu Is Istalled?"
date: 2016-02-08
forum: General Help
---

### Post by grace3 on 2016-02-08
I nomally install Windows before Ubuntu, in a dual-boot config; but can this be done in the reverse order?

Thanks, Grace

---

### Post by Vladlenin5000 on 2016-02-08
Yes, it can but it makes things unnecessarily more difficult. Also Windows tends to prefer being installed in the first primary partition (where applicable).
Installing Windows after Ubuntu will override the boot loader and then you need to find a way to boot (or chroot into) Ubuntu to fix that.

In a nutshell, if you really need dual boot - you probably don't, you just think you do like in the other question I replied to recently - then always install Windows first.

---

### Post by oldfred on 2016-02-08
UEFI or BIOS.
Either way you can install second, but partitions required are different.

Windows only boots from MBR partitioned drives with BIOS. You must have a primary partition formatted NTFS with the boot flag.

Windows only boot from gpt partitioned drives with UEFI. It recommends several partitions, but ESP - efi system partition is shared by all installs.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

