---
title: "Errors trying to access Intel raid 10"
date: 2008-04-29
forum: General Help
---

### Post by Teefs on 2008-04-29
I have a raid 10 which has windows on it and I would like to be able to access those files from ubuntu. I am trying to use dmraid, but when I enter the command "sudo dmraid -ay" it gives me the following:

ERROR: isw: Error finding disk table slot for /dev/sdb
ERROR: isw device for volume "Volume0" broken on /dev/sda in RAID set "isw_eihhbgcae_Volume0"
ERROR: isw: wrong # of devices in RAID set "isw_eihhbgcae_Volume0" [3/4] on /dev/sda
ERROR: isw device for volume "Volume0" broken on /dev/sdc in RAID set "isw_eihhbgcae_Volume0"
ERROR: isw: wrong # of devices in RAID set "isw_eihhbgcae_Volume0" [3/4] on /dev/sdc
ERROR: isw device for volume "Volume0" broken on /dev/sdd in RAID set "isw_eihhbgcae_Volume0"
ERROR: isw: wrong # of devices in RAID set "isw_eihhbgcae_Volume0" [3/4] on /dev/sdd
ERROR: no mapping possible for RAID set isw_eihhbgcae_Volume0


Any Ideas what might be wrong or how to fix this?

---

### Post by DrRobotnik on 2008-09-26
Im having the same problem...

---

### Post by fjgaude on 2008-09-26
Does the man pages for **dmraid** say it hanldes raid10? I don't have dmraid installed and don't wish to, so I can't read any of its man pages.

---

