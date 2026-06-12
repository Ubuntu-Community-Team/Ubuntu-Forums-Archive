---
title: "ZFSonLinux Zpool Replace Help"
date: 2013-01-25
forum: General Help
---

### Post by DeadLemon on 2013-01-25
Hey all

First of all I'm running ubuntu server 12.04

So one of my drive in my RaidZ array started giving huge bad sector errors, so today I got it swapped out

But now I cat seem to replace it, the procedure does not seem complex, but it keeps saying the drives don't exist in the pool

```
  pool: tank
 state: DEGRADED
status: One or more devices has experienced an error resulting in data
        corruption.  Applications may be affected.
action: Restore the file in question if possible.  Otherwise restore the
        entire pool from backup.
   see: http://zfsonlinux.org/msg/ZFS-8000-8A
 scan: resilvered 62,2M in 0h15m with 0 errors on Mon Jan  7 00:27:24 2013
config:

        NAME                                          STATE     READ WRITE CKSUM
        tank                                          DEGRADED     0     0     0
          raidz1-0                                    DEGRADED     0     0     0
            ata-WDC_WD20EARX-00PASB0_WD-WCAZA9725516  ONLINE       0     0     0
            ata-WDC_WD20EARX-00PASB0_WD-WCAZA9745385  UNAVAIL      0     0     0
            ata-WDC_WD20EARX-00PASB0_WD-WCAZA9718650  ONLINE       0     0     0
            ata-WDC_WD20EARX-00PASB0_WD-WCAZA9748645  ONLINE       0     0     0

```so what I have read is that you need to either run the zpool offline or zpool replace commands, both return the same errors, I don't know what I'm doing wrong
I assume that the drives listed at by-id

```
 #ls  /dev/disk/by-id
ata-ST2000DM001-1CH164_Z1E2T4HH           ata-WDC_WD20EARX-00PASB0_WD-WCAZA9725516  scsi-SATA_VB0250EAVER_9VMTH23R-part5       wwn-0x5000c5004f848b1b
ata-ST2000DM001-1CH164_Z1E2T4HH-part1     ata-WDC_WD20EARX-00PASB0_WD-WCAZA9748645  scsi-SATA_WDC_WD20EARX-00_WD-WCAZA9718650  wwn-0x5000c5004f848b1b-part1
ata-ST2000DM001-1CH164_Z1E2T4HH-part9     scsi-SATA_ST2000DM001-1CH_Z1E2T4HH        scsi-SATA_WDC_WD20EARX-00_WD-WCAZA9725516  wwn-0x5000c5004f848b1b-part9
ata-VB0250EAVER_9VMTH23R                  scsi-SATA_ST2000DM001-1CH_Z1E2T4HH-part1  scsi-SATA_WDC_WD20EARX-00_WD-WCAZA9748645  wwn-0x50014ee25b9114f7
ata-VB0250EAVER_9VMTH23R-part1            scsi-SATA_ST2000DM001-1CH_Z1E2T4HH-part9  wwn-0x5000c5002d3087b9                     wwn-0x50014ee2b0e6bf00
ata-VB0250EAVER_9VMTH23R-part2            scsi-SATA_VB0250EAVER_9VMTH23R            wwn-0x5000c5002d3087b9-part1               wwn-0x50014ee2b0e6c39a
ata-VB0250EAVER_9VMTH23R-part5            scsi-SATA_VB0250EAVER_9VMTH23R-part1      wwn-0x5000c5002d3087b9-part2
ata-WDC_WD20EARX-00PASB0_WD-WCAZA9718650  scsi-SATA_VB0250EAVER_9VMTH23R-part2      wwn-0x5000c5002d3087b9-part5

```[ata-ST2000DM001-1CH164_Z1E2T4HH is the new drive, the WD20EARX's are the remaining 3 drives and the VB250 is the main OS drive]

So I've tried (sdb being the new drive)

```
#zpool replace  tank /dev/disk/by-id/ata-WDC_WD20EARX-00PASB0_WD-WCAZA9745385 /dev/sdb
cannot replace /dev/disk/by-id/ata-WDC_WD20EARX-00PASB0_WD-WCAZA9745385 with /dev/sdb: no such device in pool
```or using both By-id

```
# zpool replace  tank /dev/disk/by-id/ata-WDC_WD20EARX-00PASB0_WD-WCAZA9745385 /dev/disk/by-id/ata-ST2000DM001-1CH164_Z1E2T4HH
cannot replace /dev/disk/by-id/ata-WDC_WD20EARX-00PASB0_WD-WCAZA9745385 with /dev/disk/by-id/ata-ST2000DM001-1CH164_Z1E2T4HH: no such device in pool
```any ideas? because I'm stumped

Ok, well I found a quick solution, I've gone and loaded up a live USB of Nas4Free, and that is now rebuilding my array
I would still like to find a fix, because I will probably run into the same issue down the line

---

