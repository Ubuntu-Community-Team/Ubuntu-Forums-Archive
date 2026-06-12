---
title: "Changing the Grub2 loaded in multi-boot Linux"
date: 2018-04-26
forum: General Help
---

### Post by Roger_Williams on 2018-04-26
I've got a laptop and it's multi-boot with 3 distros of Linux. I've got Linux Mint on the internal HDD it was installed first. I've got Kali installed on an external SSD it was installed 2nd. I've got Ubuntu 17.10 installed on a 2nd external SSD that was installed last. My problem is that the laptop is using the Kali Grub loader. Which means when I unplug the SSD with Kali the laptop won't boot. I'd instead like to have it boot from the Linux Mint Grub loader. I've tried the grub-install command and update-grub everything goes through without any errors. When I reboot the Kali Grub loader is what comes up. I can wipe everything out and start fresh which is what I'm considering I'd just like to know if there is a way to switch which Grub loader is used? Everything I search tells me how to change the settings in the Grub and how to change which one boots but I already know how to do all that stuff.

---

### Post by oldfred on 2018-04-26
Is hardware UEFI or BIOS.
Did you install all systems in UEFI or BIOS boot mode.
It may be Kali is BIOS and others UEFI and you just need to change UEFI/BIOS settings to use UEFI?

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Roger_Williams on 2018-04-26
Once I posted this ofcourse I solved my own issue. I booted into Linux Mint and ran the following command.
sudo grub-install --root-directory=/ /dev/sdb then after the installation was successful I ran sudo update-grub which found all the distros. I swear I did that already and it didn't work but perhaps because I didn't fully understand the settings at that time it didn't work. This time I rebooted and it was using the Linux Mint Grub loader with all the distros listed :D
[COLOR=#888888][/COLOR][COLOR=#888888][/COLOR][COLOR=#888888][/COLOR][COLOR=#888888][/COLOR]

---

### Post by Roger_Williams on 2018-04-26
> **oldfred said:**
> Is hardware UEFI or BIOS.
Did you install all systems in UEFI or BIOS boot mode.
It may be Kali is BIOS and others UEFI and you just need to change UEFI/BIOS settings to use UEFI?

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Thanks yes Ubuntu I think is UEFI and the other two are BIOS. Thanks for the links even though I solved it this will be good for future users.

---

