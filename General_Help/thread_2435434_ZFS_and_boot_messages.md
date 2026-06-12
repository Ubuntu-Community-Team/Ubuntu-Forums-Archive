---
title: "ZFS and boot messages"
date: 2020-01-20
forum: General Help
---

### Post by sfatula on 2020-01-20
When I reboot my ubuntu 18.04.03 machine, I often get emailed a bunch of zfs issues, sample:

```
ZFS has finished a resilver:

   eid: 66
 class: resilver_finish
  host: Home-Server
  time: 2020-01-20 17:33:53-0600
  pool: Raid
 state: DEGRADED
status: One or more devices could not be used because the label is missing or
    invalid.  Sufficient replicas exist for the pool to continue
    functioning in a degraded state.
action: Replace the device using 'zpool replace'.
   see: [http://zfsonlinux.org/msg/ZFS-8000-4J](http://zfsonlinux.org/msg/ZFS-8000-4J)
  scan: resilvered 1.08M in 0 days 00:00:01 with 0 errors on Mon Jan 20 17:33:53 2020
config:

    NAME                              STATE     READ WRITE CKSUM
    Raid                              DEGRADED     0     0     0
      raidz1-0                        DEGRADED     0     0     0
        wwn-0x50014ee0598b1fbe-part2  UNAVAIL      0     0     0
        wwn-0x50014ee0aebc440e-part2  ONLINE       0     0     0
        wwn-0x5000c5004ebf5f22-part2  ONLINE       0     0     0
        wwn-0x50014ee6b066d2d9-part2  ONLINE       0     0     0
      raidz1-1                        DEGRADED     0     0     0
        wwn-0x50014ee6b0706bbd-part2  ONLINE       0     0     0
        wwn-0x50014ee0040a58b7-part2  ONLINE       0     0     0
        wwn-0x5000c5004e85da20-part2  ONLINE       0     0     0
        wwn-0x5000c5004d471b6f-part2  UNAVAIL      0     0     0

errors: No known data errors

```
I may get 10 of these, I may get 30, I may get none. The devices are differnet in every email, I believe all of them end up with a message in at least 1 email. The resilver always finished, and eventually, the messages stop coming and all is well. Seems like it might be disks moving around, but, I am using the by-id names. So.... I don't understand what I am doing wrong or what is causing these? Is it perhaps starting too soon before hardware stuff is worked out? 

What can I do to solve this?

---

