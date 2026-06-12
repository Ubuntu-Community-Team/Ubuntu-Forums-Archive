---
title: "Can't remove Ubuntu launcher from BIOS?"
date: 2017-01-07
forum: General Help
---

### Post by pnk314 on 2017-01-07
I decided to uninstall Ubuntu from my computer. I deleted the partition it was in and put everything back to how it was. I removed the boot option from the BIOS, but every time I restart it is back again. How do I completly remove it?
Here's a picture if it helps.
[IMG]http://imgur.com/a/OHjdn[/IMG]

---

### Post by thecrazydude778 on 2017-01-08
Have you tried using GParted yet? If not try using the GParted Live edition ([http://downloads.sourceforge.net/gparted/gparted-live-0.27.0-1-i686.iso](http://downloads.sourceforge.net/gparted/gparted-live-0.27.0-1-i686.iso)) and deleting _***all***_the partitions from there (that usually works). Also I don't see any picture and there's no attachment as well.

---

### Post by ajgreeny on 2017-01-08
Is this really a BIOS machine or does it use UEFI firmware?

UEFI will have put the Ubuntu bootloader into a separate partition on your drive that may be called ESP or EFI and removing the Ubuntu partition will not have removed the Ubuntu bootloader from that.
I'm not sure how you deal with that in Windows but do a search for that partition, and see if there is a folder in it called efi, and in that, another subfolder named ubuntu as well as a windows subfolder.

You may need to remove that ubuntu folder, but wait for others who know Windows and its boot procedures better than I, before actually doing anything else just yet.

---

