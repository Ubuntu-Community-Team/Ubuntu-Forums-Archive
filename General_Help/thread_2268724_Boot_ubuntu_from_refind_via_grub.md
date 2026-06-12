---
title: "Boot ubuntu from refind via grub?"
date: 2015-03-11
forum: General Help
---

### Post by Veniamin_R. on 2015-03-11
Greetings!

I have an Ubuntu system which is run by GRUB installed on the MBR partition. I created an EFI partition (on the other GPT-disk) with the refind EFI shell (I load another OS using refind). I want boot my Ubuntu system using refind menu (UEFI boot) and selecting that GRUB loader. What exactly should I write in the appropriate refind stanza to load standard GRUB menu? Or I can do that only using EFI version of GRUB?

PS. If Ubuntu is recommended to be loaded directly from refind then I would have to correct refind stanza every time after a new kernel installation. I don't want to do that.

PS2. I want run GRUB from refind because the GRUB menu is always regenerated from Ubuntu system automatically after a new kernel installation.

Thanks!

---

### Post by oldfred on 2015-03-11
I do not know rEFInd.
The author of rEFInd does sometimes post in askubuntu forum.

But UEFI and BIOS boot modes are not compatible. You have to reboot to switch modes. 
Not sure if then rEFInd can force a reboot as UEFI does have a one time boot into a system option. But not sure if you can even set a BIOS reboot as that option. And rEFInd has always been only a UEFI boot and an update to the older rEFIt boot loader that was mostly used with Macs as they had UEFI long before PCs.

Generally best to have all systems either UEFI or all systems BIOS boot. If Ubuntu is reinstalled in UEFI mode on a gpt partitioned drive, then you could directly boot the other UEFI install or use rEFInd. You would have to fully backup /home and if you installed lots of apps, export a list of installed apps to reinstall them easily. 

Grub is always updated, whether UEFI or BIOS. 
But some of use manually change grub to boot partition, so updates do not matter. Have not tried much with UEFI yet as that works a bit differently. But only required when booting several Ubuntu from one grub.

Note that UEFI is a boot manager, rEFInd is a boot manager, and grub is both a boot manager and a boot loader for Linux. So best not to have too many boot managers as you get too many menus.

---

### Post by Veniamin_R. on 2015-04-08
I solved the problem. Yes, it's right, it's not possible to run mbr version of grub from refind. I had to install and properly setup grub-efi first and then running grub from refind became easy. Now it works properly.

---

