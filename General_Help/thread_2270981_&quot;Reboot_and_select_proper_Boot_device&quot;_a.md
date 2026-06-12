---
title: "&quot;Reboot and select proper Boot device&quot; after installing Ubuntu on Win 8.1"
date: 2015-03-26
forum: General Help
---

### Post by walid4 on 2015-03-26
So its day 2, I have a Toshiba Satellite-C55 Laptop 16GB Ram, 1.60-2.8 GH Intel core i5 originally had windows 8.1. I have done it all. I have read and done so much, I just dont know what i am doing wrong. 

After installing Ubuntu from USB, I used LinuxLive.USB.Creator to mount iso file onto usb stick (32GB). Changed boot sequence to boot from USB first. Ubuntu gives me the option of trying or installing Ubuntu, I select Install Ubuntu, everything goes smoothly, install completes, asks to restart to make changes. Restart (changed boot sequence to Hard drive), pulled out media prior to restart. Ubuntu wont load, as if it doesnt exist. "Reboot and select proper boot device or insert boot media device and press a key". I have tried this...oh 8 times since yesterday. Changed USB sticks, different formats, etc. I have disabled "secure boot" the boot mode is set to UEFI Boot. The other option I have is "CSM Boot". 

I also ran boot-repair. I have used rufus to mount.

Im not sure what i am doing wrong. Any help would be appreciated.

---

### Post by oldfred on 2015-03-26
Best to post link from Summary report in Boot-Repair.

Is is probably with your UEFI.
Vendors are now modifying UEFI so it is not UEFI. And the "proper boot device" is Windows. 
So many systems have to do a work around.

If you only have Ubuntu you can rename it to be Windows and UEFI will think you are booting Windows but then it will boot grub. Those that dual boot rename bootx64.efi which is a default hard drive boot entry. That then can also be renamed from grub so it boots grub menu.

More details in link in my signature.

Normally Summary report shows this. I do not have Windows but created/renamed one of my UEFI entries. list is from sudo efibootmgr -v 

```
 BootOrder: 0004,0003,0000,0001,0002,000C,0010,0011
Boot0000* ubuntu	HD(1,800,fa000,3195d314-ce88-42ac-beac-d9f80289ac11)File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0001* [COLOR=#ff0000]Windows Boot Manager[/COLOR]	HD(1,800,fa000,3195d314-ce88-42ac-beac-d9f80289ac11)File( \EFI\UBUNTU\[COLOR=#ff0000]SHIMX64.EFI[/COLOR])
Boot0002* UEFI OS	ACPI(a0341d0,0)PCI(1f,2)03120a000000ffff0000HD(1,800,fa000,3195d314-ce88-42ac-beac-d9f80289ac11)..BO
Boot0003* vivid	HD(1,800,fa000,3195d314-ce88-42ac-beac-d9f80289ac11)File(\EFI\VIVID\SHIMX64.EFI)
Boot0004* trusty	HD(1,800,fa000,3195d314-ce88-42ac-beac-d9f80289ac11)File(\EFI\trusty\shimx64.efi)
Boot000C* UEFI OS	ACPI(a0341d0,0)PCI(1f,2)03120a000000ffff0000HD(1,800,fa000,3195d314-ce88-42ac-beac-d9f80289ac11)..BO
Boot0010* UEFI OS	HD(1,800,fa000,3195d314-ce88-42ac-beac-d9f80289ac11)File(\EFI\BOOT\BOOTX64.EFI)..BO
Boot0011* ubuntu	HD(1,800,fa000,3195d314-ce88-42ac-beac-d9f80289ac11)File(\EFI\UBUNTU\GRUBX64.EFI)..BO



```

---

### Post by cariboo on 2015-03-26
On my Toshiba C50-B,  I have to press 0 (zero) when the Toshiba logo shows, in order to get to the boot menu, where I select Ubuntu when I want to boot into it.

---

### Post by coffeecat on 2015-03-27
Moved to a support forum.

*Thread moved to **General Help**.*

---

