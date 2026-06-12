---
title: "Updating Dell Bios Firmware via OS"
date: 2024-11-22
forum: General Help
---

### Post by sniper8752 on 2024-11-22
Is there a repo I can add to update my Dell Bios Firmware?  I have a Dell XPS 9530 Laptop.

---

### Post by oldfred on 2024-11-22
I would start on the Dell site. But looks only like Windows .exe updater.
Shows end of life & last "BIOS" update 2020
[https://www.dell.com/support/home/en-us/product-support/product/xps-13-9350-laptop/drivers](https://www.dell.com/support/home/en-us/product-support/product/xps-13-9350-laptop/drivers)
[https://www.dell.com/support/home/en-us/product-support/product/xps-15-9530/drivers](https://www.dell.com/support/home/en-us/product-support/product/xps-15-9530/drivers)
[https://www.dell.com/support/home/en-us/drivers/driversdetails?driverid=gdnv7](https://www.dell.com/support/home/en-us/drivers/driversdetails?driverid=gdnv7)

Many Dell update directly from UEFI settings.

---

### Post by dragonfly41 on 2024-11-23
> [COLOR=#000000]Many Dell update directly from UEFI settings.[/COLOR][COLOR=#000000]

I installed rEFInd (supplementary boot manager) and the GUI shows link to Dell firmware update.
I have Inspiron at the moment.[/COLOR]

---

### Post by guiverc on 2024-11-23
I'm using a dell optiplex 7050, and on occasion I get told of firmware updates for my machine.  (*they actually annoy me, as I get nagged that I have to reboot the box to apply fixes; and I only reboot this box once per fornight; and the updates  seem to rollout just after I've rebooted*)

In my case upgrades are handed by firmware-updater snap package, which comes standard with my (*and recent releases*) of Ubuntu, though older releases will use a different package (*deb* in some cases instead of *snap* package)

Are you sure you need a specific repository.

---

### Post by oldfred on 2024-11-25
Dell was one of the first to start using fwupdate.
UEFI/BIOS updates brand model list  for Dell with (uefi >= 0.6.2 & dell >= 0.7.3) 
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)

But old systems were not added.
Older systems that fwupdate does not support
[https://wiki.archlinux.org/title/Flashing_BIOS_from_Linux](https://wiki.archlinux.org/title/Flashing_BIOS_from_Linux)

---

