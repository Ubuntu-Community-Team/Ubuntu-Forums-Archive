---
title: "Help please! Serios problems leading to a complete freeze."
date: 2008-05-03
forum: General Help
---

### Post by descentspb on 2008-05-03
This happens for the second time today already.
At some point, the system starts laggin' seriously. The cpu usage is going up and up, but NO applications are using so much cpu according to top, htop and gnome system monitor. Then it reaches 100% cpu load on each core, and the system becomes totally unresponsive. Even ctrl-alt-f1 and ctrl-alt-backspace do not save me. [COLOR="Red"]Screenshot attached[/COLOR] (look at the **overall cpu load** in the top and the **application cpu load**, descending sort). What can that be?

The system is Hardy, haven't noticed anything similar while using Gutsy.

If /var/log/kernel.log is the file i need to inspect, then the only thing that was happening a little time ago before the incident is
```
May  3 23:00:17 descent kernel: [ 5413.699321] atl1 0000:02:00.0: hw csum wrong, pkt_flag:2600, err_flag:40
May  3 23:14:40 descent kernel: [ 6276.067170] atl1 0000:02:00.0: hw csum wrong, pkt_flag:2600, err_flag:40
May  3 23:14:40 descent kernel: [ 6276.067177] atl1 0000:02:00.0: hw csum wrong,
 pkt_flag:2600, err_flag:40
May  3 23:14:40 descent kernel: [ 6276.067179] atl1 0000:02:00.0: hw csum wrong, pkt_flag:2600, err_flag:40
May  3 23:21:55 descent kernel: [ 6711.124766] atl1 0000:02:00.0: hw csum wrong, pkt_flag:2600, err_flag:40
May  3 23:21:55 descent kernel: [ 6711.124771] atl1 0000:02:00.0: hw csum wrong, pkt_flag:2600, err_flag:40
May  3 23:21:55 descent kernel: [ 6711.124968] atl1 0000:02:00.0: hw csum wrong, pkt_flag:2600, err_flag:40
May  3 23:24:22 descent kernel: [ 6857.963834] atl1 0000:02:00.0: hw csum wrong, pkt_flag:2600, err_flag:40
May  3 23:24:22 descent kernel: [ 6857.964036] atl1 0000:02:00.0: hw csum wrong, pkt_flag:2600, err_flag:40
May  3 23:24:22 descent kernel: [ 6857.964039] atl1 0000:02:00.0: hw csum wrong, pkt_flag:2600, err_flag:40
May  3 23:28:24 descent kernel: [ 7099.402301] atl1 0000:02:00.0: hw csum wrong, pkt_flag:2600, err_flag:40

```

I think that atl1 is Attansic L1 ethernet controller.

---

### Post by descentspb on 2008-05-05
Figuret it out. Somehow my swap partition has lost  its UUID. And due to that, it stopped mounting on system start. The system itself didn't tell me anything about it, so I didn't know that i was working without any swap space.

---

