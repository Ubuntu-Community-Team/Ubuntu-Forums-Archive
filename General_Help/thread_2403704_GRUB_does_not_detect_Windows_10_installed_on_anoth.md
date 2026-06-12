---
title: "GRUB does not detect Windows 10 installed on another drive"
date: 2018-10-15
forum: General Help
---

### Post by dd42 on 2018-10-15
Hi,

I have Lenovo Y520 and Ubuntu 16.04 installed on one SSD drive and Windows 10 on another drive (Windows was installed first). Both were installed in UEFI mode. Fast boot and Secure boot are disabled in BIOS. I am able to boot into both OSes by changing the boot order in BIOS but I would like to be able to select just using GRUB without going into BIOS every time. I ran boot-repair and Ubuntu now starts with GRUB but Windows is not detected in its menu.

Note: When I installed Ubuntu, the drive with Windows 10 was not detected at all.

Here is the output of boot-repair:
[http://paste.ubuntu.com/p/VMYgF5RBmr/](http://paste.ubuntu.com/p/VMYgF5RBmr/)

Thanks.

---

### Post by oldfred on 2018-10-15
You are only showing sda drive?
Since you can still boot Windows, drive must not be seen.

If an NVMe drive, you may need firmware updates for SSD.
And UEFI updates from Lenovo.

---

### Post by dd42 on 2018-10-16
There does not seem to be a firmware update for my SSD and I would rather not update BIOS. Thanks for your help I am closing this.

---

