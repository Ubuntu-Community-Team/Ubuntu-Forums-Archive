---
title: "A required cd/dvd device driver is missing"
date: 2013-06-18
forum: General Help
---

### Post by bTanmay on 2013-06-18
I own an ASUS K55VM-SX086D laptop. I have been  using Windows 7 and a Ubuntu with a dual boot. I updated my Ubuntu 12.10 to 13.04 and thats when evrything went downhill. 
Firstly my Windows failed to boot, and after a lot of effort I managed to manually rebuild the bcd and got my windows to boot. But in the process somehow the partition with the Ubuntu was wiped, So installed Ubuntu 13.04 using a live USB. Now neither my Windows nor my Ubuntu wouldn't show up in the boot menu. I tried to rescue it with the boot-repair tool in Ubuntu but nothing helped. Next I tried to reinstall windows using a live USB, but that didn't help as i got the following error. "A required cd/dvd device driver is missing." I tried a lot of combinations of configurations with acpi and ide and uefi but nothing worked. So I gave up and deleted my Windows and Ubuntu partition, merged them into one and installed Ubuntu 13.04 on it. I tried to run the Windows 7 USB again but the same error keeps showing up. When i try to browse for the drivers manually, the USB drive doesn't show up in the list of available drives.

I have verified that there is no problem in the live windows USB, by using it on another laptop. I have also tried the SATA:ACPI and the SATA:IDE configurations but nothing seems to work.
I know this is a Windows problem but I have always found solutions to Windows problems in Ubuntu.

---

