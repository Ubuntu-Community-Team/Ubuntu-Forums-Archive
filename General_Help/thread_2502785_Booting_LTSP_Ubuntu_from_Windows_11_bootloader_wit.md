---
title: "Booting LTSP Ubuntu from Windows 11 bootloader with secureboot enabled"
date: 2024-11-29
forum: General Help
---

### Post by allcoms on 2024-11-29
At my workplace we mainly run Windows but we also use LTSP Ubuntu, or at  least we currently do but we might not be able to do so for much longer.


 With the rapidly approaching end of support of Windows 10,  we are moving to Windows 11 which means secureboot will (has to be)  enabled so we can no longer use grub4dos to boot LTSP via the Wiindows  bootmanager like we do currently. Unfortunately we have to use Windows  bootmanager as the main bootloader and we can't switch to GRUB or  refind because of how our deployment system works. Does anyone know a way of booting LTSP Ubuntu from the Windows 11 bootmanager?


 I've found the Super UEFIinSecureBoot Disk which lets you  boot grub2 etc when secureboot is enabled but it is designed to be run  from a USB disk. It would be great if there was something similar that  could be loaded from the Windows 11 bootmanager.
 [URL="https://github.com/ValdikSS/Super-UEFIinSecureBoot-Disk"]https://github.com/ValdikSS/Super-UEFIinSecureBoot-Disk

[/URL]

 I know its possible to boot LTSP from a Windows virtualbox  instance but the video performance is terrible when run under  virtualbox and it ruins the whole user experience plus it doesn't allow  for dual screen displays or 3D/video acceleration etc.

Thanks

---

### Post by deadflowr on 2024-11-29
Is this the client or the server?

---

### Post by yancek on 2024-11-29
If you want to boot from windows and can't use Grub (which can boot with Secure Boot on/off) but need a windows bootloader, you should have better luck at some windows forum.  EasyBCD from neosmart could to this but I don't believe they are allowed by Microsoft  to work on UEFI.  Are you booting all on a network or individual computers.  If individual computers and EFI installs it should be simple. 

[https://neosmart.net/wiki/easybcd/uefi/](https://neosmart.net/wiki/easybcd/uefi/)

---

### Post by Tadaen_Sylvermane on 2024-11-30
> EasyBCD from neosmart could to this but I don't believe they are allowed by Microsoft  to work on UEFI

It's nice living in a world where one company controls what every single person does with their computers these days. Where are the anti trust cases on this front?

---

### Post by oldfred on 2024-12-01
If only booting Ubuntu occasionally, why not just boot from UEFI boot menu?

If UEFI Secure boot on, some systems also have another security settings. They may restrict USB boot or other boot entries. 
Most have a way to authorize or allow other boots in Secure mode. So you may need to review UEFI settings.
Note that Windows updates often update UEFI and that reverts UEFI settings to defaults. Or you may have to redo changes.
And Windows turns on Windows fast startup which sets hibernation flag. If accessing any  NTFS partition from Ubuntu that setting must be off.

---

### Post by allcoms on 2024-12-02
I am only referring to the LTSP client machines. Our LTSP server is running Ubuntu only and doesn't really care about secureboot.

We wouldn't want users interracting with the UEFI menu, not only for security reasons but also because it will be different from machine to machine.

Its very much looking like Windows 11 & secureboot has killed off LTSP for dual boot environments which is real shame. I've always been impressed by how well diskless Linux works.

---

