---
title: "Slow boot time (dmesg attached)"
date: 2013-01-09
forum: General Help
---

### Post by retrodans on 2013-01-09
So it seems like the boot time of my local ubuntu setup is not perfect (approx. 60s).  From looking at other posts, they suggest running dmesg to see if there are any obvious delays there.

I have pasted the results of a snippet of my results, and can see a delay here.  Would I be right in thinking the time is the start time of a process, therefore the line marked "mounted filesystem with ordered data mode" is the process causing the delay.

If so, is this just how it is, or is there a chance there is a bug with my setup here?

Thanks,
Dan



[PHP][    6.612441] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    6.944716] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[    6.944721] EXT4-fs (sda5): write access will be enabled during recovery
[   11.567028] EXT4-fs (sda5): recovery complete
[   11.567475] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   49.759673] Adding 3145792k swap on /dev/sda3.  Priority:-1 extents:1 across:3145792k 
[   49.766096] ADDRCONF(NETDEV_UP): eth0: link is not ready
[/PHP]

---

