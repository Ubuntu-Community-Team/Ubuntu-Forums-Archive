---
title: "Is my Hard drive about to die?"
date: 2007-12-06
forum: General Help
---

### Post by gamma on 2007-12-06
My system has been pausing for large gaps of time trying to get I/O from my hard drive. The requests generally time out, but it locks up my system for a while..dmesg is showing a ton of these msgs too
[  122.364000] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  122.364000] ata2.00: (BMDMA stat 0x25)
[  122.364000] ata2.00: cmd c8/00:08:fd:da:18/00:00:00:00:00/e5 tag 0 cdb 0x0 data 4096 in
[  122.364000]          res 51/40:08:fd:da:18/00:00:00:00:00/e5 Emask 0x9 (media error)
[  122.388000] ata2.00: configured for UDMA/100
[  122.388000] ata2: EH complete

I'm attached my output of smartctl -a /dev/sda if someone wants to interpret it.

I just want to play it safe and start backing up data if people think this is the issue.

---

### Post by lucasl on 2007-12-06
Not sure, but it sounds like a very good reason to backup - which you should be doing already.

---

