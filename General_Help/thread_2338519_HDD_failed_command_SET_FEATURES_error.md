---
title: "HDD failed command: SET FEATURES error"
date: 2016-09-29
forum: General Help
---

### Post by bizhat on 2016-09-29
When my computer boots, i get a screen with following errors

```

[    9.470860] ata6.00: exception Emask 0x1 SAct 0x0 SErr 0x0 action 0x0
[    9.470880] ata6.00: irq_stat 0x40000001
[    9.470893] ata6.00: failed command: SET FEATURES
[    9.470908] ata6.00: cmd ef/05:fe:00:00:00/00:00:00:00:00/40 tag 29
[    9.470908]          res 51/04:fe:00:00:00/00:00:00:00:00/40 Emask 0x1 (device error)
[    9.470942] ata6.00: status: { DRDY ERR }
[    9.470954] ata6.00: error: { ABRT }
[    9.506904] ata5.00: exception Emask 0x1 SAct 0x0 SErr 0x0 action 0x0
[    9.506944] ata5.00: irq_stat 0x40000001
[    9.506974] ata5.00: failed command: SET FEATURES
[    9.507008] ata5.00: cmd ef/05:fe:00:00:00/00:00:00:00:00/40 tag 26
[    9.507008]          res 51/04:fe:00:00:00/00:00:00:00:00/40 Emask 0x1 (device error)
[    9.507083] ata5.00: status: { DRDY ERR }
[    9.507110] ata5.00: error: { ABRT }

```

After some time, it boots up.

My Hard Disks are

```

boby@hon-pc-01:~ $ cat /proc/scsi/scsi 
Attached devices:
Host: scsi1 Channel: 00 Id: 01 Lun: 00
  Vendor: ATA      Model: ST31000528AS     Rev: CC46
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi3 Channel: 00 Id: 00 Lun: 00
  Vendor: ATAPI    Model: iHAS124   E      Rev: 4L06
  Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi4 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: WDC WD20EZRX-00D Rev: 0A80
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi5 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: WDC WD20EZRX-00D Rev: 0A80
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi11 Channel: 00 Id: 00 Lun: 00
  Vendor: Marvell  Model: 91xx Config      Rev: 1.01
  Type:   Processor                        ANSI  SCSI revision: 05
boby@hon-pc-01:~ $ 

```

This error happens to both of my "WDC WD20EZRX-00D" HDD's. 

Also no such errors displayed if i boot with Ubuntu 14.04, it all started after i upgrade my PC to Ubuntu 16.04.

I expected this to be a comparability issue with my hardware/kernel and get fixed with newer kernel as it worked fine on Ubuntu 14.04. Even after many kernel upgrades, error won't go away.

Any idea how to fix the error or hide it from showing ?

---

### Post by rastating on 2016-10-15
I've installed 16.04 yesterday (fresh install, no upgrade) and have been noticing the same error during boot. I've not seen any problems whilst using the system, but it just hangs the boot process by about 8-10 seconds?

See my drives below:

```

rastating:~$ cat /proc/scsi/scsi
Attached devices:
Host: scsi4 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: Samsung SSD 750  Rev: 1B6Q
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi5 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: Corsair CSSD-F60 Rev: 1.1 
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi6 Channel: 00 Id: 00 Lun: 00
  Vendor: HL-DT-ST Model: BDDVDRW CH10LS20 Rev: 1.01
  Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi8 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: Corsair Force GT Rev: 5.03
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi9 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: Samsung SSD 750  Rev: 1B6Q
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi15 Channel: 00 Id: 00 Lun: 00
  Vendor: Marvell  Model: 91xx Config      Rev: 1.01
  Type:   Processor                        ANSI  SCSI revision: 05

```

One thing you and I seem to have in common, is that we both have the Marvell 91xx controller, not sure if that may possibly be the issue?

---

### Post by bizhat on 2016-10-15
Thanks for the info.

Yes, only boot process get delayed with that error, no other problem.

I have an open issue at

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1629512](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1629512)

I did try newer kernel as they said, but this error still there.

Look like Marvell controller issue, maybe some driver update can fix it. I will update the bug repot with the info you posted.

---

