---
title: "Windows 8 UEFI Weird Booting Issues"
date: 2013-04-06
forum: General Help
---

### Post by rL1rj19Ko2 on 2013-04-06
Hello all, I have recently uninstalled Ubuntu 12.10 and reformatted my HDD to its factory state because I had a lot of problems with my dual boot configuration, much of which I'm blaming on this being my first time doing something like this. But hey, I did it to learn, and that's what I'm doing! Everything is working fine, but now when I look into my EasyBCD bootloader tool in Windows, there are about 8 boot entries for Ubuntu, and the same goes when I interrupt startup and select "Boot Devices." When I select one of the entries in Boot Devices, it takes me to grub rescue and says "the partition does not exist" because it is pointing to a partition that I have deleted. I have deleted all of the entires from EasyBCD but everytime I reboot they reappear. I believe that they are entries in my Windows bootloader that have been created by incorrectly installing Ubuntu. I just want all of this gone and my machine back to booting directly into Windows with that being the only option because I plan to reinstall Ubuntu a completely different way in order to make it appear in my Windows 8 OS selection screen (It's much prettier :)) and I think that all of these other entries will be an issue. Especially because I am practically OCD and I know they're still there :mad:. Any help is greatly appreciated!

---

### Post by oldfred on 2013-04-07
I do not know how EasyBCD works. But UEFI saves info in its memory where old BIOS saved nothing.
Some users that uninstalled had to go into UEFI to delete the save ubuntu boot entries. So I guess EasyBCD must be seeing entries in UEFI?

Instead of editing entry like this poster, just delete entries.
       > Enter your UEFI menu, select "Boot maintenance manager", then "Boot options", then "Add boot option", then "NO VOLUME LABEL,....Primary,Slave...1, GPT,..", then browse the /EFI/ubuntu/ folder via the UEFI boot menu, and select the grubx64.efi . Give it the name you want (eg "Precise"), then "Commit Changes and exit", then Enter. 
And to remove entries as UEFI remembers them.
UEFI system only shows ubuntu. Delete ubuntu entry & reboot a couple of times & it resets to defaults including drives & USB ports.

---

### Post by rL1rj19Ko2 on 2013-04-08
> **oldfred said:**
> I do not know how EasyBCD works. But UEFI saves info in its memory where old BIOS saved nothing.
Some users that uninstalled had to go into UEFI to delete the save ubuntu boot entries. So I guess EasyBCD must be seeing entries in UEFI?

Instead of editing entry like this poster, just delete entries.
       
And to remove entries as UEFI remembers them.
UEFI system only shows ubuntu. Delete ubuntu entry & reboot a couple of times & it resets to defaults including drives & USB ports.

Great, thanks. I'll give this a shot when I get home.

---

