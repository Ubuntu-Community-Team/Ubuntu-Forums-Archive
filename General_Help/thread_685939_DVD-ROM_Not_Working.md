---
title: "DVD-ROM Not Working"
date: 2008-02-02
forum: General Help
---

### Post by cephus6 on 2008-02-02
I have an older HP Desktop with LG DRD-840B DVD ROM drive installed.

I cannot get this drive to read any disk audio, cd, or DVD.
I get the message cannot eject volume and nothing plays.

I checked the event log and this is the messages left when I insert a disk.
Feb  2 16:58:08 Pavilion kernel: [ 5310.526299]          res 40/00:03:00:00:20/00:00:00:00:00/b0 Emask 0x4 (timeout)
Feb  2 16:58:13 Pavilion kernel: [ 5315.565634] ata2: port is slow to respond, please be patient (Status 0xd0)
Feb  2 16:58:18 Pavilion kernel: [ 5320.549041] ata2: device not ready (errno=-16), forcing hardreset
Feb  2 16:58:18 Pavilion kernel: [ 5320.549063] ata2: soft resetting port
Feb  2 16:58:19 Pavilion kernel: [ 5321.205263] ata2.00: configured for MWDMA1
Feb  2 16:58:19 Pavilion kernel: [ 5321.377179] ata2.01: configured for MWDMA1
Feb  2 16:58:19 Pavilion kernel: [ 5321.377228] ata2: EH complete

I am new to LInux so any help would be appreciated.

Thanks

---

