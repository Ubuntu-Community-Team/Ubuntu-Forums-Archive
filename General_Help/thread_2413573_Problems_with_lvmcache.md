---
title: "Problems with lvmcache"
date: 2019-02-27
forum: General Help
---

### Post by InThane on 2019-02-27
I'm trying to set up a system using LVMcache. The system has three hard drives, 2x 3TB and one 240gb SSD. The only "fancy" partitioning I've done is on the SSD, which has 3 partitions:
```
Device       Size Type
/dev/sdc1     37M EFI System
/dev/sdc2   37.3G Linux filesystem
/dev/sdc3  201.2G Linux LVM
```
The two platter drives have a single partition each, set up as a Linux LVM partition.

I installed Ubuntu 18.10 on sdc2, then made a VG called vg-datapool out of sda1 and sdb1. I assigned all sectors to a LV called lv-datapool. I verified I could mount it and write to it. Added it to fstab, then rebooted, and it was still there.

I then added sdc3 to the VG, and made two LVs: lv-cache-meta (300mb) and lv-cache (the remaining, minus 100 extants that according to the directions I was following the cache drive needs to keep unassigned) and ran the following:
lvconvert --type cache-pool --cachemode writethrough --poolmetadata vg-datapool/lv-cache-meta vg-datapool/lv-cache
lvconvert --type cache --cachepool vg-datacloud/lv-cache vg-datacloud/lv-nextcloud

I then tested the system, and data appeared to be showing up there. I rebooted it, and the system hung on startup. Hit the escape key and I saw the following:
```
/dev/sdc2: clean, 176606/2444624 files, 1923730/9765625 blocks
[FAILED] Failed to start LVM2 PV scan on device 8:17.
See 'systemctl status lvm2-pvscan@8.17.service' for details.
[FAILED] Failed to start LVM2 PV scan on device 8:35.
See 'systemctl status lvm2-pvscan@8.35.service' for details.
[FAILED] Failed to start LVM2 PV scan on device 8:1.
See 'systemctl status lvm2-pvscan@8.1.service' for details.
```

It bounced me into repair mode. I commented out the pool entry in mount, restarted the computer, and it came up fine. Results of systemctl status below:
```
 systemctl status lvm2-pvscan@8:17.service
&#9679; lvm2-pvscan@8:17.service - LVM2 PV scan on device 8:17
   Loaded: loaded (/lib/systemd/system/lvm2-pvscan@.service; static; vendor preset: enabled)
   Active: failed (Result: exit-code) since Wed 2019-02-27 04:44:32 PST; 19min ago
     Docs: man:pvscan(8)
 Main PID: 2626 (code=exited, status=5)

Feb 27 04:44:32 server01 systemd[1]: Starting LVM2 PV scan on device 8:17...
Feb 27 04:44:32 server01 lvm[2626]:   /usr/sbin/cache_check: execvp failed: No such file or directory
Feb 27 04:44:32 server01 lvm[2626]:   Check of pool vg-datapool/lv-cache failed (status:2). Manual repair required!
Feb 27 04:44:32 server01 lvm[2626]:   0 logical volume(s) in volume group "vg-datapool" now active
Feb 27 04:44:32 server01 lvm[2626]:   vg-datapool: autoactivation failed.
Feb 27 04:44:32 server01 systemd[1]: lvm2-pvscan@8:17.service: Main process exited, code=exited, status=5/NOTINSTALLED
Feb 27 04:44:32 server01 systemd[1]: lvm2-pvscan@8:17.service: Failed with result 'exit-code'.
Feb 27 04:44:32 server01 systemd[1]: Failed to start LVM2 PV scan on device 8:17.
```
```
systemctl status lvm2-pvscan@8:35.service
&#9679; lvm2-pvscan@8:35.service - LVM2 PV scan on device 8:35
   Loaded: loaded (/lib/systemd/system/lvm2-pvscan@.service; static; vendor preset: enabled)
   Active: failed (Result: exit-code) since Wed 2019-02-27 04:39:07 PST; 29min ago
     Docs: man:pvscan(8)
 Main PID: 524 (code=exited, status=5)

Feb 27 04:39:06 server01 systemd[1]: Starting LVM2 PV scan on device 8:35...
Feb 27 04:39:07 server01 lvm[524]:   /usr/sbin/cache_check: execvp failed: No such file or directory
Feb 27 04:39:07 server01 lvm[524]:   Check of pool vg-datapool/lv-cache failed (status:2). Manual repair required!
Feb 27 04:39:07 server01 lvm[524]:   0 logical volume(s) in volume group "vg-datapool" now active
Feb 27 04:39:07 server01 lvm[524]:   vg-datapool: autoactivation failed.
Feb 27 04:39:07 server01 systemd[1]: lvm2-pvscan@8:35.service: Main process exited, code=exited, status=5/NOTINSTALLED
Feb 27 04:39:07 server01 systemd[1]: lvm2-pvscan@8:35.service: Failed with result 'exit-code'.
Feb 27 04:39:07 server01 systemd[1]: Failed to start LVM2 PV scan on device 8:35.
```
```
systemctl status lvm2-pvscan@8:1.service
&#9679; lvm2-pvscan@8:1.service - LVM2 PV scan on device 8:1
   Loaded: loaded (/lib/systemd/system/lvm2-pvscan@.service; static; vendor preset: enabled)
   Active: failed (Result: exit-code) since Wed 2019-02-27 04:39:07 PST; 30min ago
     Docs: man:pvscan(8)
 Main PID: 527 (code=exited, status=5)

Feb 27 04:39:06 server01 systemd[1]: Starting LVM2 PV scan on device 8:1...
Feb 27 04:39:07 server01 lvm[527]:   /usr/sbin/cache_check: execvp failed: No such file or directory
Feb 27 04:39:07 server01 lvm[527]:   Check of pool vg-datapool/lv-cache failed (status:2). Manual repair required!
Feb 27 04:39:07 server01 lvm[527]:   0 logical volume(s) in volume group "vg-datapool" now active
Feb 27 04:39:07 server01 lvm[527]:   vg-datapool: autoactivation failed.
Feb 27 04:39:07 server01 systemd[1]: lvm2-pvscan@8:1.service: Main process exited, code=exited, status=5/NOTINSTALLED
Feb 27 04:39:07 server01 systemd[1]: lvm2-pvscan@8:1.service: Failed with result 'exit-code'.
Feb 27 04:39:07 server01 systemd[1]: Failed to start LVM2 PV scan on device 8:1.
```
This is just the latest attempt I've made to make a cached LV - I've followed several different recipes, all of which come to the same end result. The system runs fine until reboot, at which point it just hangs. The first time I did it, I was able to remove the cache LV from the main LV without a hitch and the system continued running (albeit slowly) but every time after that the LV appears to be corrupted and need manual repair. The SSD itself seems to be working fine according to the manufacturer's diagnostic tools.

Any thoughts or tips?

---

