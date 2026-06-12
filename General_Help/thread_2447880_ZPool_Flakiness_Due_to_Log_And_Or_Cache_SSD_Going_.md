---
title: "ZPool Flakiness Due to Log And Or Cache SSD Going Bad"
date: 2020-07-27
forum: General Help
---

### Post by pmagid on 2020-07-27
Architecture:
1.  Home NAS setup so corners are cut in ways that would not be if truly prod enterprise environment.
2. zpool consisting of 8 x 8TB drives in RAIDZ2 (upgraded from original 8x4TB)
3. 2 SSD with multiple partitions for:  1) Boot (Ubuntu 20.04 btrfs mirror) [when NAS was created booting to zfs was not a widely supported thing in Ubuntu, so even though I hate btrfs that is what we have] 2) OS swap 3) zfs cache 4) zfs log 
4. Motherboard 8 core Asrock C2750D4I, 32GB ECC memory

Symptoms Observed and Tests Conducted:
1.  Over the last couple of months during scrub (and only during scrub) miscellaneous read and write errors would pop up some times to the point where the drive would be faulted.   It was always the same two drives at the bottom of the list of drives in zpool status.
2. A check of the drives smart data would never show an issue.  The drives where old but there were no Offline_uncorrectable or Pending_Sectors or other items indicating an issue with the drive.
3. Smartctl long tests on the drive with errors completed with no issues.
4. Swapping the drives to different NAS bays made no impact.
5. Swapping drives with known good drives made no change.
6. Swapping NAS power supply for a newer beefier 80plus one with higher capacity made no change.
7. Changed sata cables…. No impact.
8. Moved affected drive to an external sata controller card. No change.

Resolution?
While doing the eighth and last test mentioned above (I could not think of any more tests to perform honestly) the NAS failed to reboot.   One of the two SSD drives was as dead as a doornail….   In retrospect it appears it was failing for a while.   I replaced the SSD drive by adding a new one to the boot btrfs mirror.   Recreated the pools log and cache using the existing SSD and the new SSD and the issue seems to have gone away…. Ran a scrub and there are no errors.   Does this make sense?   Can a failing log or cache drive manifest (falsely / misleadingly) as read or write issues with data drives in a pool?

---

### Post by pmagid on 2020-07-29
Uh yeah...  This is an example of posting before you have ALL the facts.    Actually the random read and write issues appear to be only when attached to the Marvell 9230 chip driven ports on the board and has nothing to do with the dying SSD drive....   Anyone know anything about that chip?

---

