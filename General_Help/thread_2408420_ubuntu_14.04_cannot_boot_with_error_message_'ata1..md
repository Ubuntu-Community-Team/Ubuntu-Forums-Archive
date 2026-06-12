---
title: "ubuntu 14.04 cannot boot with error message 'ata1.00: status: { DRDY }'"
date: 2018-12-18
forum: General Help
---

### Post by liujiazi on 2018-12-18
My dell PC couldn't boot up with 'ata1.00: status: { DRDY }'

Dmesg as follow:

 811 [    2.163623] ata1.00: exception Emask 0x50 SAct 0x20 SErr 0x4090800 action 0xe frozen
 812 [    2.164510] ata1.00: irq_stat 0x00400040, connection status changed
 813 [    2.165392] ata1: SError: { HostInt PHYRdyChg 10B8B DevExch }
 814 [    2.166268] ata1.00: failed command: READ FPDMA QUEUED
 815 [    2.167165] ata1.00: cmd 60/20:28:80:81:99/00:00:41:00:00/40 tag 5 ncq 16384 in
 816 [    2.167165]          res 40/00:28:80:81:99/00:00:41:00:00/40 Emask 0x50 (ATA bus error)
 817 [    2.168900] ata1.00: status: { DRDY }
 818 [    2.169639] ata1: hard resetting link
 819 [    2.524019] Switched to clocksource tsc
 820 [    6.883549] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
 821 [    6.887233] ata1.00: configured for UDMA/133
 822 [    6.888111] ata1: EH complete

Are there any suggestion?

---

### Post by Tadaen_Sylvermane on 2018-12-18
Boot live and run smart checks would be my first thing to do.

---

