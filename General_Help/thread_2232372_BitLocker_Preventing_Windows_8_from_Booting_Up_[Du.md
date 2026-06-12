---
title: "BitLocker Preventing Windows 8 from Booting Up [Dual Boot / Surface Pro]"
date: 2014-07-01
forum: General Help
---

### Post by AmagicalFishy on 2014-07-01
Hi, everyone.

I've just installed Ubuntu on my Surface Pro (disabled Secure Boot and all that good stuff) alongside Windows 8. 

When I get to the Grub menu, there is a "Windows Boot Manager" option. Wanting to boot into Windows, I click that. I get a "Preparing BitLocker recovery" screen, and have to enter some obscenely long code. I enter said code, and apparently "unlock" the drive. I'm told the tablet needs to restart before I can access the drive, so it restarts...

... into the Grub menu, wherein the whole process starts over again.

Can anyone give me a hand? I'm thinking I have to reinstall the Windows 8 Bootloader from Ubuntu or something. Boot-repair seems to work ok (with all the EFI options checked), except at the end it gives me an error regarding the location of my boot partition; it's too far away, apparently.

Thanks for any help anyone can offer

---

### Post by oldfred on 2014-07-01
The warning on boot too far from start of drive only applies to older BIOS based or sometimes external USB drives. You can ignore that error. Have yet to see a UEFI based (or newer) system need that fix.

You cannot install a Windows boot loader from Linux. You need your Windows repair flash drive that you make when you get system.

And with BIOS BitLocker took over MBR, so you could not install grub to MBR, Not sure how BitLocker works with UEFI booting?? You probably need to have BitLocker repair tools in your Windows repair flash drive.

If you used Boot-Repair's fix on buggy UEFI undo that, so you directly boot Windows from UEFI menu.
       Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

---

### Post by AmagicalFishy on 2014-07-01
Ah.

I actually fixed the problem. I went into CMD from Windows 8's Troubleshoot screen and disabled Bitlocker

---

