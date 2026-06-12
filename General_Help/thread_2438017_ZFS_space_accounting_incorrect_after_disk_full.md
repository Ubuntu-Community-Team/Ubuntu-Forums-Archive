---
title: "ZFS space accounting incorrect after disk full"
date: 2020-03-04
forum: General Help
---

### Post by ljlj1983 on 2020-03-04
Hi all,

I'm running Ubuntu Server 19.10 and have a ZFS storage pool in a single striped vDev (RAID0).
The ZFS file system version is showing as v5 (although the pool version does not seem to display...).

I was sending an rsync file copy to this server's ZFS volume (DISK1_BACKUP) and the volume ran out of space.
I immediately deleted some unneeded files but now ZFS commands show me as having far less than that free.

The zpool command shows me the number I expect (446GB free) but zfs list and df show much less (98.2GB) 


sudo zpool list
NAME                 SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
DISK1_BACKUP  10.9T  10.4T   446G        -         -    21%    95%  1.00x    ONLINE  -



sudo zfs list
NAME                 USED  AVAIL     REFER  MOUNTPOINT
DISK1_BACKUP  10.4T  98.2G     10.4T  /DISK1_BACKUP

df -h /DISK1_BACKUP/
Filesystem             Size  Used Avail Use% Mounted on
DISK1_BACKUP     11T   11T   99G 100% /DISK1_BACKUP



I've waited for a while and done a reboot but it didn't help.
zpool status is OK.
I am not using deduplication (nor have I ever).
I have no snapshots (nor did I delete any existing snapshots to try to resolve the issue).
My compression ratio is showing as 1.01x so it's not likely that.


"sudo zpool get freeing" shows nothing pending...

sudo zpool get freeing
NAME                PROPERTY  VALUE    SOURCE
DISK1_BACKUP  freeing          0        -


_**Curious:**_

The output above of zpool list shows an "EXPANDSZ" value of 21%.
'autoexpand' is not enabled on the zpool but I have replaced no devices either...
My other server which is identical shows 0% for "EXPANDSZ".

Help!! :)


sudo zpool status -v
  pool: DISK1_BACKUP
 state: ONLINE
status: Some supported features are not enabled on the pool. The pool can
        still be used, but some features are unavailable.
action: Enable all features using 'zpool upgrade'. Once this is done,
        the pool may no longer be accessible by software that does not support
        the features. See zpool-features(5) for details.
  scan: scrub repaired 0B in 1 days 15:30:20 with 0 errors on Mon Jan 13 15:54:22 2020
config:


        NAME                                        STATE     READ WRITE CKSUM
        DISK1_BACKUP                                ONLINE       0     0     0
          ata-WDC_WD30EFRX-68AX9N0_WD-WMC1T0994917  ONLINE       0     0     0
          ata-WDC_WD30EFRX-68AX9N0_WD-WMC1T0995030  ONLINE       0     0     0
          ata-WDC_WD30EFRX-68AX9N0_WD-WMC1T1067057  ONLINE       0     0     0
          ata-WDC_WD30EFRX-68AX9N0_WD-WMC1T1088592  ONLINE       0     0     0


errors: No known data errors

---

