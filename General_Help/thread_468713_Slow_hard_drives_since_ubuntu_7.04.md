---
title: "Slow hard drives since ubuntu 7.04"
date: 2007-06-09
forum: General Help
---

### Post by Skyline77 on 2007-06-09
Hi

I've been using ubuntu for about 3 months now and so far its done exactly what I wanted which was raid5 + lvm allowing me to store my important data in a secure fashion and allow me to upgrade the space at a alter date. However since the kernals have been updating 2 of my hard disks have dropped into PIO mode timings without anyway to get them back to DMA. This makes ubuntu very slow when accessing those drives.

My hardware consists of 3 IDE controllers plus the one on the motherboard. I have 7 drives, 6 of which form the raid/lvm array and organized as 2 raid 5 arrarys with 3 disks each. Its been very flakey when booting up as well where I'm frequently having to re-sync the array.

The drives that keep dropping to PIO timings are both on the same controller. An ITE821X and appear as /dev/sdX where as when it worked they appeared as /dev/hdX.

Here is a snip from my dmesg.0

[    5.978200] scsi0 : pata_it821x
[    7.156085] it821x: can't process command 0xF8
[    7.156103] ata1.00: ata_hpa_resize 1: sectors = 240121728, hpa_sectors = 0
[    7.156159] ata1.00: ATA-7: Maxtor 6Y120L0, YAR41BW0, max UDMA/133
[    7.156205] ata1.00: 240121728 sectors, multi 0: LBA 
[    7.156250] ata1.00: Drive reports diagnostics failure. This may indicate a drive
[    7.156304] ata1.00: fault or invalid emulation. Contact drive vendor for information.
[    7.156361] ata1.00: configured for PIO
[    7.156419] scsi1 : pata_it821x
[    8.335428] it821x: can't process command 0xF8
[    8.335446] ata2.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 0
[    8.335500] ata2.00: ATA-5: WDC WD1200BB-00CAA1, 17.07W17, max UDMA/100
[    8.335549] ata2.00: 234441648 sectors, multi 0: LBA 
[    8.335594] ata2.00: Drive reports diagnostics failure. This may indicate a drive
[    8.335647] ata2.00: fault or invalid emulation. Contact drive vendor for information.
[    8.335705] ata2.00: configured for PIO

Just to note I tried running smartctl on the drives but it states that smart is not supported so I can't determine if there is a genuine fault. I know that if I drop to the older kernal where the drives are hdX then the drives work fine.

Any help on solving this is much appreciated.

Cheers

---

### Post by Skyline77 on 2007-06-10
Any thoughts on this? Is there a forum more specific to these type of faults that I should be posting into ?

Cheers

---

