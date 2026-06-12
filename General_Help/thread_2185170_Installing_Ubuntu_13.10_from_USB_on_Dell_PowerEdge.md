---
title: "Installing Ubuntu 13.10 from USB on Dell PowerEdge T110"
date: 2013-11-01
forum: General Help
---

### Post by mwg25 on 2013-11-01
I have a Dell PowerEdge T110 (Xeon 1220v2) server with no OS. From my mac, I was able to save the Ubuntu 13.10 for server iso (x86) and used UNetbootin to save the iso to a USB stick (2GB).

I was hoping to boot the server from USB, and all seemed to be going well, BIOS even detected my USB drive when I plugged it in to the Dell, but for some reason I'm getting a "Missing operating system" error. I checked the USB drive and it appears that UNetbootin put the correct files on it form a cursory glance (although I'm not entirely sure what I should be looking for :confused:).

Should I be able to boot a server with no OS from a UNetbootin created Ubuntu 13.10 USB? 

I had read that there is a USB Emulation setting in BIOS, but I haven't been able to find this in the menus. My understanding is that by default, this is set to on.

I might try wiping the USB stick and recreating the files using UNetbootin. The USB is formatted to MS-DOS FAT16 (should it be formatted some other way?).

Thanks in advance!

---

### Post by TheFu on 2013-11-01
UnetBootIn has never worked well for me.  Don't know why.
Use Yumi - also from the pen-drive-linux website.
I think the USB flash drive needs to be fat32 formated.

Before reloading the OS, check my signature for **boot-repair**. It might work. The only time it didn't work for me was when the BIOS swapped the order of USB and SATA HDDs.

Seems that some systems put the USB HDD devices before the SATA devices in the boot order - that seems to screw up the Ubuntu installer.  My last server install had that issue.  Ended up booting off the flash drive again, using chroot to switch to the already installed HDD partition, then manually running grub-install /dev/sd{xxxx} where xxxx is the real boot HDD, not the flash drive.  Doing this is hard when you aren't too familiar with Linux.

Basically, grub was installed to the wrong HDD ... 

If you don't get everything working, please run **boot-info** and post the link back here for more help.

---

