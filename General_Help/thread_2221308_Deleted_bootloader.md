---
title: "Deleted bootloader"
date: 2014-05-01
forum: General Help
---

### Post by CYzMLcT on 2014-05-01
Hello, I accidentally deleted the boot partition on my ubuntu 14.04 computer. I tried using boot-repair to fix it from a live USB, but my computer now repeatedly restarts itself going through the BIOS flash screen without ever actually booting up. the paste from boot repair is here: [http://paste.ubuntu.com/7374063/](http://paste.ubuntu.com/7374063/) I would really rather not reinstall since I have a lot of (big) downloaded programs that I compiled from source on that computer. Any suggestions on how to get boot-repair or another program to fix this?

---

### Post by oldfred on 2014-05-01
You have what looks like a BIOS boot install that should work.

But you have reference to an efi partition in fstab, and your bios_grub is huge. The bios_grub is required for BIOS boot with grub and is usually 1 or 2MB. Your is 100MB which would be more the size for a small efi partition. An efi partition is required for UEFI boot.

How you boot installer is how it installs. UEFI and BIOS are not really compatible so once you start in one mode you cannot change to the other. So if booting in UEFI mode it installs in UEFI mode.

Do you have UEFI/BIOS set to boot in BIOS mode.

Or you can reset bios_grub to efi partition by formatting to FAT32 and if using gparted add boot flag to make it the efi partition. Then use Boot-Repair in UEFI mode to make repairs.

I do prefer to have smaller / (root) partition of 20 or 25GB and then use rest of drive as data or /home.

---

