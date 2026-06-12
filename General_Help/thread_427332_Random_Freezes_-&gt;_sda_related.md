---
title: "Random Freezes -&gt; sda related?"
date: 2007-04-29
forum: General Help
---

### Post by dafrabbit on 2007-04-29
Hi all,

I've been experiencing random freezes ever since installing a fresh feisty, never used to happen with edgy, dapper, etc. Does not happen now on WinXP either. I do believe I have found the source of my problems in dmesg log. The following log entries seem to be consistent with the two freezes I've had since booting up this morning:

Freeze #1:
```

[  738.728000] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  738.728000] ata1.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x0 data 0 
[  738.728000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  745.736000] ata1: port is slow to respond, please be patient (Status 0xd0)
[  768.760000] ata1: port failed to respond (30 secs, Status 0xd0)
[  768.760000] ata1: soft resetting port
[  769.160000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  769.168000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  769.168000] ata1.00: configured for UDMA/100
[  769.348000] ata1.01: configured for UDMA/33
[  769.348000] ata1: EH complete
[  769.364000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[  769.372000] sda: Write Protect is off
[  769.372000] sda: Mode Sense: 00 3a 00 00
[  769.600000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  769.616000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[  769.616000] sda: Write Protect is off
[  769.616000] sda: Mode Sense: 00 3a 00 00
[  769.616000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```

Second freeze:
```

[  858.780000] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  858.780000] ata1.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x0 data 0 
[  858.780000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  865.788000] ata1: port is slow to respond, please be patient (Status 0xd0)
[  888.804000] ata1: port failed to respond (30 secs, Status 0xd0)
[  888.804000] ata1: soft resetting port
[  889.208000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  889.220000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  889.220000] ata1.00: configured for UDMA/100
[  889.400000] ata1.01: configured for UDMA/33
[  889.400000] ata1: EH complete
[  889.416000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[  889.424000] sda: Write Protect is off
[  889.424000] sda: Mode Sense: 00 3a 00 00
[  889.424000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  889.428000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[  889.428000] sda: Write Protect is off
[  889.428000] sda: Mode Sense: 00 3a 00 00
[  889.428000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```

Any ideas? Could this be a result of changing over to using sda/sdb/sdc/etc. for hard drives instead of hda/hdb/hdc/etc.?

---

### Post by dafrabbit on 2007-04-29
Another freeze, happened just now:

```

[ 2073.772000] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 2073.772000] ata1.01: cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x43 data 12 in
[ 2073.772000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[ 2080.780000] ata1: port is slow to respond, please be patient (Status 0xd0)
[ 2103.816000] ata1: port failed to respond (30 secs, Status 0xd0)
[ 2103.816000] ata1: soft resetting port
[ 2104.228000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[ 2104.236000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[ 2104.236000] ata1.00: configured for UDMA/100
[ 2104.416000] ata1.01: configured for UDMA/33
[ 2104.416000] ata1: EH complete
[ 2104.432000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[ 2104.448000] sda: Write Protect is off
[ 2104.448000] sda: Mode Sense: 00 3a 00 00
[ 2104.472000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 2104.496000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[ 2104.504000] sda: Write Protect is off
[ 2104.504000] sda: Mode Sense: 00 3a 00 00
[ 2104.504000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```

Strangely I had partial control of my computer at this time....

---

### Post by kiev on 2008-05-24
This kernel bug
 this problem already whole year

for me she showed up one time in the floor of hour, however as a result of this problem I lost a mysql database - mysql innodb not start - "Accertion error" - did not help even "innodb_force_recovery = 4", backup was an a week remoteness - the works of whole department lost data for a few days, the management simply in shock - I going to discharge from job (((

this problem already whole year:
-----------
I'm stumped trying to track down the below intermittent problem.....
I've confirmed this problem on 2.6.19, 2.6.20 and 2.6.21.
[http://lkml.org/lkml/2007/6/14/154](http://lkml.org/lkml/2007/6/14/154)
[http://kerneltrap.org/mailarchive/linux-kernel/2007/6/14/103765](http://kerneltrap.org/mailarchive/linux-kernel/2007/6/14/103765)
[http://kerneltrap.org/node/16175](http://kerneltrap.org/node/16175)
[http://lkml.org/lkml/2007/6/14/154](http://lkml.org/lkml/2007/6/14/154)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/217920](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/217920)
[https://bugs.launchpad.net/ubuntu/+bug/164183](https://bugs.launchpad.net/ubuntu/+bug/164183)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229747](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229747)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/159521](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/159521)
[https://bugs.launchpad.net/ubuntu/+bug/164183](https://bugs.launchpad.net/ubuntu/+bug/164183)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/187146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/187146)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/221437](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/221437)
[https://bugs.launchpad.net/ubuntu/+bug/226600](https://bugs.launchpad.net/ubuntu/+bug/226600)

SUSE:

ata errors, system freeze
[https://bugzilla.novell.com/show_bug.cgi?id=393675](https://bugzilla.novell.com/show_bug.cgi?id=393675)

System lockup with concurrent acces to SATA disks on Promise PDC20378
[http://lists.opensuse.org/opensuse-bugs/2008-02/msg03458.html](http://lists.opensuse.org/opensuse-bugs/2008-02/msg03458.html)

Kernel panic / system hang / sata_promise
[https://bugzilla.novell.com/show_bug.cgi?id=350907](https://bugzilla.novell.com/show_bug.cgi?id=350907)

DELL Poweredge 2970 hangs sometimes (ata1)
[https://bugzilla.novell.com/show_bug.cgi?id=359333](https://bugzilla.novell.com/show_bug.cgi?id=359333)

Fedora:
ata device crashing system in Fedora 8
[http://www.experts-exchange.com/OS/Linux/Distributions/Fedora/Q_23125450.html](http://www.experts-exchange.com/OS/Linux/Distributions/Fedora/Q_23125450.html)

problème de mise à jour
[http://forums.fedora-fr.org/viewtopic.php?pid=253930](http://forums.fedora-fr.org/viewtopic.php?pid=253930)

Kernel 2.6.24.x boot problem - Anyone , Any idea
[http://fcp.surfsite.org/modules/newbb/viewtopic.php?viewmode=flat&order=ASC&topic_id=54760&forum=10](http://fcp.surfsite.org/modules/newbb/viewtopic.php?viewmode=flat&order=ASC&topic_id=54760&forum=10)

Thought though with the newest hard drive with support of NCQ such is not present, ... also same:

"With this kernel I’m getting frequent temporary freezes (system comes back responsive after a minute or so…)."
[http://kerneltrap.org/mailarchive/linux-kernel/2008/1/8/546296](http://kerneltrap.org/mailarchive/linux-kernel/2008/1/8/546296)

---

