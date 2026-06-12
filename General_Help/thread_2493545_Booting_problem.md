---
title: "Booting problem"
date: 2023-12-18
forum: General Help
---

### Post by woopud on 2023-12-18
I recently installed Ubuntu 23.10 alongside Windows 7, and Windows 10 on my PC, all was good for a while but then out of the blue the GRUB loader disappeared and the PC goes straight to the Windows loader which give me the option to boot Win7 or Win10. I can boot in Win7 fine but Win10 won't boot at all.  What can I do to start troubleshooting?

---

### Post by grahammechanical on 2023-12-18
> but then out of the blue the GRUB loader disappeared

The phrase 'out of the blue' can mean a Windows update which can often break the Grub bootloader. When Windows 10 updates it usually enables Windows fast boot which is a form of hibernation which prevents Grub from seeing the Windows 10 bootloader.

It may be a Windows 7 update which may have overwritten the grub bootloader if Windows 7 is installed in BIOS/Legacy mode. We need more information. Computer specifications please. What order were the operating systems installed? Could you dual boot Windows 7 & 10 before the installation of Ubuntu?

Please use something called Boot-Repair. 

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Run a Ubuntu live session and install Boot-Repair in the live session and then direct it to produce a Boot-Info Summary. Do not choose Recommended Repair. We would like to see the Summary before any attempt is made to repair the booting of Ubuntu. Do click to upload the report to a pastebin. Make a note of the internet address of the pastebin and include it in a post in this forum thread. That will give us some information that we can use to advise you.

Regards

---

