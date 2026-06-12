---
title: "Monitoring HDD power state with SNMP"
date: 2015-12-28
forum: General Help
---

### Post by genka on 2015-12-28
Hello,
I'm using Observium NMS to monitor my devices. One of the aspects I'm interested in is to see how much time my hard drives spend in the active/idle vs. sleep states. I can view the current state from the console with the smartctl command, but would like to access this information over SNMP, so Observium could graph it.

Thanks.

---

### Post by Habitual on 2015-12-28
[Linux SNMP OID’s for CPU,Memory and Disk Statistics]("http://www.debianadmin.com/linux-snmp-oids-for-cpumemory-and-disk-statistics.html")

---

### Post by genka on 2015-12-28
Yes, all this data is pulled and graphed by Observium. But the HDD power state is not there. I know that this OID doesn't exist, and asking if it is possible to create a custom one.

---

### Post by Habitual on 2015-12-28
I don't know.
What smartctl calls "active/idle" or "sleep" may be present in another OID.
Have you "walked the tree" to see what OIDs may be of interest?

---

### Post by genka on 2015-12-28
Observium walks SNMP during the discovery process and maps all available OIDs. Enterprise level servers might have proprietary extensions, but I'm talking about generic hardware. 
I stumbled upon an article describing SNMP based external temperature monitoring with RaspberryPI [http://djsattempt.blogspot.com/2013/03/raspberry-pi-and-snmp-polling-using.html](http://djsattempt.blogspot.com/2013/03/raspberry-pi-and-snmp-polling-using.html) and hoped that something similar existed for HDD power.

---

