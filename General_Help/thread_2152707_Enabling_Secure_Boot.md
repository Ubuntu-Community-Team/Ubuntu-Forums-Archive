---
title: "Enabling Secure Boot"
date: 2013-06-08
forum: General Help
---

### Post by JaySeeJC on 2013-06-08
I was wondering, not that all these issues seem to have calmed down a little about secure boot, is it possible to take advantage of it under ubuntu? My primary (only) os on my laptop is ubuntu right now, and so I ask, is it possible to use secure boot on a 100% ubuntu system, from grub up to full boot? If so, how?

---

### Post by oldfred on 2013-06-08
Are you booting with UEFI?

You need the grub shim file and the signed kernel versions. And easy way is to turn secure boot on, boot with Boot-Repair, check secure boot  and update system.
       Please enable SecureBoot in your BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.

But Why?
It is more for Microsoft Marketing to make it difficult to run anything but Windows and let Windows users think they have more security which has been a major Windows failing.
 [http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security

---

### Post by JaySeeJC on 2013-06-08
Seems to have not worked. Attempting to boot in secure boot mode only gives me the error in the picture.

[ATTACH=CONFIG]243667[/ATTACH]

The output of efibootmgr is as follows

```

-> % sudo efibootmgr --verbose
BootCurrent: 0003
Timeout: 0 seconds
BootOrder: 0003,2003,2001,2002
Boot0001* EFI Network 0 for IPv6 (00-26-6C-27-FC-95)     ACPI(a0341d0,0)PCI(1c,0)PCI(0,0)MAC(00266c27fc95,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000RC
Boot0002* EFI Network 0 for IPv4 (00-26-6C-27-FC-95)     ACPI(a0341d0,0)PCI(1c,0)PCI(0,0)MAC(00266c27fc95,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0RC
Boot0003* Ubuntu    HD(1,800,5f000,6f0c3da6-2aae-4c89-892f-3e6f11c78e66)File(\EFI\ubuntu\grubx64.efi)RC
Boot0004* EFI USB Device 1 (SanDisk Cruzer)    ACPI(a0341d0,0)PCI(14,0)USB(1,0)USB(0,0)USB(3,0)HD(1,800,ee8000,aeeb529f-0eaa-4707-80d5-7c8716804c9f)RC
Boot0005* EFI USB Device 2 (SanDisk U3 Cruzer Micro)    ACPI(a0341d0,0)PCI(14,0)USB(1,0)USB(2,0)HD(1,3e,7a6df8,0009fb7b)RC
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC



```

and the only contents of /boot/efi/EFI/ubuntu is grubx64.efi. Now if i'm not mistaken shim should be somewhere in there? Should I copy shim myself and add a boot entry? If so, where would the grubx64.efi file need to be to be loaded by shim?

---

### Post by oldfred on 2013-06-08
I think shim should be there, but it gets renamed to be one of the grub boot efi files. You also have to have the signed kernels, so you have to do it via install unless you know exactly what to copy & rename. That is why I suggest Boot-Repair.

       Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

You should also be able to boot Ubuntu live installer with secure boot on as it has the signed kernel & shim file which has the Microsoft key.

Some info here which looks correct, if you want to manually reconfigure.
[http://ubuntuforums.org/showthread.php?t=2149658&p=12683163#post12683163](http://ubuntuforums.org/showthread.php?t=2149658&p=12683163#post12683163)

 Manually copy efi files to efi partition on flash drive. Toshiba Satellite S855-5378
[http://ubuntuforums.org/showthread.php?t=2107873&p=12599515#post12599515](http://ubuntuforums.org/showthread.php?t=2107873&p=12599515#post12599515)

This was to create a bootable flash drive using shim & signed kernels:
On the Ubuntu filessystem, you should have the signed versions of the following: /usr/lib/shm/shim.efi.signed, /usr/lic/grub/x86_64-efi-signed/grubx64.efi.signed, and /usr/lib/grub/x86_64-efi-signed/gcdx64.efi.signed. 
Copy them all onto the USB stick .../EFI/ubuntu directory without the ".signed" extension. 
Then copy and rename the shim.efi to the USB .../EFI/Boot/bootx64.efi. 
Also copy the grubx64.efi to the EFI/Boot/grubx64.efi. 
There should be the working grub.cfg in the USB .../EFI/ubuntu/grub.cfg

---

