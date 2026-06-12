---
title: "SNMP OID for disk transfer rate"
date: 2018-04-06
forum: General Help
---

### Post by Hans_van_Leeuwen on 2018-04-06
SNMP on a Ubuntu system contains several OID's with disk information, like:
Path where the disk is mounted:         .1.3.6.1.4.1.2021.9.1.2.1
Path of the device for the partition:      .1.3.6.1.4.1.2021.9.1.3.1
Total size of the disk/partion (kBytes): .1.3.6.1.4.1.2021.9.1.6.1
Available space on the disk:               .1.3.6.1.4.1.2021.9.1.7.1
Used space on the disk:                     .1.3.6.1.4.1.2021.9.1.8.1
Percentage of space used on disk:      .1.3.6.1.4.1.2021.9.1.9.1
Percentage of inodes used on disk:      .1.3.6.1.4.1.2021.9.1.10.1

But I want to know how busy the disk is.
So is it also possible to get the disk transfer rate by SNMP?

---

