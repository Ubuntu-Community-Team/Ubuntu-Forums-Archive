---
title: "Accidentally deleted Windows 8."
date: 2015-01-07
forum: General Help
---

### Post by safaoral on 2015-01-07
Hi. I was trying to make dual boot with win8 and ubuntu I accidentaly accepted replace win8 with ubuntu and I closed the pc. When I turn on windows doesnt come. I'm writing this with ubuntu installed on a usb stick.

---

### Post by Tadaen_Sylvermane on 2015-01-07
Reinstall windows from scratch. Only thing to do.

---

### Post by oldfred on 2015-01-08
Did you make an image backup of Windows before install or create the recovery set of DVDs before install, so you can restore system?

Your porduct key is now in UEFI and only applies to the OEM/vendor version your installed.
 Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)

You may be able to go to vendor and some offer the recovery set of DVD's for a nominal charge.

You may be able to use testdisk to restore the NTFS partitions. But if any Windows file is overwriting which is most likely it will not be bootable, but then you may be able to do a repair reinstall.
Partitions you should see. Testdisk may not separately see the system reserved, and you need to restore that also.

 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)

      
 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[URL="http://www.cgsecurity.org/wiki/TestDisk"]http://www.cgsecurity.org/wiki/TestDisk

[/URL]
 Windows 8 has both a Refresh and a Reset option. To find out the details of both, and to decide which best to use, you should check in with the Windows 8 forum:
 [http://www.eightforums.com](http://www.eightforums.com). 
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

[URL="http://www.cgsecurity.org/wiki/TestDisk"]
[/URL]

---

