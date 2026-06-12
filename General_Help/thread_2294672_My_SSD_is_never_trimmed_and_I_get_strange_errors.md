---
title: "My SSD is never trimmed and I get strange errors"
date: 2015-09-12
forum: General Help
---

### Post by georgesgiralt on 2015-09-12
Hello Guys !
I own a Lenovo laptop which has an M.2 NGFF format connector. I installed an 128GB SSD from ZTC on it. It is GPT parted, 32 GB for a cache used under windows, and the remaining space serve as my Ubuntu 14.04 LTS installation. 
As the laptop had a normal disk, the /var, /home, /tmp and swap are on this drive in order to minimize the writes on the SSD.
In the logs I get messages like this 
```

[ 7143.640708] ata1.00: exception Emask 0x50 SAct 0x40000000 SErr 0x2c0900 action 0x6 frozen
[ 7143.640711] ata1.00: irq_stat 0x08000000, interface fatal error
[ 7143.640713] ata1: SError: { UnrecovData HostInt CommWake 10B8B BadCRC }
[ 7143.640715] ata1.00: failed command: READ FPDMA QUEUED
[ 7143.640718] ata1.00: cmd 60/40:f0:c0:7a:79/00:00:39:00:00/40 tag 30 ncq 32768 in
[ 7143.640718]          res 40/00:f0:c0:7a:79/00:00:39:00:00/40 Emask 0x50 (ATA bus error)
[ 7143.640719] ata1.00: status: { DRDY }
[ 7143.640721] ata1: hard resetting link
[ 7143.960964] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[ 7143.978854] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[ 7143.978858] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[ 7143.978859] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[ 7144.035742] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[ 7144.035745] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[ 7144.035747] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[ 7144.062170] ata1.00: configured for UDMA/133
[ 7144.071280] ata1: EH complete
[ 9039.449354] ata1.00: exception Emask 0x50 SAct 0x8000000 SErr 0x2c0900 action 0x6 frozen
[ 9039.449357] ata1.00: irq_stat 0x08000000, interface fatal error
[ 9039.449359] ata1: SError: { UnrecovData HostInt CommWake 10B8B BadCRC }
[ 9039.449362] ata1.00: failed command: READ FPDMA QUEUED
[ 9039.449365] ata1.00: cmd 60/08:d8:18:e6:4d/00:00:21:00:00/40 tag 27 ncq 4096 in
[ 9039.449365]          res 40/00:d8:18:e6:4d/00:00:21:00:00/40 Emask 0x50 (ATA bus error)
[ 9039.449366] ata1.00: status: { DRDY }
[ 9039.449368] ata1: hard resetting link
[ 9039.769550] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[ 9039.789528] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[ 9039.789531] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[ 9039.789532] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[ 9039.846400] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[ 9039.846404] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[ 9039.846405] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[ 9039.872854] ata1.00: configured for UDMA/133
[ 9039.881937] ata1: EH complete
[ 9083.452425] ata1.00: exception Emask 0x40 SAct 0x7fffffff SErr 0x8d0800 action 0x6 frozen
[ 9083.452437] ata1: SError: { HostInt PHYRdyChg CommWake 10B8B LinkSeq }
[ 9083.452443] ata1.00: failed command: WRITE FPDMA QUEUED
[ 9083.452454] ata1.00: cmd 61/18:00:38:62:3c/00:00:21:00:00/40 tag 0 ncq 12288 out
[ 9083.452454]          res 40/00:01:00:4f:c2/00:00:00:00:00/00 Emask 0x44 (timeout)
[ 9083.452459] ata1.00: status: { DRDY }
[ 9083.452463] ata1.00: failed command: WRITE FPDMA QUEUED
[ 9083.452472] ata1.00: cmd 61/08:08:28:63:3c/00:00:21:00:00/40 tag 1 ncq 4096 out
[ 9083.452472]          res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask 0x44 (timeout)
[ 9083.452476] ata1.00: status: { DRDY }
[ 9083.452480] ata1.00: failed command: WRITE FPDMA QUEUED
[ 9083.452488] ata1.00: cmd 61/08:10:c8:63:3c/00:00:21:00:00/40 tag 2 ncq 4096 out
[ 9083.452488]          res 40/00:ff:00:00:00/00:00:00:00:00/40 Emask 0x44 (timeout)
[ 9083.452492] ata1.00: status: { DRDY }
[ 9083.452496] ata1.00: failed command: WRITE FPDMA QUEUED
[ 9083.452503] ata1.00: cmd 61/08:18:78:65:3c/00:00:21:00:00/40 tag 3 ncq 4096 out
[ 9083.452503]          res 40/00:01:00:00:00/00:00:00:00:00/00 Emask 0x44 (timeout)
[ 9083.452507] ata1.00: status: { DRDY }
[ 9083.452511] ata1.00: failed command: WRITE FPDMA QUEUED
[ 9083.452518] ata1.00: cmd 61/10:20:18:66:3c/00:00:21:00:00/40 tag 4 ncq 8192 out
[ 9083.452518]          res 40/00:ff:00:00:00/00:00:00:00:00/40 Emask 0x44 (timeout)
[ 9083.452523] ata1.00: status: { DRDY }
[ 9083.452526] ata1.00: failed command: WRITE FPDMA QUEUED
[ 9083.452534] ata1.00: cmd 61/08:28:30:66:3c/00:00:21:00:00/40 tag 5 ncq 4096 out
[ 9083.452534]          res 40/00:01:00:4f:c2/00:00:00:00:00/00 Emask 0x44 (timeout)
[ 9083.452538] ata1.00: status: { DRDY }
[ 9083.452541] ata1.00: failed command: WRITE FPDMA QUEUED
[ 9083.452549] ata1.00: cmd 61/08:30:90:6d:3c/00:00:21:00:00/40 tag 6 ncq 4096 out
[ 9083.452549]          res 40/00:01:00:4f:c2/00:00:00:00:00/00 Emask 0x44 (timeout)
[ 9083.452553] ata1.00: status: { DRDY }
[ 9083.452556] ata1.00: failed command: WRITE FPDMA QUEUED
[ 9083.452564] ata1.00: cmd 61/08:38:a8:6d:3c/00:00:21:00:00/40 tag 7 ncq 4096 out
[ 9083.452564]          res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask 0x44 (timeout)
[ 9083.452568] ata1.00: status: { DRDY }
[ 9083.452571] ata1.00: failed command: WRITE FPDMA QUEUED
[ 9083.452579] ata1.00: cmd 61/08:40:c0:6f:3c/00:00:21:00:00/40 tag 8 ncq 4096 out
[ 9083.452579]          res 40/00:01:00:00:00/00:00:00:00:00/40 Emask 0x44 (timeout)
[ 9083.452583] ata1.00: status: { DRDY }
[ 9083.452586] ata1.00: failed command: WRITE FPDMA QUEUED
[ 9083.452594] ata1.00: cmd 61/08:48:28:72:3c/00:00:21:00:00/40 tag 9 ncq 4096 out
[ 9083.452594]          res 40/00:01:00:00:00/00:00:00:00:00/00 Emask 0x44 (timeout)
[ 9083.452598] ata1.00: status: { DRDY }
[ 9083.452601] ata1.00: failed command: WRITE FPDMA QUEUED
[ 9083.452609] ata1.00: cmd 61/08:50:d0:73:3c/00:00:21:00:00/40 tag 10 ncq 4096 out
[ 9083.452609]          res 40/00:ff:00:00:00/00:00:00:00:00/40 Emask 0x44 (timeout)
[ 9083.452613] ata1.00: status: { DRDY }
[ 9083.452617] ata1.00: failed command: WRITE FPDMA QUEUED
[ 9083.452624] ata1.00: cmd 61/08:58:68:75:3c/00:00:21:00:00/40 tag 11 ncq 4096 out
[ 9083.452624]          res 40/00:01:00:4f:c2/00:00:00:00:00/00 Emask 0x44 (timeout)
[ 9083.452629] ata1.00: status: { DRDY }
[ 9083.452632] ata1.00: failed command: WRITE FPDMA QUEUED
[ 9083.452640] ata1.00: cmd 61/10:60:78:75:3c/00:00:21:00:00/40 tag 12 ncq 8192 out
[ 9083.452640]          res 40/00:01:00:4f:c2/00:00:00:00:00/00 Emask 0x44 (timeout)
[ 9083.452644] ata1.00: status: { DRDY }
[ 9083.452647] ata1.00: failed command: WRITE FPDMA QUEUED
[ 9083.452655] ata1.00: cmd 61/08:68:98:75:3c/00:00:21:00:00/40 tag 13 ncq 4096 out
[ 9083.452655]          res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask 0x44 (timeout)
[ 9083.452659] ata1.00: status: { DRDY }
[ 9083.452662] ata1.00: failed command: WRITE FPDMA QUEUED
[ 9083.452670] ata1.00: cmd 61/08:70:10:81:3c/00:00:21:00:00/40 tag 14 ncq 4096 out
[ 9083.452670]          res 40/00:01:00:00:00/00:00:00:00:00/40 Emask 0x44 (timeout)
[ 9083.452674] ata1.00: status: { DRDY }
[ 9083.452678] ata1.00: failed command: READ FPDMA QUEUED
[ 9083.452685] ata1.00: cmd 60/08:78:f0:e4:4d/00:00:21:00:00/40 tag 15 ncq 4096 in
[ 9083.452685]          res 40/00:01:00:00:00/00:00:00:00:00/40 Emask 0x44 (timeout)
[ 9083.452689] ata1.00: status: { DRDY }
[ 9083.452693] ata1.00: failed command: WRITE FPDMA QUEUED
[ 9083.452701] ata1.00: cmd 61/08:80:00:7c:18/00:00:1f:00:00/40 tag 16 ncq 4096 out
[ 9083.452701]          res 40/00:24:00:00:00/00:00:00:00:00/40 Emask 0x44 (timeout)
[ 9083.452705] ata1.00: status: { DRDY }
[ 9083.452708] ata1.00: failed command: WRITE FPDMA QUEUED
[ 9083.452716] ata1.00: cmd 61/00:88:f8:9a:18/01:00:1f:00:00/40 tag 17 ncq 131072 out
[ 9083.452716]          res 40/00:01:00:00:00/00:00:00:00:00/40 Emask 0x44 (timeout)
[ 9083.452720] ata1.00: status: { DRDY }
[ 9083.452723] ata1.00: failed command: WRITE FPDMA QUEUED
[ 9083.452731] ata1.00: cmd 61/08:90:38:30:fc/00:00:1e:00:00/40 tag 18 ncq 4096 out
[ 9083.452731]          res 40/00:80:00:00:00/00:00:00:00:00/40 Emask 0x44 (timeout)
[ 9083.452735] ata1.00: status: { DRDY }
[ 9083.452739] ata1.00: failed command: WRITE FPDMA QUEUED
[ 9083.452746] ata1.00: cmd 61/08:98:78:30:fc/00:00:1e:00:00/40 tag 19 ncq 4096 out
[ 9083.452746]          res 40/00:01:00:00:00/00:00:00:00:00/40 Emask 0x44 (timeout)
[ 9083.452750] ata1.00: status: { DRDY }
[ 9083.452754] ata1.00: failed command: WRITE FPDMA QUEUED
[ 9083.452761] ata1.00: cmd 61/10:a0:20:30:3c/00:00:21:00:00/40 tag 20 ncq 8192 out
[ 9083.452761]          res 40/00:01:00:00:00/00:00:00:00:00/00 Emask 0x44 (timeout)
[ 9083.452765] ata1.00: status: { DRDY }
[ 9083.452769] ata1.00: failed command: WRITE FPDMA QUEUED
[ 9083.452777] ata1.00: cmd 61/10:a8:40:30:3c/00:00:21:00:00/40 tag 21 ncq 8192 out
[ 9083.452777]          res 40/00:ff:00:00:00/00:00:00:00:00/40 Emask 0x44 (timeout)
[ 9083.452781] ata1.00: status: { DRDY }
[ 9083.452784] ata1.00: failed command: WRITE FPDMA QUEUED
[ 9083.452792] ata1.00: cmd 61/08:b0:90:30:3c/00:00:21:00:00/40 tag 22 ncq 4096 out
[ 9083.452792]          res 40/00:01:00:4f:c2/00:00:00:00:00/00 Emask 0x44 (timeout)
[ 9083.452796] ata1.00: status: { DRDY }
[ 9083.452799] ata1.00: failed command: WRITE FPDMA QUEUED
[ 9083.452807] ata1.00: cmd 61/08:b8:a0:30:3c/00:00:21:00:00/40 tag 23 ncq 4096 out
[ 9083.452807]          res 40/00:01:00:4f:c2/00:00:00:00:00/00 Emask 0x44 (timeout)
[ 9083.452811] ata1.00: status: { DRDY }
[ 9083.452814] ata1.00: failed command: WRITE FPDMA QUEUED
[ 9083.452822] ata1.00: cmd 61/08:c0:d8:50:3c/00:00:21:00:00/40 tag 24 ncq 4096 out
[ 9083.452822]          res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask 0x44 (timeout)
[ 9083.452826] ata1.00: status: { DRDY }
[ 9083.452829] ata1.00: failed command: WRITE FPDMA QUEUED
[ 9083.452837] ata1.00: cmd 61/08:c8:88:54:3c/00:00:21:00:00/40 tag 25 ncq 4096 out
[ 9083.452837]          res 40/00:01:00:00:00/00:00:00:00:00/40 Emask 0x44 (timeout)
[ 9083.452841] ata1.00: status: { DRDY }
[ 9083.452844] ata1.00: failed command: WRITE FPDMA QUEUED
[ 9083.452852] ata1.00: cmd 61/08:d0:48:58:3c/00:00:21:00:00/40 tag 26 ncq 4096 out
[ 9083.452852]          res 40/00:01:00:00:00/00:00:00:00:00/00 Emask 0x44 (timeout)
[ 9083.452856] ata1.00: status: { DRDY }
[ 9083.452859] ata1.00: failed command: WRITE FPDMA QUEUED
[ 9083.452867] ata1.00: cmd 61/08:d8:b0:5a:3c/00:00:21:00:00/40 tag 27 ncq 4096 out
[ 9083.452867]          res 40/00:d8:18:e6:4d/00:00:21:00:00/40 Emask 0x44 (timeout)
[ 9083.452871] ata1.00: status: { DRDY }
[ 9083.452874] ata1.00: failed command: WRITE FPDMA QUEUED
[ 9083.452883] ata1.00: cmd 61/08:e0:20:5c:3c/00:00:21:00:00/40 tag 28 ncq 4096 out
[ 9083.452883]          res 40/00:01:00:00:00/00:00:00:00:00/00 Emask 0x44 (timeout)
[ 9083.452887] ata1.00: status: { DRDY }
[ 9083.452890] ata1.00: failed command: WRITE FPDMA QUEUED
[ 9083.452898] ata1.00: cmd 61/08:e8:b8:5d:3c/00:00:21:00:00/40 tag 29 ncq 4096 out
[ 9083.452898]          res 40/00:ff:00:00:00/00:00:00:00:00/40 Emask 0x44 (timeout)
[ 9083.452902] ata1.00: status: { DRDY }
[ 9083.452905] ata1.00: failed command: WRITE FPDMA QUEUED
[ 9083.452913] ata1.00: cmd 61/08:f0:28:5f:3c/00:00:21:00:00/40 tag 30 ncq 4096 out
[ 9083.452913]          res 40/00:01:00:4f:c2/00:00:00:00:00/00 Emask 0x44 (timeout)
[ 9083.452917] ata1.00: status: { DRDY }
[ 9083.452924] ata1: hard resetting link
[ 9083.772547] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[ 9083.792000] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[ 9083.792007] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[ 9083.792011] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[ 9083.848880] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[ 9083.848886] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[ 9083.848890] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[ 9083.875463] ata1.00: configured for UDMA/133
[ 9083.884568] ata1.00: device reported invalid CHS sector 0
[ 9083.884577] ata1.00: device reported invalid CHS sector 0
[ 9083.884581] ata1.00: device reported invalid CHS sector 0
[ 9083.884584] ata1.00: device reported invalid CHS sector 0
[ 9083.884588] ata1.00: device reported invalid CHS sector 0
[ 9083.884591] ata1.00: device reported invalid CHS sector 0
[ 9083.884594] ata1.00: device reported invalid CHS sector 0
[ 9083.884597] ata1.00: device reported invalid CHS sector 0
[ 9083.884600] ata1.00: device reported invalid CHS sector 0
[ 9083.884603] ata1.00: device reported invalid CHS sector 0
[ 9083.884606] ata1.00: device reported invalid CHS sector 0
[ 9083.884609] ata1.00: device reported invalid CHS sector 0
[ 9083.884612] ata1.00: device reported invalid CHS sector 0
[ 9083.884615] ata1.00: device reported invalid CHS sector 0
[ 9083.884618] ata1.00: device reported invalid CHS sector 0
[ 9083.884621] ata1.00: device reported invalid CHS sector 0
[ 9083.884624] ata1.00: device reported invalid CHS sector 0
[ 9083.884628] ata1.00: device reported invalid CHS sector 0
[ 9083.884631] ata1.00: device reported invalid CHS sector 0
[ 9083.884634] ata1.00: device reported invalid CHS sector 0
[ 9083.884637] ata1.00: device reported invalid CHS sector 0
[ 9083.884640] ata1.00: device reported invalid CHS sector 0
[ 9083.884643] ata1.00: device reported invalid CHS sector 0
[ 9083.884646] ata1.00: device reported invalid CHS sector 0
[ 9083.884649] ata1.00: device reported invalid CHS sector 0
[ 9083.884652] ata1.00: device reported invalid CHS sector 0
[ 9083.884655] ata1.00: device reported invalid CHS sector 0
[ 9083.884660] ata1.00: device reported invalid CHS sector 0
[ 9083.884663] ata1.00: device reported invalid CHS sector 0
[ 9083.884665] ata1.00: device reported invalid CHS sector 0
[ 9083.884698] ata1: EH complete
[11156.657539] ata1.00: exception Emask 0x50 SAct 0x40 SErr 0x2c0900 action 0x6 frozen
[11156.657545] ata1.00: irq_stat 0x08000000, interface fatal error
[11156.657549] ata1: SError: { UnrecovData HostInt CommWake 10B8B BadCRC }
[11156.657553] ata1.00: failed command: READ FPDMA QUEUED
[11156.657559] ata1.00: cmd 60/00:30:e0:31:a5/01:00:2b:00:00/40 tag 6 ncq 131072 in
[11156.657559]          res 40/00:30:e0:31:a5/00:00:2b:00:00/40 Emask 0x50 (ATA bus error)
[11156.657562] ata1.00: status: { DRDY }
[11156.657566] ata1: hard resetting link
[11156.977704] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[11156.995832] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[11156.995835] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[11156.995837] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[11157.052653] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[11157.052658] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[11157.052659] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[11157.079103] ata1.00: configured for UDMA/133
[11157.088213] ata1: EH complete
[11157.121833] ata1.00: exception Emask 0x50 SAct 0x800 SErr 0x2c0900 action 0x6 frozen
[11157.121836] ata1.00: irq_stat 0x08000000, interface fatal error
[11157.121838] ata1: SError: { UnrecovData HostInt CommWake 10B8B BadCRC }
[11157.121840] ata1.00: failed command: READ FPDMA QUEUED
[11157.121843] ata1.00: cmd 60/00:58:e0:35:a5/01:00:2b:00:00/40 tag 11 ncq 131072 in
[11157.121843]          res 40/00:58:e0:35:a5/00:00:2b:00:00/40 Emask 0x50 (ATA bus error)
[11157.121844] ata1.00: status: { DRDY }
[11157.121847] ata1: hard resetting link
[11157.442002] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[11157.459892] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[11157.459904] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[11157.459906] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[11157.516738] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[11157.516750] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[11157.516752] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[11157.543213] ata1.00: configured for UDMA/133
[11157.552324] ata1: EH complete
[11157.582121] ata1.00: exception Emask 0x10 SAct 0x8000 SErr 0x2c0100 action 0x6 frozen
[11157.582124] ata1.00: irq_stat 0x08000000, interface fatal error
[11157.582126] ata1: SError: { UnrecovData CommWake 10B8B BadCRC }
[11157.582129] ata1.00: failed command: READ FPDMA QUEUED
[11157.582132] ata1.00: cmd 60/00:78:e0:38:a5/01:00:2b:00:00/40 tag 15 ncq 131072 in
[11157.582132]          res 40/00:78:e0:38:a5/00:00:2b:00:00/40 Emask 0x10 (ATA bus error)
[11157.582134] ata1.00: status: { DRDY }
[11157.582136] ata1: hard resetting link
[11157.902297] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[11157.920239] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[11157.920243] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[11157.920244] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[11157.977064] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[11157.977068] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[11157.977070] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[11158.003577] ata1.00: configured for UDMA/133
[11158.012687] ata1: EH complete
[11158.034433] ata1: limiting SATA link speed to 3.0 Gbps
[11158.034437] ata1.00: exception Emask 0x10 SAct 0x80000 SErr 0x2c0100 action 0x6 frozen
[11158.034439] ata1.00: irq_stat 0x08000000, interface fatal error
[11158.034441] ata1: SError: { UnrecovData CommWake 10B8B BadCRC }
[11158.034443] ata1.00: failed command: READ FPDMA QUEUED
[11158.034445] ata1.00: cmd 60/00:98:e0:3b:a5/01:00:2b:00:00/40 tag 19 ncq 131072 in
[11158.034445]          res 40/00:98:e0:3b:a5/00:00:2b:00:00/40 Emask 0x10 (ATA bus error)
[11158.034447] ata1.00: status: { DRDY }
[11158.034449] ata1: hard resetting link
[11158.354600] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[11158.372565] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[11158.372568] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[11158.372570] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[11158.429419] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[11158.429423] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[11158.429425] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[11158.455866] ata1.00: configured for UDMA/133
[11158.464963] ata1: EH complete

```

The device reports no errors :
```

root@espineux:~# smartctl -a /dev/sdb
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.16.0-49-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Device Model:     ZTC-SM201-128GB
Serial Number:    E20150305610038
Firmware Version: N1114B
User Capacity:    120 034 123 776 bytes [120 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ACS-2 (minor revision not indicated)
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Sat Sep 12 16:52:59 2015 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x02)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(    0) seconds.
Offline data collection
capabilities: 			 (0x71) SMART execute Offline immediate.
					No Auto Offline data collection support.
					Suspend Offline collection upon new
					command.
					No Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0002)	Does not save SMART data before
					entering power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  10) minutes.
Conveyance self-test routine
recommended polling time: 	 (   2) minutes.

SMART Attributes Data Structure revision number: 1
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x0000   100   100   000    Old_age   Offline      -       0
  5 Reallocated_Sector_Ct   0x0000   100   100   000    Old_age   Offline      -       0
  9 Power_On_Hours          0x0000   100   100   000    Old_age   Offline      -       342
 12 Power_Cycle_Count       0x0000   100   100   000    Old_age   Offline      -       633
160 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       0
161 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       291
163 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       19
164 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       11592
165 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       31
166 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       0
167 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       5
168 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       3000
169 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       100
175 Program_Fail_Count_Chip 0x0000   100   100   000    Old_age   Offline      -       0
176 Erase_Fail_Count_Chip   0x0000   100   100   000    Old_age   Offline      -       0
177 Wear_Leveling_Count     0x0000   100   100   050    Old_age   Offline      -       0
178 Used_Rsvd_Blk_Cnt_Chip  0x0000   100   100   000    Old_age   Offline      -       0
181 Program_Fail_Cnt_Total  0x0000   100   100   000    Old_age   Offline      -       0
182 Erase_Fail_Count_Total  0x0000   100   100   000    Old_age   Offline      -       0
192 Power-Off_Retract_Count 0x0000   100   100   000    Old_age   Offline      -       102
194 Temperature_Celsius     0x0000   100   100   000    Old_age   Offline      -       30
195 Hardware_ECC_Recovered  0x0000   100   100   000    Old_age   Offline      -       269
196 Reallocated_Event_Count 0x0000   100   100   016    Old_age   Offline      -       0
197 Current_Pending_Sector  0x0000   100   100   000    Old_age   Offline      -       0
198 Offline_Uncorrectable   0x0000   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0000   100   100   050    Old_age   Offline      -       0
232 Available_Reservd_Space 0x0000   100   100   000    Old_age   Offline      -       100
241 Total_LBAs_Written      0x0000   100   100   000    Old_age   Offline      -       10085
242 Total_LBAs_Read         0x0000   100   100   000    Old_age   Offline      -       13664
245 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       23184

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%        49         -
# 2  Short offline       Completed without error       00%        49         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

root@espineux:~# 

```
And the HDD does not either :
```

root@espineux:~# smartctl -a /dev/sda
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.16.0-49-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Device Model:     ST500LM021-1KJ152
Serial Number:    W6232BZL
LU WWN Device Id: 5 000c50 08248270f
Firmware Version: 0002LIM1
User Capacity:    500 107 862 016 bytes [500 GB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    7200 rpm
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ATA8-ACS T13/1699-D revision 4
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Sat Sep 12 16:54:43 2015 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(    0) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 (  79) minutes.
Conveyance self-test routine
recommended polling time: 	 (   2) minutes.
SCT capabilities: 	       (0x1031)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   115   099   034    Pre-fail  Always       -       86167368
  3 Spin_Up_Time            0x0003   098   098   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       727
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   072   060   030    Pre-fail  Always       -       18041881
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1664 (241 203 0)
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       681
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   096   000    Old_age   Always       -       4295033003
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   054   044   045    Old_age   Always   In_the_past 46 (0 24 46 26 0)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       100
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       0
193 Load_Cycle_Count        0x0032   096   096   000    Old_age   Always       -       9789
194 Temperature_Celsius     0x0022   046   056   000    Old_age   Always       -       46 (128 0 0 0 0)
196 Reallocated_Event_Count 0x000f   099   099   030    Pre-fail  Always       -       1628 (8335 0)
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       465
254 Free_Fall_Sensor        0x0032   100   100   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%       766         -
# 2  Conveyance offline  Completed without error       00%       764         -
# 3  Short offline       Completed without error       00%       764         -
# 4  Vendor (0x50)       Completed without error       00%       722         -
# 5  Short offline       Completed without error       00%       722         -
# 6  Short offline       Completed without error       00%       634         -
# 7  Vendor (0x50)       Aborted by host               10%       264         -
# 8  Short offline       Completed without error       00%       264         -
# 9  Vendor (0x50)       Completed without error       00%       106         -
#10  Short offline       Completed without error       00%       106         -
#11  Extended offline    Completed without error       00%        55         -
#12  Short offline       Completed without error       00%         0         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

root@espineux:~# 

```

So wondering what may be off I did trim the / (sdb2) FS :
```

root@espineux:~# fstrim -v /
/: 75767685120 bytes were trimmed
root@espineux:~# 

```

As you can see quite the whole partition size where trimmed. I though the trimming occurred at least once a week in the cron jobs (I've modified the script in order to have the unknown ZTC drive trimmed also). 
So could you please tell me what's going wrong and what should I do to keep this SSD running properly ? 
Many thanks in advance for your help and advice !
P.S. : The ZTC device is said to support FS trim by the manufacturer. And I bought it because I had good comment about it by Lenovo laptop users.

---

