---
title: "Sytem freez with corupt logs"
date: 2013-06-05
forum: General Help
---

### Post by n00ne on 2013-06-05
I have installed Ubuntu 13.04 on a new lenovo thinkpad x230 with ssd,
and I'm experiencing some random system freezes.
it seems to either happen 10-15 min after restart or not happen at all.
when I get a "good" boot I can work on the computer without any issues
for days and even suspend and wake with no problems. but if I do a proper restart the system might freeze within
10-15 minutes of the restart.

when I look at the syslog it seems like its got corrupted when the crash happens -
```

Jun  1 19:56:25 bob-lp kernel: [66074.832731] cfg80211: World regulatory domain updated:
Jun  1 19:56:25 bob-lp kernel: [66074.832736] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jun  1 19:56:25 bob-lp kernel: [66074.832738] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  1 19:56:25 bob-lp kernel: [66074.832739] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun  1 19:56:25 bob-lp kernel: [66074.832741] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun  1 19:56:25 bob-lp kernel: [66074.832742] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  1 19:56:25 bob-lp kernel: [66074.832743] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  1 19:56:25 bob-lp NetworkManager[1227]: <info> (wlan0): cleaning up...
Jun  1 19:56:25 bob-lp NetworkManager[1227]: <info> (wlan0): taking down device.
Jun  1 19:56:25 bob-lp dbus[811]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jun  1 19:56:25 bob-lp dbus[811]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun  1 19:56:26 bob-lp anacron[31311]: Anacron 2.3 started on 2013-06-01
Jun  1 19:56:26 bob-lp anacron[31311]: Normal exit (0 jobs run)
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^

```

any help detecting what might causing this issue would be appreciated

---

