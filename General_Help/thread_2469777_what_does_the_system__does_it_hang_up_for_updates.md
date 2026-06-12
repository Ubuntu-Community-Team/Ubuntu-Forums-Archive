---
title: "what does the system ? does it hang up for updates ?"
date: 2021-12-09
forum: General Help
---

### Post by alain.roger on 2021-12-09
Hi,

I'm still working on my logs and today I would like to understand what does the system ?
Here is my log extract:
```
déc. 09 08:51:56 PC0001 org.kde.KScreen[2241]:          m_crtc XRandRCrtc(0x55b16fb9a030)
déc. 09 08:51:56 PC0001 org.kde.KScreen[2241]:          CRTC: 441
déc. 09 08:51:56 PC0001 org.kde.KScreen[2241]:          MODE: 448
déc. 09 08:51:56 PC0001 org.kde.KScreen[2241]:          Connection: 0
déc. 09 08:51:56 PC0001 org.kde.KScreen[2241]:          Primary: false
déc. 09 08:51:56 PC0001 org.kde.KScreen[2241]: kscreen.xrandr: XRandR::setConfig done!

déc. 09 08:52:06 PC0001 PackageKit[2154]: get-updates transaction /2424_dccaacbe from uid 1000 finished with success after 501ms

déc. 09 08:52:22 PC0001 kernel: FS-Cache: Loaded
déc. 09 08:52:22 PC0001 kernel: FS-Cache: Netfs 'nfs' registered for caching
déc. 09 08:52:22 PC0001 kernel: NFS: Registering the id_resolver key type
déc. 09 08:52:22 PC0001 kernel: Key type id_resolver registered
déc. 09 08:52:22 PC0001 kernel: Key type id_legacy registered

déc. 09 08:52:36 PC0001 systemd[1837]: Starting Sound Service...
déc. 09 08:52:36 PC0001 rtkit-daemon[1636]: Successfully made thread 5206 of process 5206 owned by '1000' high priority at nice level -11.
déc. 09 08:52:36 PC0001 rtkit-daemon[1636]: Supervising 5 threads of 3 processes of 1 users.
déc. 09 08:52:36 PC0001 rtkit-daemon[1636]: Supervising 5 threads of 3 processes of 1 users.
```

To make it clearer, I added a line as space between actions/log status.

I'm analyzing my logs because I'm not satisfied by the time system needs to display my desktop from my log in time.
It takes too long from my point of view.

I would like to know if it's normal to have so much "not justified time" among thses actions:
```
déc. 09 08:51:56 PC0001 org.kde.KScreen[2241]: kscreen.xrandr: XRandR::setConfig done!

déc. 09 08:52:06 PC0001 PackageKit[2154]: get-updates transaction /2424_dccaacbe from uid 1000 finished with success after 501ms

déc. 09 08:52:22 PC0001 kernel: FS-Cache: Loaded
```

what does system do from 08:51:56 to 08:52:06 ?
the same question from 08:52:06 to 08:52:22 ?

when I run "sudo apt update && sudo apt upgrade" system does not need 16s amount time as written in logs.
so what's the problem ?
I'm lost, so can you explain me that step ?
thx

---

