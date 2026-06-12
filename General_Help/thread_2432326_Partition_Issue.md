---
title: "Partition Issue"
date: 2019-11-30
forum: General Help
---

### Post by cmcanulty on 2019-11-30
I recently deleted win 10 parttions from my double boot. Everything was successful. However I have weird partition names now. I would like to change the setup so I have just 2 partitions both primary: sda1 and sda2. Can someone explain how to do this? See the screenshot

[ATTACH=CONFIG]284523[/ATTACH]

---

### Post by Dennis N on 2019-11-30
In msdos partition tables, sda1 sda2 sda3 and sda4 are reserved for primary partitions and the extended partition only. To convert logical to primary, look into FixParts program:
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
It claims it can change logical partitions into primary (1-4). I have not used it.

---

### Post by The Cog on 2019-11-30
Make sure you have a good babkup before trying that. It would not surprise me if converting the partitions from logical to physical left it unbootable, even if the conversion was successful. I could be wrong (never tried such a thing), but it seems like a risk to me. My advice would be not to worry about being on sda5,6. Mine is.

---

### Post by oldfred on 2019-11-30
+1 on The Cog's suggestions.

It will probably create new UUIDs. Then at least the minimum is a full reinstall of grub, not just sudo update-grub which just redoes menu.

If really wanting to convert, you may want to consider the newer gpt partitioning. That also will require a full reinstall of grub plus before that you need a tiny 1 or 2MB unformatted partition with bios_grub flag (if using gparted).

I started to use gpt back in 2010, but had XP on separate MBR drive. Windows requires MBR for BIOS boot, and gpt for UEFI boot.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)

---

### Post by cmcanulty on 2019-11-30
maybe I'll just leave it then, I'm just used to sda 1 & 2 for / and home, thanks all

---

