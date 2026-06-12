---
title: "Windows after Ubuntu UEFI Environment"
date: 2015-09-29
forum: General Help
---

### Post by andrew265 on 2015-09-29
I currently have Ubuntu 14 installed on my system and want to Dualboot with Windows 7. After trying multiple sources of installation media i find there is no way to boot into the Windows setup. it always sends me straight to the grub. I've had success changing into Legacy but i would have to format the drive to do so. is there any way at all to install Windows after Ubuntu in UEFI? 
BTW this is not a safeboot issue, I've tried that.
Thanks.

---

### Post by oldfred on 2015-09-30
Most Windows 7 installers, and all DVD seem to be BIOS only. But you can copy to flash drive & move some files around so UEFI will work, if 64 bit. Then you can boot Windows installer in UEFI mode and install to a gpt drive. Windows only installs to gpt partitioned drives with UEFI.

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[URL="http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition"]http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition

[/URL]
  How to Create a Bootable UEFI USB Flash Drive for Installing Windows 7, Windows 8, or Windows 8.1 - Also command line install of files to efi partition uses rufus
[http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html](http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html)
[http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx](http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx)
[http://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI](http://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI)

[URL="http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition"]
[/URL]

---

