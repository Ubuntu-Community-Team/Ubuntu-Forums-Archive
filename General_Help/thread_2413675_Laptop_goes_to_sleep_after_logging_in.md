---
title: "Laptop goes to sleep after logging in"
date: 2019-02-28
forum: General Help
---

### Post by branttaylor on 2019-02-28
Laptop: Dell Precision 5520

Events:
1. Laptop is powered down. Plug in laptop to Dell Thunderbolt TB16 dock and power on.
2. Log into desktop with user password.
3. Laptop immediately goes to sleep and requires the power button to be pressed to wake back up.

Observations:
-The laptop does not go to sleep when I am not plugged into the Thunderbolt dock but follow the same above steps of logging in after being powered down.
-Nothing seems to stand out in the syslog other than the message logging that sleep was requested, but I don't know what requested it. Grep for sleep below, and I attached the log .zip. Please help point me in the right direction! I can't tell why it's happening.

```

&#10140;  log cat syslog | grep sleep
Feb 28 08:15:36 a00016424 NetworkManager[994]: <info>  [1551363336.4060] manager: sleep: sleep requested (sleeping: no  enabled: yes)
Feb 28 08:15:36 a00016424 NetworkManager[994]: <info>  [1551363336.4077] device (wlp2s0): state change: activated -> deactivating (reason 'sleeping', sys-iface-state: 'managed')
Feb 28 08:15:36 a00016424 NetworkManager[994]: <info>  [1551363336.4098] device (wlp2s0): state change: deactivating -> disconnected (reason 'sleeping', sys-iface-state: 'managed')
Feb 28 08:15:36 a00016424 NetworkManager[994]: <info>  [1551363336.4995] device (wlp2s0): state change: disconnected -> unmanaged (reason 'sleeping', sys-iface-state: 'managed')
Feb 28 08:15:36 a00016424 systemd-sleep[3905]: Suspending system...
Feb 28 08:19:12 a00016424 kernel: [ 3135.307747] ACPI: Preparing to enter system sleep state S3
Feb 28 08:19:12 a00016424 kernel: [ 3135.492128]  cache: parent cpu1 should not be sleeping
Feb 28 08:19:12 a00016424 kernel: [ 3135.493845]  cache: parent cpu2 should not be sleeping
Feb 28 08:19:12 a00016424 kernel: [ 3135.495591]  cache: parent cpu3 should not be sleeping
Feb 28 08:19:12 a00016424 kernel: [ 3135.497391]  cache: parent cpu4 should not be sleeping
Feb 28 08:19:12 a00016424 kernel: [ 3135.497978]  cache: parent cpu5 should not be sleeping
Feb 28 08:19:12 a00016424 kernel: [ 3135.498576]  cache: parent cpu6 should not be sleeping
Feb 28 08:19:12 a00016424 kernel: [ 3135.499188]  cache: parent cpu7 should not be sleeping
Feb 28 08:19:12 a00016424 kernel: [ 3135.505718] ACPI: Waking up from system sleep state S3
Feb 28 08:19:12 a00016424 systemd-sleep[3905]: System resumed.
Feb 28 08:19:12 a00016424 systemd[1]: sleep.target: Unit not needed anymore. Stopping.
Feb 28 08:19:13 a00016424 NetworkManager[994]: <info>  [1551363553.2601] manager: sleep: wake requested (sleeping: yes  enabled: yes)
Feb 28 08:19:13 a00016424 NetworkManager[994]: <info>  [1551363553.2618] device (enxa44cc8a6c2e1): state change: unavailable -> unmanaged (reason 'sleeping', sys-iface-state: 'managed')

```

---

