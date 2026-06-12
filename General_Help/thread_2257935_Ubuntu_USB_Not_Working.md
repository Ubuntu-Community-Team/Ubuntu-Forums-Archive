---
title: "Ubuntu USB Not Working"
date: 2014-12-23
forum: General Help
---

### Post by colin35 on 2014-12-23
Hello! I have downloaded a ISO ubuntu file and burned it onto a USB using Universal USB INstaller than I changed my BIOS Setup to boot from the USB. Now, when I boot with the USB in it simply says, SYSLINUX 4.07 EDD, I dont remember the rest but I know it was something COPYRIGHT, then like Peter something or another. But Im just trying to boot off of the USB and install Ubuntu. Any help would be greatly appreciated! 

My syslinux.cfg contains: 0
DEFAULT append
LABEL append
CONFIG /isolinux/isolinux.cfg
APPEND /isolinux

---

### Post by sudodus on 2014-12-23
So the computer boots, but stops at the syslinux message. I think there can be a few causes of your problems.

1. The download of the iso file was bad. What file is it? (distro, version, flavour ... and iso file name)

Please check with md5sum according to this link [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

2. The installation to the pendrive was bad. Try another tool, Unetbootin (from Linux or Windows), or mkusb (from Linux) or Win32 Disk Imager (from Windows).

See this link [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

3. It is a kind of iso file that does not fit for your computer. In general,

- use 32-bit systems for old computers and 64-bit systems for new computers and both might work for middle-aged computers.
- use a light-weight flavour of Ubuntu for old computers

Please specify  your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

-o-

*Edit*:

4. And there could be a hardware problem, but it is not likely

By the way, do you intend to make an Ubuntu only installation, or a dual boot with Windows?

---

