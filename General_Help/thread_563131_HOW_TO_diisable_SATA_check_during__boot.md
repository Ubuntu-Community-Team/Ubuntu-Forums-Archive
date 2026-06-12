---
title: "HOW TO: diisable SATA check during  boot?"
date: 2007-09-29
forum: General Help
---

### Post by hewe on 2007-09-29
There seems to be a problem in the most recent kernel(s) 2.16.x because sata is implemented.
However there are problems reported in forums that in some (chip related) cases that the kernel determines sata and this is false. This will make the boot very lengthy and sometimes you get a time-out with a message "ata2: port is slow to respond status (0xd8 )" or an error message telling you that there was a time-out after 30 secs. Some solutions were referring to the /etc/modeprobe.conf file but unfortunately I was not able to find this conf file in Ubuntu. Is there any other way in telling the kernel that all drives are ata/ide and no sata check has to be performed?
thanks for reponses
Henk

---

