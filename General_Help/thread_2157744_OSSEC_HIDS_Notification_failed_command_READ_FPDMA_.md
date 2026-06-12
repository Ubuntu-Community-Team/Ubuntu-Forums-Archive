---
title: "OSSEC HIDS Notification failed command: READ FPDMA QUEUED and more."
date: 2013-06-26
forum: General Help
---

### Post by John554 on 2013-06-26
Hello,
from what i understand somethings is wrong with hdd  i am trying to find some commands in order to run some tests to check if hard disk is OK

  I will post a full list of logs after REBOOT of system:

"Unknown problem somewhere in the system."
    kernel: ata2.00: failed command: READ FPDMA QUEUED
    kernel:         res 51/40:c8:38:5c:16/00:00:00:00:00/40 Emask 0x409 (media error) <F>
    kernel: ata2.00: error: { UNC }
    kernel: ata2.00: failed command: READ FPDMA QUEUED
    kernel:         res 51/40:78:88:5c:16/00:00:00:00:00/40 Emask 0x409 (media error) <F>
    kernel: sd 1:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
    kernel: sd 1:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
    kernel: md/raid1:md1: read error corrected (8 sectors at 1461400 on sda1)
    kernel: sd 1:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
    kernel: sd 1:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
    kernel: md/raid1:md1: read error corrected (8 sectors at 1461672 on sda1)

Also some of this logs are duplicate or even more.
This logs are sent to me only after restart.

  
Also i think this start after i apply some security/packages updates.

Thanks.

---

### Post by John554 on 2013-06-28
Hello today i restart again the machine and i get huges logs of this messages also the game that i host freeze.
I must know if this is hard disk issue or Linux ubuntu issue in order to open a ticket, thanks.

---

