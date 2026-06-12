---
title: "Boot Windows 8 ISO from GRUB2"
date: 2013-10-21
forum: General Help
---

### Post by renatose2 on 2013-10-21
Hey you all!
I've been using from 5 years or so and I could always take care of any issues I had with what I could find on the Internet.
However after I bought a new laptop (Samsung 700Z5C-S02PT) that came with Windows 7 and then I installed Ubuntu 12.10 (and tried 12.04 to check if there were less issues). It worked seamlessly as it were with UEFI disabled.
Some months then I activated UEFI in the BIOS menu, installed Win8 and ubuntu 13.04 and it worked okay with some issues i could take care of.
I upgraded Win8 to 8.1 preview and it got some problems shutting down so often I had to press long the power button to power it of even when restarting. Then i got issues booting and i had to boot a dvd/usb with a win8 image to recover its boot and it never messed with grub menu.
Some time ago while I was trying to create an entry for windows on UEFI other than grub i issued the command ```
sudo install-grub
``` and since then I lost access to my BIOS (version P05AAG) menu so pressing F2 does nothing. So now I can't boot to windows to try to reflash my bios neither can I boot from a USB/DVD.

[B]I have grub2 and ubuntu 13.04 working and Windows 8.1 unbootable and this laptop has an integrated 8GB SSD in which i flashed windows 8 iso.
However I don't know how boot from a usb stick/ a dvd/ an iso file in a partition/ the iso's files on a partition from grub2.[/B]

I believe that once I can boot into windows again i'll be able to reflash the bios and get access to its setup again.

---

### Post by fantab on 2013-10-21
You must install-grub-efi or something like that. Check with synaptic what it is.

Try [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"), it can fix a whole lot of grub issues with UEFI.

---

### Post by oldfred on 2013-10-21
If still the ISO file, it is probably not directly bootable. Grub2 loopmounts many ISO directly but the ISO has to be configured for that. Ubuntu desktop works, but server does not.

My only experience with newer Windows was making a Windows 7 repair flash drive. But to do that I had to install it to a CD to make it bootable and boot the CD and use Windows commands to write the flash drive. I was then able to install grub into the Windows repairCD and use it to boot, but that was a standard chainload type entry.

---

### Post by renatose2 on 2013-10-21
I could boot into the dvd files after extracting them to a new partition in fat32 and using the same commands in grub to boot it as if it were a windows instalation. I pointed it to an .efi file (bootx64.efi i think) that was in there and it worked nicely!
But I can't reinstall the same BIOS version as it won't let me. afaik i'll have to wait for samsung to release an update to my bios.

However I was able to retrieve a P05AAG.rom file and WinFlash. So if anybody has any way to reflash it with windows or ubuntu I'd be very pleased to know!

---

