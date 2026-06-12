---
title: "How do one use Amanda with Ubuntu to backup to a hard drive?"
date: 2007-03-25
forum: General Help
---

### Post by motin on 2007-03-25
I'd really love to start using Amanda to backup my Ubuntu system. It really caught my interest when I saw their 15-minute guide to getting up and running with Amanda using virtual tapes, that is pure hard drives as backup destination - [http://www.zmanda.com/quick-backup-setup.html](http://www.zmanda.com/quick-backup-setup.html). (Earlier I looked past Amanda as a backup software option because I thought it only supported tape drives, of which I do not have...)

Problems quickly arose though:

1. The guide is written for RPM-based installation, where xinetd is used instead of inetd and the user/group used by amanda is amandabackup/disk instead of backup/backup as on a Ubuntu installation - Which means following the guide literally doesn't work and a lot of guessing and testing about how the corresponding Ubuntu-setup has been laid out have had to be done. Also, I had to skip the parts about ~amandabackup/.amandahosts and ~amandabackup/.am_passphrase because I cannot find the corresponding files in my Ubuntu system (after installing amanda-common, amanda-server and amanda-client from the repos)...

2. The guide is written for Amanda 2.5.1p2, while the latest version for Ubuntu Dapper is 2.4.5p1 - This means that: a. the parts about encryption were met by inability to parse the configuration file and b. The commands used to label the virtual tapes led to these errors:
```
labeling tape in slot /usr/lib/amanda/chg-disk: (line 84: /usr/adm/amanda/changer-status-access: No such file or directory):
rewinding
amlabel: tape_rewind: tape open: line 84: /usr/adm/amanda/changer-status-access: No such file or directory: No such file or directory
labeling tape in slot /usr/lib/amanda/chg-disk: (line 84: /usr/adm/amanda/changer-status-access: No such file or directory):
rewinding
```

So after trying to following the quickstart-guide, I am left with more questions than answers on how to use Amanda with Ubuntu. 

If someone could share their experiences with backing up to a physical hard drive path using Amanda on Ubuntu (preferable Dapper), many including myself would be very grateful!

---

### Post by cjsmith on 2007-04-17
I've posted a full HOWTO on this very subject at [http://ubuntuforums.org/showthread.php?p=2470030](http://ubuntuforums.org/showthread.php?p=2470030)

---

