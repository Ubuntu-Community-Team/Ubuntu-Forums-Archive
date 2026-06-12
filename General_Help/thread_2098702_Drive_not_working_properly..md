---
title: "Drive not working properly."
date: 2012-12-27
forum: General Help
---

### Post by NenadSpaske on 2012-12-27
Hi, i have a probem my drive isnt recognizing CDs only DVDs, but on my previous OS it was recognizing both. Help ? 
Ubuntu version 12.10.

---

### Post by catalin.vasilescu on 2012-12-27
Did you check with :
dmesg |grep -i dvd  or cd-rom
grep -i dvd  /var/log/messages

---

### Post by NenadSpaske on 2012-12-27
Ok, so i checked first two things, for third one says the directory dosent exist.
[    0.821483] ata1.01: ATAPI: PIONEER DVD-RW  DVR-112D, 1.21, max UDMA/66
[    0.942670] scsi 0:0:1:0: CD-ROM            PIONEER  DVD-RW  DVR-112D 1.21 PQ: 0 ANSI: 5

[    0.942670] scsi 0:0:1:0: CD-ROM            PIONEER  DVD-RW  DVR-112D 1.21 PQ: 0 ANSI: 5
[    0.948970] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.949161] sr 0:0:1:0: Attached scsi CD-ROM sr0
.

---

