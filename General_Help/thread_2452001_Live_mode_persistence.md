---
title: "Live mode persistence"
date: 2020-10-14
forum: General Help
---

### Post by vkkindia on 2020-10-14
Hi,

A doubt on how to create a working persistence in live usb

After dd to pen drive ( and in grub menu added persistence)
I  created a ext4 partition with label   writable ( even tried with casper-rw) but it cannot store my saved files or settings.

when checked the mounts
the /dev/sdb3 (the ext4 partition of pen drive) is mounted as /var/log only.

What am i doing wrong.

---

### Post by ajgreeny on 2020-10-14
Why not use mkusb and then choose the option to create persistence in one of the early screens that appear; much easier than your way unless you need a very large persistent disk.
See [https://help.ubuntu.com/community/mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent) for much more detail; I never bother with persistence so have no experience of this but my quick read through suggests that this way can make a large persistent partition.

---

### Post by C.S.Cameron on 2020-10-14
Here is a step by step for building a persistent USB by hand.
[https://askubuntu.com/questions/1227221/simple-hand-made-persistent-usb-that-boots-either-bios-or-uefi/1227225#1227225](https://askubuntu.com/questions/1227221/simple-hand-made-persistent-usb-that-boots-either-bios-or-uefi/1227225#1227225)
This is meant as a learning experience, mkusb is simpler.

---

### Post by HermanAB on 2020-10-15
BTW, live persistent media installation is one of those things that sounds very useful but in practice is so full of gotchas, that it isn't really worth the hassle.  One can just as well do a normal install on a SD card or USB stick.  It amounts to the same thing and works more reliably.

---

### Post by C.S.Cameron on 2020-10-15
> **HermanAB said:**
> One can just as well do a normal install on a SD card or USB stick.  It amounts to the same thing and works more reliably.

I agree mostly, but a Full install USB should boot on both BIOS and UEFI mode computers and include a data partition that works on both Windows and Linux machines. This can get a little complicated for a new user.

Sudodus has created an Ubuntu image file that once flashed to a USB drive will produce a Full install of Ubuntu. This method should be easy enough for the newest user.

[https://phillw.net/isos/linux-tools/uefi-n-bios/dd_unb_ubuntu-20.04_15GB_2020-06-26.img.xz](https://phillw.net/isos/linux-tools/uefi-n-bios/dd_unb_ubuntu-20.04_15GB_2020-06-26.img.xz)

The image is 2GB to download and extracts to 15GB on disk, ready for the addition of a FAT32 or NTFS data partition.

The initial password is "changeme".

More info can be found here: [https://askubuntu.com/questions/1283587/install-ubuntu-to-a-sd-card/1283628#1283628](https://askubuntu.com/questions/1283587/install-ubuntu-to-a-sd-card/1283628#1283628)

---

