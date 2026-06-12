---
title: "harddisk stop spinning"
date: 2008-04-27
forum: General Help
---

### Post by ultimatsz on 2008-04-27
```
Apr 27 10:20:29 ultima-ubuntu kernel: [  614.787366]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Apr 27 10:20:34 ultima-ubuntu kernel: [  619.822416] ata1: port is slow to respond, please be patient (Status 0xd0)
Apr 27 10:20:39 ultima-ubuntu kernel: [  624.801623] ata1: device not ready (errno=-16), forcing hardreset
Apr 27 10:20:39 ultima-ubuntu kernel: [  624.801632] ata1: soft resetting link
Apr 27 10:20:39 ultima-ubuntu kernel: [  624.982070] ata1.00: configured for UDMA/100
Apr 27 10:20:39 ultima-ubuntu kernel: [  624.982089] ata1: EH complete
Apr 27 10:20:39 ultima-ubuntu kernel: [  624.984124] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Apr 27 10:20:39 ultima-ubuntu kernel: [  624.984451] sd 0:0:0:0: [sda] Write Protect is off
Apr 27 10:20:39 ultima-ubuntu kernel: [  625.008060] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
```

problem can be solved by changing to ide rather than using atapiix. but it makes the computer slower.

the above code is a common issue among users using sata.

need help in solving this issue.

---

### Post by ultimatsz on 2008-06-22
any helps other than noapic nolapic combined_mode=libata irqpoll?

mine still hangs with cd in drive so...

laptop.

---

