---
title: "Large RAID array wont automount on boot"
date: 2016-01-11
forum: General Help
---

### Post by XBNCPRk on 2016-01-11
I recently upgraded from an 8-drive RAID5 array of 2tb drives to an 8-drive RAID6 array of 4tb drives. This wasnt without its own pains (concerning the 64 bit flag not being used by default, and ext4's lazy_itable_init taking a small ice age to run without ever finishing), but the array is up, populated with data and runs fine. My problem though is that no matter what I try it will not automount from fstab. 

[LIST]
[*]After booting, the array does mount fine from the terminal by either explictly calling the array and mount point, or by just using mount -a.
[*]I have tried using both the UUID (from blkid and from mdadm --detail --scan) and using /dev/md0 in my fstab file. Both the mdadm given UUID and /dev/md0 result in hanging at boot saying its unavailable, the one from blkid gives an error while running update-initramfs -u after changing the fstab file.
[*]I have erased the metadata= and name= portions of the /etc/mdadm/mdadm.conf file, no joy from that.
[/LIST]

The /etc/mdadm/mdadm.conf file contents are: 
```
ARRAY /dev/md0 UUID=7db0c723:c7f62b03:8ed2ef78:ccb7fa47
```

The pertinent fstab line is:
```
/dev/md0     /path/to/mountpoint     ext4     defaults 0 2
```

And from the dmesg log (and given that it otherwise mounts and operates fine), it appears as though theres nothing wrong with the array itself.
```
[    2.394920] md: bind<sdh>[    2.397523] md: bind<sdf>
[    2.401120] md: bind<sdg>
[    2.427905] md: bind<sdc>
[    2.432152] md: bind<sdd>
[    2.437634] md: bind<sdb>
[    2.442720] md: bind<sda>
[    2.447225] md/raid:md0: device sda operational as raid disk 3
[    2.447229] md/raid:md0: device sdb operational as raid disk 4
[    2.447231] md/raid:md0: device sdd operational as raid disk 6
[    2.447233] md/raid:md0: device sdc operational as raid disk 5
[    2.447234] md/raid:md0: device sdg operational as raid disk 1
[    2.447235] md/raid:md0: device sdf operational as raid disk 0
[    2.447237] md/raid:md0: device sdh operational as raid disk 2
[    2.447238] md/raid:md0: device sdi operational as raid disk 7
[    2.447887] md/raid:md0: allocated 0kB
[    2.448070] md/raid:md0: raid level 6 active with 8 out of 8 devices, algorithm 2
[    2.448071] RAID conf printout:
[    2.448072]  --- level:6 rd:8 wd:8
[    2.448073]  disk 0, o:1, dev:sdf
[    2.448074]  disk 1, o:1, dev:sdg
[    2.448076]  disk 2, o:1, dev:sdh
[    2.448077]  disk 3, o:1, dev:sda
[    2.448078]  disk 4, o:1, dev:sdb
[    2.448079]  disk 5, o:1, dev:sdc
[    2.448080]  disk 6, o:1, dev:sdd
[    2.448081]  disk 7, o:1, dev:sdi
[    2.448300] created bitmap (30 pages) for device md0
[    2.449066] md0: bitmap initialized from disk: read 2 pages, set 0 of 59615 bits
[    2.532462] md0: detected capacity change from 0 to 24003914760192

```

Anyone have any ideas why this will not automount along with everything else on boot?

---

### Post by XBNCPRk on 2016-01-13
*bump* 

Additionally, gdisk says each member drive of the array shows that it has a problem with the gpt. It suggests restoring it from the backup, so I dropped a disk from the array, let it fix the gpt error, verified it no longer showed an error, then re-added it to the raid array. 23 hours of sync-ing later, the drive shows the same gpt error in gdisk. All the drives show this, all function fine, and there is no data corruption across any of the ~65% used. 

Is this something I should be concerned about? And if so, what causes this and would an error like this prevent the array from starting on boot?

The actual error messages:

Caution! After loading partitions, the CRC doesn't check out!
Warning! Main partition table CRC mismatch! Loaded backup partition table
instead of main partition table!

Warning! One or more CRCs don't match. You should repair the disk!

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: damaged

****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************

---

### Post by XBNCPRk on 2016-01-16
...Anyone have any thoughts? I will also entertain any wildly speculative, off the wall, or just plain funny suggestions as well...

---

### Post by XBNCPRk on 2016-01-28
*one final, hopeful bump*

---

