---
title: "Strange crashes because of the mdadm service?"
date: 2004-11-07
forum: General Help
---

### Post by JsPr on 2004-11-07
I thought I would share something strange concerning the mdadm service in Ubuntu. I don't know for sure if it is responsible but it sure looks like it. Since installing Ubuntu I have experienced strange crashes when using TAR or DAR to backup my files. Ubuntu , and the process, crashed every time. I checked my computers memory and everything I could think of and began to feel a bit frustrated.
When I looked in /var/log I noticed that I had a lot of logs called evms-engine.log. I don't have any RAID disks on my system. There were a lot of errors in those log files.
I suspected that this could be connected to my DAR and TAR crashes. Something was wrong when my system was writing heavily to disk.
Anyway I disabled the mdadm daemon and I am now able to use DAR and TAR to take backups.
Strange, isn't it?

---

