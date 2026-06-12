---
title: "SNMP stopped hrStorageDescr for Disks"
date: 2019-09-05
forum: General Help
---

### Post by mjjazz on 2019-09-05
This morning, so far, three of my Ubuntu 18.04 LTS boxes have stopped advertising the root partition through SNMP hrStorageDescr.  The only items using this index are memory and swap items.  Prior to this morning (7:30 AM CDT for the first affected box) this SNMP query would find the root partition.  Was there a security update released this morning or last night that could be causing this?

Using the UCD OIDs, which index on the physical device paths, i.e. /dev/sda4, the SNMP queries will work, but I have one monitoring system that will only use the other which I believe, if I am reading the Cacti php script correctly, are under OID .1.3.6.1.2.1.25.2.3.  Cacti clued me in as it threw a "bad index" error.  Then my network monitoring alarms went off that the disk was not reachable.

What has changed?  Where do I need to look to find out what could have possibly changed?  The snmpd.conf definitely was not changed at this time.  The disk is mounted.  SNMPD is answering rocommunity gets.

Thank you!

---

### Post by The Cog on 2019-09-05
Odd. Did the snmp daemon restart? [http://www.oid-info.com/get/1.3.6.1.2.1.1.3](http://www.oid-info.com/get/1.3.6.1.2.1.1.3)

---

### Post by mjjazz on 2019-09-05
No, but I have restarted it since, multiple times with no change in this new behavior.

---

### Post by The Cog on 2019-09-05
I just found this: [https://bugs.launchpad.net/ubuntu/+source/net-snmp/+bug/1842924](https://bugs.launchpad.net/ubuntu/+source/net-snmp/+bug/1842924)

---

### Post by mjjazz on 2019-09-05
TY!  That confirms my suspicions.  I guess I'll work to backrev the affected boxes, and wait for the patch.

---

