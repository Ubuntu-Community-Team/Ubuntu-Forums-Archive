---
title: "Lost home directory"
date: 2007-11-29
forum: General Help
---

### Post by sankoz on 2007-11-29
Hi,

Something strange happened in my PC last night. My roommate was browsing internet (some harmless sites like bbc sport), when the system hanged all of a sudden. He powercycled the machine, after waiting for five minutes. After the system restarted, he was not able to log in to the machine; it kept complaining that the directory /home/username does not exist! 

We went to recovery mode, and found that /home indeed does not contain the user's home directory. Timestamp of /home shows that it was updated just before the crash. Only Firefox 2.10 was running during that time. /home is on a separate partition (ext3) and that is getting mounted perfectly in recovery mode. df  output shows that only 1% is used, so apparently the user's home directory has been deleted somehow.

Any idea what could have gone wrong? System details are as follows:

 - OS : Gutsy (latest updates up to 29-Nov installed).
-  samba was running with the said home directory shared. But no one was accessing it at the moment, AFAIK, since this is behind a password protected ADSL router. Moreover, the share itself is password protected.

Could this be some vulnerability in samba or firefox? Any idea on how to recover the home directory (ext3 partition) ? Thanks for your time and thoughts.

Regards,
Sanjeev

---

### Post by Sef on 2007-11-30
Get [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").

---

