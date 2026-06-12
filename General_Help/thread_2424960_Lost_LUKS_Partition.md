---
title: "Lost LUKS Partition"
date: 2019-08-18
forum: General Help
---

### Post by jmichael2 on 2019-08-18
I had a data-only drive encrypted with LUKS. I was in Windows reformatting 2 live CDs using the Disk Management tool. I'm not sure how but my LUKS drive ended up being reformatted as well. It was a single encrypted ext4 partition. I booted into a live CD and GParted shows these partitions on the data drive:

/dev/sdb1 - Microsoft reserved partition - file system unknown - 15.98mb - msftres
unallocated - - unallocated - 3.64tb

I am performing a quick scan with testdisk right now but I'm not sure if I'm doing it right. Should I be searching for "ext2/ext3" partition type for the underlying ext4 partion or "other" for the LUKS partition? And how do I proceed afterwards?

Any help would be greatly appreciated. I had over 3tb of data stored on that drive.

---

### Post by haplorrhine on 2019-08-18
First response!!!

I would try the terminal next.
[https://askubuntu.com/questions/626353/how-to-list-unmounted-partition-of-a-harddisk-and-mount-them](https://askubuntu.com/questions/626353/how-to-list-unmounted-partition-of-a-harddisk-and-mount-them)

Maybe EFI vs UEFI is relevant.  wikipedia.org/wiki/Unified_Extensible_Firmware_Interface

> [Intel]("https://en.wikipedia.org/wiki/Intel")[FONT=sans-serif] developed the original [/FONT]**Extensible Firmware Interface ([B]EFI) specification. Some of the EFI's practices and data formats mirror those from [Microsoft Windows]("https://en.wikipedia.org/wiki/Microsoft_Windows").[SUP][[4]]("https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#cite_note-4")[/SUP][SUP][[5]]("https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#cite_note-Matthew_Garrett-5")[/SUP] In 2005, UEFI deprecated EFI 1.10 (the final release of EFI). The [Unified EFI Forum]("https://en.wikipedia.org/wiki/Unified_EFI_Forum") is the industry body that manages the UEFI specification.**[/B]

---

