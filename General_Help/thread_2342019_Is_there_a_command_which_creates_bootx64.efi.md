---
title: "Is there a command which creates bootx64.efi ?"
date: 2016-11-03
forum: General Help
---

### Post by viswesh2 on 2016-11-03
Hi,

I have a ubuntu system with uefi.

I ran a sudo grub-install --target=x86_64-efi --efi-directory=/boot/efi/, which creates the grubx64.efi under \EFI\ubuntu, but i dont see the default bootloader \EFI\BOOT\bootx64.efi being created. I understand that, i could copy grubx64.efi to bootx64.efi, but i am just wondering, if there is a command to create the default/fall back bootloader.

Thanks.

---

### Post by viswesh2 on 2016-11-03
Checked the grub code. We could pass --removable option to grub-install to create BOOTx64.efi :-)

sudo grub-install --removable --target=x86_64-efi --efi-directory=/boot/efi/

---

### Post by oldfred on 2016-11-03
I have only used the --removable version of grub install to a flash drive with no system. Just so I can have a grub.cfg to loopmount my ISO which I have to manually configure.
That does not then have an automatically updated version of grub.cfg.

If you copy shimx64.efi to /EFI/Boot and rename to bootx64.efi, then that version is hard coded to find the other parts of grub that are in ESP in /EFI/ubuntu folder. And then it uses /EFI/ubuntu/grub.cfg which has just a configfile entry to find full grub.cfg in your install.

Boot-Repair now copies shimx64.efi to bootx64.efi/
 
 Boot-Repair now creates  bkpbootx64.efi and copies shimx64.efi as bootx64.efi. This is a hard drive default or fallback boot entry in UEFI.
'Use the standard EFI file' in advanced options.
[https://bugs.launchpad.net/boot-repair/+bug/1531178](https://bugs.launchpad.net/boot-repair/+bug/1531178) 

Bug on issue in Debian:
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=746662](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=746662)

---

### Post by viswesh2 on 2016-11-04
Copying grubx64.efi to bootx64.efi is not a good solution anymore ? Is it better to move shimx64.efi to bootx64.efi (Since boot-repair does the same). 

One more behavior which i saw that, suppose i deleted all my boot entries, but the ESP partition contains both ubuntu and fedora, the boot entries are automatically created. But if i create a new directory under /EFI, say dummy and include a grubx64.efi and shimx64.efi, it doesnt create a boot entry for files in dummy. I was thinking firmware is not strict about which all entries to create(except for the presence of some .efi file)

---

### Post by oldfred on 2016-11-04
I believe I copy grubx64.efi as I do not plan on using Secure Boot. And if later I did have to start using Secure boot would change at that time.
Shimx64.efi works for both Secure boot & standard UEFI boot, so that is why Boot-Repair copies it. 

I do not think UEFI creates most entries. It seems most will create the Windows one, some create the fallback or hard drive entry. 
But grub install  adds the ubuntu entries using efibootmgr.

I do not have Windows, but multiple versions of Ubuntu. Each new install of Ubuntu overwrites my /EFI/ubuntu. So I have learned to back up my ESP.

With grub2 BIOS you could change name . GRUB_DISTRIBUTOR is defined in /etc/default/grub.  So I changed that. It then used that name to create new UEFI folder and entry in UEFI. But because grub was hard coded somewhere to only load /EFI/ubuntu/grub.cfg every UEFI entry booted the one install in /EFI/ubuntu/grub.cfg. Someday I may try to track that down, but some effort a year or two ago could not find much detail. It has to be somewhere in grub2 as other systems using grub2 have their own entries loading from their folder in ESP.

---

