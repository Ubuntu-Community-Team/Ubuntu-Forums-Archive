---
title: "raid1 array not spinning down"
date: 2016-06-23
forum: General Help
---

### Post by gametaunt on 2016-06-23
i've recently put together a new HTPC/nas system. however i cant seem to get the 2 HGST 6TB Nas drives to spin down. They are not being used as a os drive, i've got a separate drive for that

hdparm.conf is configured as such
```

/dev/disk/by-id/ata-HGST_HDN726060ALE614_NCGPL8MS {
        apm = 127
        keep_features_over_reset = on
        spindown_time = 120
}

/dev/disk/by-id/ata-HGST_HDN726060ALE614_NCGPMRVS {
        apm = 127
        keep_features_over_reset = on
        spindown_time = 120
}

```

/etc/default/smartmontools is set to:
```

smartd_opts="-q never -i 7200"

```

/etc/smartd.conf is set to
```

DEVICESCAN -S on -o on -a -I 194 -m root -s (S/../.././02|L/../../6/03) -n standby,q

```

when i manually set the apm settings they still wont spin down automatically.
```

hdparm -B1 /dev/sd[bc]
hdparm -S1 /dev/sd[bc]

```

i've ran inotifywatch on my mount point there dont seem to be happening any io events whatsoever.

i've also tried disablying as many services as possible that might keep drives alive like: webmin, samba, nfs, cron.

also checked that the raid array is fully initialized.
```

# mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Sat Jun 18 19:35:09 2016
     Raid Level : raid1
     Array Size : 5860391488 (5588.90 GiB 6001.04 GB)
  Used Dev Size : 5860391488 (5588.90 GiB 6001.04 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

  Intent Bitmap : Internal

    Update Time : Thu Jun 23 19:05:37 2016
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           Name : bjorn-media:0  (local to host bjorn-media)
           UUID : 88d23551:c08a3d48:f384903a:17e74cff
         Events : 8101

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc

```

seems there is still something ocasionally doing something (like once each 4-5 secs) with the drives that makes them tick that also prevents spin-down.

also when putting drives in standby with:
```

hdparm -y /dev/sd[bc]

```

they enter standby state and stay like that, untill accessed.

Does anyone have any clue why the automatic spindown isn't working?

---

