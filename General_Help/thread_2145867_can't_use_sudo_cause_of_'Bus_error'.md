---
title: "can't use sudo cause of 'Bus error'"
date: 2013-05-16
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2013-05-16
i just assumed the ssd was the problem, and updated it's firmware (which deletes the data on the drive)
and loaded a backup, hopefully this does not happen again
*ssd firmware updates do not destroy data for every controller
---------------original post-------------
running 13.04
Every time i try to use sudo the system give me 'Bus error' and the program exits with status 135
```
~$ sudo su;echo $?
Bus error
135

```
it worked fine this morning
i cant use gksu/gksudo either

could this be a issue with the ssd in the system?

edit my syslog is full of stuff like this:
```
May 16 17:18:08 desktop kernel: [  517.961211]         00 9b 83 e0 
May 16 17:18:08 desktop kernel: [  517.961220] sd 0:0:0:0: [sda]  
May 16 17:18:08 desktop kernel: [  517.961225] Add. Sense: Unrecovered read error - auto reallocate failed
May 16 17:18:08 desktop kernel: [  517.961230] sd 0:0:0:0: [sda] CDB: 
May 16 17:18:08 desktop kernel: [  517.961233] Read(10): 28 00 00 9b 83 e0 00 00 08 00
May 16 17:18:08 desktop kernel: [  517.961249] end_request: I/O error, dev sda, sector 10191840
May 16 17:18:08 desktop kernel: [  517.961275] ata1: EH complete
May 16 17:21:57 desktop kernel: [  746.901085] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
May 16 17:21:57 desktop kernel: [  746.901097] ata1.00: irq_stat 0x40000008
May 16 17:21:57 desktop kernel: [  746.901105] ata1.00: failed command: READ FPDMA QUEUED
May 16 17:21:57 desktop kernel: [  746.901120] ata1.00: cmd 60/08:00:e0:83:9b/00:00:00:00:00/40 tag 0 ncq 4096 in
```

---

### Post by linuxtechguy on 2013-05-17
It looks like you have a failing hard drive, bad cable or failing controller.

---

### Post by pqwoerituytrueiwoq on 2013-05-18
since i was able to update the firmware and load the backup i will assume that was the issue, it is really stupid for a company to ship obsolete firmware n a ssd when updating the firmware on deletes all your data
old version was 1.3 new version is 2.1 on a adata sp600 32gb (30gb effective)

---

