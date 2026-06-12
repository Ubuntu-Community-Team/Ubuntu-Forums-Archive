---
title: "Creating bootable USB for Atom based CPU and EXT4/BTRFS filesystem"
date: 2024-12-02
forum: General Help
---

### Post by ramiroelliot on 2024-12-02
Looking to create a ubuntu USB bootable.


YUMI and Rufus dont give the ability to setup the USB as EXT4/BTRFS which the Atom core needs. I can use YUMI / rufus to create an already built 14.04.Ext4.img, however thats already built.


What i would like to do is run a newer flavour of ubuntu as bootable, but normal Ubuntu.com images are i386 or AMD. Can anyone advise how to cook a atom based image to enable me to create a usable USB, using a normal i386 image doesnt result in booting, but the ext or btrfs works.

---

### Post by oldfred on 2024-12-02
The binaries for AMD64 will also work on processors that implement the Intel 64 architecture (formerly EM64T), i.e. the architecture that Microsoft calls x64, and AMD called x86-64 before calling it AMD64. They will not work on Intel Itanium Processors (formerly IA-64).

[http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64) &
[https://askubuntu.com/questions/641112/confused-about-amd-intel](https://askubuntu.com/questions/641112/confused-about-amd-intel)

How old is your Atom. Some are very old and BIOS or only work with 32 bit which is now obsolete in Ubuntu.

---

### Post by grahammechanical on 2024-12-03
I would like to provide a quotation from the Debian wiki on the subject of UEFI.

> **Support for mixed-mode systems: 64-bit system with 32-bit UEFI** Some systems have been released containing 64-bit Intel Atom CPUs (such as the Bay Trail), but unfortunately use 32-bit UEFI firmware with no BIOS compatibility mode. Using the 32-bit UEFI x86 support, an i386 installation should be possible on these machines but it won't make the most of the 64-bit hardware. 

Debian Jessie (8.0, released on April 2015) was the first Linux distribution to include full support for mixed-mode UEFI installation on these machines. **As of 2023 and Debian 12 the amd64 installation media (available in netinst form)** includes the UEFI boot loaders necessary for both i386 and amd64 boot. By selecting "64-bit install" from the initial boot menu, debian-installer will install a 64-bit (amd64) version of Debian. The system will automatically detect that the underlying UEFI firmware is 32-bit and will install the appropriate version of grub-efi to work with it. 

> The Debian 12 life cycle encompasses five years: the initial three years of full Debian support, until June 10th, 2026, and two years of Long Term Support (LTS), until June 30th, 2028.

[https://wiki.debian.org/UEFI](https://wiki.debian.org/UEFI)

[https://www.debian.org/releases/bookworm/](https://www.debian.org/releases/bookworm/)

I have tried to find something from Ubuntu documentation about this. Even very old documentation. But I could find nothing useful.

Regards

---

### Post by Holger_Gehrke on 2024-12-03
There is a [long thread on getting an Asus X205TA]("https://ubuntuforums.org/showthread.php?t=2254322") working with Ubuntu. If your system is a 64bit Atom with 32bit firmware, then some of it might be useful to you. I remember this thread because I helped someone install Linux on such a machine but after reading through this decide to go with 32bit Debian since 32bit code is slightly more compact and this machine has 2 GB RAM that can't be upgraded.

Holger

---

### Post by him610 on 2024-12-03
Yes, there are i386 (32bit) releases of Debian based operating systems installable, or bootable from usb sticks. Ubuntu dropped its i386 release a few years ago.

You may want to check out these websites:

debian (i386 or amd64) Bookworm can be downloaded here, [https://www.debian.org/distrib/]("https://www.debian.org/distrib/")

bunsenlabs.org offers both i386 and amd64 releases [https://www.bunsenlabs.org/]("https://www.bunsenlabs.org/")

Raspberry OS for PC (based on 32bit Debian) [https://www.raspberrypi.com/software/operating-systems/]("https://www.raspberrypi.com/software/operating-systems/")

I have installed all three on my Acer atom powered netbook (bios date 2008). It is not much different than installing on a more modern system.

---

