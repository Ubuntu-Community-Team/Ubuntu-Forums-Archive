---
title: "Just updated to 20.04.1 journalctl --b -u smartd not finding anything"
date: 2020-10-08
forum: General Help
---

### Post by David_Partridge on 2020-10-08
```
amonra@Charon:~$ journalctl -b | grep smartd
Oct 08 21:51:35 Charon smartd[944]: smartd 7.1 2019-12-30 r5022 [x86_64-linux-5.4.0-48-generic] (local build)
Oct 08 21:51:35 Charon smartd[944]: Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org
Oct 08 21:51:35 Charon smartd[944]: Opened configuration file /etc/smartd.conf
Oct 08 21:51:35 Charon smartd[944]: Drive: DEVICESCAN, implied '-a' Directive on line 21 of file /etc/smartd.conf
Oct 08 21:51:35 Charon smartd[944]: Configuration file /etc/smartd.conf was parsed, found DEVICESCAN, scanning devices
Oct 08 21:51:35 Charon smartd[944]: Device: /dev/sda, opened
Oct 08 21:51:35 Charon smartd[944]: Device: /dev/sda, [Adaptec  Shared           V1.0], S/N: B81AE929, 27.9 TB
Oct 08 21:51:35 Charon smartd[944]: Device: /dev/sda, does not support SMART Self-Test Log.
Oct 08 21:51:35 Charon smartd[944]: Device: /dev/sda, is SMART capable. Adding to "monitor" list.
Oct 08 21:51:35 Charon smartd[944]: Device: /dev/sda, state read from /var/lib/smartmontools/smartd.Adaptec-Shared-B81AE929.scsi.state
Oct 08 21:51:35 Charon smartd[944]: Device: /dev/sdb, type changed from 'scsi' to 'sat'
Oct 08 21:51:35 Charon smartd[944]: Device: /dev/sdb [SAT], opened
Oct 08 21:51:35 Charon smartd[944]: Device: /dev/sdb [SAT], KINGSTON SVP100S296G, S/N:312Y10B7Y5SK, FW:CJR10202, 96.0 GB
Oct 08 21:51:35 Charon smartd[944]: Device: /dev/sdb [SAT], found in smartd database: JMicron based SSDs
Oct 08 21:51:36 Charon smartd[944]: Device: /dev/sdb [SAT], can't monitor Offline_Uncorrectable count - no Attribute 198
Oct 08 21:51:36 Charon smartd[944]: Device: /dev/sdb [SAT], is SMART capable. Adding to "monitor" list.
Oct 08 21:51:36 Charon smartd[944]: Device: /dev/sdb [SAT], state read from /var/lib/smartmontools/smartd.KINGSTON_SVP100S296G-312Y10B7Y5SK.ata.state
Oct 08 21:51:36 Charon smartd[944]: Monitoring 1 ATA/SATA, 1 SCSI/SAS and 0 NVMe devices
Oct 08 21:51:36 Charon smartd[944]: Device: /dev/sda, state written to /var/lib/smartmontools/smartd.Adaptec-Shared-B81AE929.scsi.state
Oct 08 21:51:36 Charon smartd[944]: Device: /dev/sdb [SAT], state written to /var/lib/smartmontools/smartd.KINGSTON_SVP100S296G-312Y10B7Y5SK.ata.state
amonra@Charon:~$ journalctl -b -u smartd
-- Logs begin at Mon 2018-10-22 13:58:37 BST, end at Thu 2020-10-08 21:55:16 BST. --
-- No entries --
amonra@Char
```

---

### Post by David_Partridge on 2020-10-09
Any ideas?

---

### Post by &amp;wP*!) on 2020-10-09
> **David_Partridge said:**
> Any ideas?

Try
```
journalctl -b -u smartmontools.service
```

---

### Post by David_Partridge on 2020-10-10
Hey!  That worked - when did they change that!  It always used to be -u smartd

```

journalctl -b -u smartmontools
```

also worked

Thanks
David

---

