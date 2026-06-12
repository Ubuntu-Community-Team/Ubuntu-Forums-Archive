---
title: "grub: &quot;invalid efi file path&quot; for win7"
date: 2013-12-25
forum: General Help
---

### Post by roux.jesse on 2013-12-25
I installed windows 7 on one of my drives and ubuntu on the other (I installed ubuntu after win7). Ubuntu works fine and grub works as it should, but when selecting the Windows 7 option I get an "invalid efi file path" error. I searched around and read that using boot-repair can fix it, as the entry in the grub menu for windows is for BIOS and not EFI if I understood it correctly. After running boot-repair, it did not actually do anything, such as create a new boot entry like others have said it does. 

I'm on 12.04 64 bit ubuntu, as well as 64 bit windows 7.

Bootinfo summary: [http://paste.ubuntu.com/6637193/](http://paste.ubuntu.com/6637193/)

---

### Post by oldfred on 2013-12-25
This must be a newer computer with UEFI/BIOS. But you reinstalled Windows 7 in the old BIOS boot mode and Ubuntu in the new UEFI boot mode. Once you start booting in one mode you cannot switch with grub. You can only boot from UEFI/BIOS menu into correct system based on UEFI/BIOS settings. You may have to turn UEFI on to boot Ubuntu and turn UEFI off or turn on CSM/BIOS/Legacy to boot Windows. Some auto switch if configured in that mode, but you still have to choose from UEFI menu or one time boot key.

It also looks like the 750GB drive was gpt. When you installed Windows it converted to MBR(msdos) with the 4 primary partition limit, but left the gpt backup partition table. All Linux tools will have issue with drive as it now is both MBR & gpt. Best to remove backup gpt data with fixparts.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

You could also convert 750GB drive back to gpt and install Windows 7 in UEFI mode.
      
 Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

---

### Post by roux.jesse on 2013-12-26
> **oldfred said:**
> This must be a newer computer with UEFI/BIOS.** But you reinstalled Windows 7 in the old BIOS boot mode and Ubuntu in the new UEFI boot mode.**

Yep, that turned out to be the problem. I setup my boot order to boot the DVD as UEFI but when I put in the windows disk for some reason booting into UEFI isn't an option, so windows was under BIOS and ubuntu UEFI. I just cleared out my ubuntu install and did it under BIOS and it works fine now. Thanks

---

