---
title: "Question about USB bootable ubuntu."
date: 2018-11-25
forum: General Help
---

### Post by ludwig00 on 2018-11-25
I just learned about persistent and non-persistent mode and I'm lost, even after reading all the docs provided. 

I just want to install Ubuntu on a SSD, but this persistent/non-persistent thing lost me. Does presistent/non-persistent mode really matters if I just want to boot my PC from the USB and just use the ubuntu installer ? 

As note, I must precise I want to use gnome disk utility and stick with it if I can, since I know this soft the most. Problem is I read about how it was non-persistent mode only. Does it matter ?

---

### Post by oldfred on 2018-11-25
You only need persistence if you want to use live installer for longer term testing and want to be able to save some data onto the flash drive. It is not up-datable, you need full install for that.
You still should use installer to test that your system works, will be a bit slower as flash drives are not as fast as SSD (or HDD). 

Is system newer UEFI or older BIOS?
If newer UEFI be sure to boot in UEFI boot mode from UEFI/BIOS boot menu. Or if you installed Windows, install in same boot mode as you installed Windows.

If you have other drives, generally better to disconnect other drives and only have your new SSD connected (and flash drive installer).

More UEFI info, if you have UEFI in link in my signature.

---

### Post by ludwig00 on 2018-11-25
If I read you write, persitent or non-persistent mode doesn't matter if you just want to use the ubuntu installer (for full-install) that come with it, right ? I want to full-install, not test.

---

### Post by oldfred on 2018-11-25
You use the live installer to do a full install. Mode does not matter.

UEFI or BIOS install?
What brand/model system.
Does live installer work well on your system in live mode?

---

### Post by C.S.Cameron on 2018-11-25
A Live, (non-Persistent), install to USB is all you need as an installer.
If you make the installer from a Windows machine you can use Rufus or UNetbootin or Universal or YUMI, (UEFI).
If you make the installer from a Ubuntu machine you can use Startup Disk Creator or mkusb.
If you are installing to a UEFI machine you can simply extract thr ISO file to a USB and it should boot.

---

