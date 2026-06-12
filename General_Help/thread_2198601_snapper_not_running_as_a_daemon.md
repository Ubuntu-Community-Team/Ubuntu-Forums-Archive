---
title: "snapper not running as a daemon"
date: 2014-01-09
forum: General Help
---

### Post by roberto32 on 2014-01-09
I've only one snapshot, I've installed sanpper 2 weeks ago and I looked in the /etc/snapper/configs/root and there is 
 ```

# subvolume to snapshot
SUBVOLUME="/root"

# filesystem type
FSTYPE="btrfs"

# start comparing pre- and post-snapshot in background after creating
# post-snapshot
BACKGROUND_COMPARISON="yes"


# run daily number cleanup
NUMBER_CLEANUP="yes"

# limit for number cleanup
NUMBER_MIN_AGE="1800"
NUMBER_LIMIT="100"


# create hourly snapshots
TIMELINE_CREATE="yes"

# cleanup hourly snapshots after some time
TIMELINE_CLEANUP="yes"

# limits for timeline cleanup
TIMELINE_MIN_AGE="1800"
TIMELINE_LIMIT_HOURLY="10"
TIMELINE_LIMIT_DAILY="10"
TIMELINE_LIMIT_MONTHLY="10"
TIMELINE_LIMIT_YEARLY="10"


# cleanup empty pre-post-pairs
EMPTY_PRE_POST_CLEANUP="yes"

# limits for empty pre-post-pair cleanup
EMPTY_PRE_POST_MIN_AGE="1800"


```
but I have only one snapshot ```
 snapper list
```
```
 
Type   | # | Pre # | Date | Cleanup | Description | Userdata
-------+---+-------+------+---------+-------------+---------
single | 0 |       |       |           | current   |         

```

---

### Post by roberto32 on 2014-01-09
here's some output form /var/log/snapper 
```
2014-01-09 21:46:00 MIL libsnapper(16983) SystemCmd.cc(execute):90 - SystemCmdxecuting:"/sbin/btrfs subvolume snapshot '/root' '/root/.snapshots/1/snapshot'
2014-01-09 21:46:00 MIL libsnapper(16983) SystemCmd.cc(addLine):568 - Adding Le 1 "ERROR: '/root' is not a subvolume"
2014-01-09 21:46:00 MIL libsnapper(16983) SystemCmd.cc(getUntilEOF):532 - pid:984 added lines:1 stderr:true
2014-01-09 21:46:00 MIL libsnapper(16983) SystemCmd.cc(doExecute):275 - stopwah 0.004819s for "/sbin/btrfs subvolume snapshot '/root' '/root/.snapshots/1/snshot'"
2014-01-09 21:46:00 MIL libsnapper(16983) SystemCmd.cc(doExecute):295 - system Returns:13
2014-01-09 21:46:00 MIL libsnapper(16983) SystemCmd.cc(logOutput):587 - stderrRROR: '/root' is not a subvolume
2014-01-09 21:46:00 ERR libsnapper(16983) snapper.cc(main):1257 - caught finalxception
2014-01-09 21:46:00 MIL libsnapper(16983) Snapper.cc(~Snapper):85 - Snapper deructor


```

---

### Post by oldos2er on 2014-01-09
Moved to General Help.

---

