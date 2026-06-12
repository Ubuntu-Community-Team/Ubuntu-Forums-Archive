---
title: "SynCe connection issue - any ideas ?"
date: 2007-08-17
forum: General Help
---

### Post by dcarpeneto on 2007-08-17
Hi all - looking for ideas - I've got a HTC TyTn that I'm trying to connect to via SynCe - odccm shows the following:

```
[B]** (odccm:7831): DEBUG: PDA network interface discovered! udi='/org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00'
** (odccm:7831): DEBUG: device_info_received
** (odccm:7831): DEBUG: f7 4d f1 19 15 c9 12 3e 23 bd 57 63 47 4f 25 00 05 00 00 00 01 00 00 00 0f 00 00 00 57 00 4d 00 5f 00 52 00 6f 00 6e 00 61 00 6c 00 64 00 5f 00 56 00 69 00 6c 00 6c 00 32 00 00 00 05 01 c3 00 11 0a 00 00 05 00 00 00 d5 07 d8 54 00 00 00 00 0f 00 00 00 50 6f 63 6b 65 74 50 43 00 53 53 44 4b 00 00 07 00 00 00 48 45 52 4d 32 30 30 00 02 00 00 00 04 00 00 00 00 00 00 00 05 00 00 00 00 00 00 00 00 00 00 00
** (odccm:7831): DEBUG: device_info_received: registering object path '/org/synce/odccm/Device/_19F14DF7_C915_3E12_23BD_5763474F2500_'
[/B]
```

... so the device shows up OK, and I get an IP address for device rndis0 (and I can ping the TyTn), so it looks like everything's cool, however running 'pls' results in:

```
**pls: Could not find configuration at path '(Default)'**
```

... any ideas ? I've been googling for a bit, however I haven't been able to solve this one yet.

Thx - Dave

---

