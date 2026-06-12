---
title: "EDGY system frozen, can only access via ssh &quot;Additional sense: Scsi parity error&quot;"
date: 2007-04-20
forum: General Help
---

### Post by Barleyman on 2007-04-20
I tried to log into my Edgy system this morning and I noticed the CPU was stuck around 50% in my system monitor but my desktop was unresponsive.  I logged in via ssh from another machine and ran top.  My output from top was this.

"Input/output error"


"dmesg" gives me a bunch of these
[17364507.828000] ata1: status=0xb7 { Busy }
[17364507.828000] sd 0:0:0:0: SCSI error: return code = 0x8000002
[17364507.828000] sda: Current: sense key: Aborted Command
[17364507.828000]     Additional sense: Scsi parity error
[17364507.828000] Info fld=0x14caf
[17364507.828000] end_request: I/O error, dev sda, sector 209887703
[17364537.840000] ata1: command 0xc8 timeout, stat 0xb7 host_stat 0x61
[17364537.840000] ata1: translated ATA stat/err 0xb7/00 to SCSI SK/ASC/ASCQ 0xb/47/00
[17364537.840000] ata1: status=0xb7 { Busy }
[17364537.840000] sd 0:0:0:0: SCSI error: return code = 0x8000002
[17364537.840000] sda: Current: sense key: Aborted Command
[17364537.840000]     Additional sense: Scsi parity error
[17364537.840000] Info fld=0x14caf
[17364537.840000] end_request: I/O error, dev sda, sector 209887703


I assume it is a hardware error, but I didn't want to reboot yet, until I have a better idea what is going on.
any ideas?

---

### Post by ashz on 2007-04-20
at a guess, and i mean guess it looks like ur running a raid and one of ur hard disks is packing up... sorry i cant be any more help!!

---

### Post by Barleyman on 2007-04-20
No raid on this system, just two sata disks, one on / and one for /home

---

### Post by Barleyman on 2007-04-20
Well I decided to just shut the system down hard and it came back up fine.

Strange.

---

### Post by franspot on 2007-05-05
I had almost the same error but in my case I'm using dapper
That error is repeating ramdomly. So if you find a solution please let me know

---

