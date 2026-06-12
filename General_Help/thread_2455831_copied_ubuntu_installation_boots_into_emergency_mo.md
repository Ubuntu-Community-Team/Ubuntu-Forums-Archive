---
title: "copied ubuntu installation boots into emergency mode (Raspberry Pi)"
date: 2020-12-28
forum: General Help
---

### Post by areslagae on 2020-12-28
Hi,

I copied a working Ubuntu installation from a microsd card to an usb flash drive.
More specifically, I copied the files on the "system-boot" fat32 partition and on the "writable" ext4 partition (cp -ax) containing the root filesystem.

However, the copied installation on the usb flash drive does not work. More specifically, the installation boots and mounts the root filesystem but for some reason boots into emergency mode (see attached image).

This operation does work with Raspberry Pi OS.

Does anyone know what is going on and how to solve this?

(Background: I am trying to create a multi-boot setup for a Raspberry Pi, since none of the bootloaders allow custom paritioning.)

[ATTACH=CONFIG]287639[/ATTACH]

---

### Post by areslagae on 2020-12-30
anyone?

---

### Post by #&amp;thj^% on 2020-12-30
This works for me: [https://www.raspberrypi.org/forums/viewtopic.php?t=211290](https://www.raspberrypi.org/forums/viewtopic.php?t=211290)
EDIT: BTW Gnome is not the best DE for a PI Device.  (XFCE Mate LXDE)

---

### Post by areslagae on 2021-01-07
Meanwhile I did some more experiments.

My setup is indeed similar to the link above. I have made a dual boot Raspberry Pi OS / Ubuntu USB stick. I use an USB stick with a single fat32 boot partition and two ext4 partitions, one for Raspberry Pi OS / Ubuntu. I download the Raspberry Pi OS / Ubuntu images, mount them, and directly dd the rootfs partitions to the USB stick partition. I swap out the files on the boot partition depening which OS I want to boot.


This seems to work quite robustly for Raspberry Pi OS but not so much for Ubuntu:
- changing a LABEL to a PARTUUID or the other way around in either cmdline.txt or /etc/fstab tends to break the Ubuntu install, either right away or at some later time later
- updating the Ubuntu install often seems to break it (hang at boot, booting into emergency mode, ...)
Not entirely sure what is going on.

=> If anyone has pointers w.r.t. the issues above they are of course welcomed.

=> Why is there no "regular" Ubuntu installer for Raspberry Pi that will allow you to partition and install? Especially now that users are moving away from sdcards to USB3 flash disks and ssd disks.

---

