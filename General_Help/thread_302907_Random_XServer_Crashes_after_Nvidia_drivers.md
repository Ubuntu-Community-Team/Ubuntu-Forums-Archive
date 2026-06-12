---
title: "Random XServer Crashes after Nvidia drivers"
date: 2006-11-19
forum: General Help
---

### Post by seanUSXIII on 2006-11-19
Ever since I installed the new Nvidia drivers (9629, NOT the betas) and removed XGL, I have been experiencing random Xserver lockups. I tried several fixes, including: changing to the 9742 drivers to see if they were better and downgrading Beryl to 0.1.1. Both tries yielded no results, it still crashses. So now im on Nvidia 9742 and Beryl 0.1.2. One event that seems to accompany it in my kern.log is an "APIC error on CPU0: 40(40)" 

```
Nov 19 00:08:46 localhost kernel: [17179626.716000] Bluetooth: RFCOMM ver 1.7
Nov 19 00:10:05 localhost kernel: [17179705.224000] APIC error on CPU0: 00(40)
Nov 19 00:10:42 localhost kernel: [17179742.360000] APIC error on CPU0: 40(40)
Nov 19 00:27:12 localhost kernel: [17180732.264000] APIC error on CPU0: 40(40)
Nov 19 00:36:29 localhost kernel: [17181289.176000] APIC error on CPU0: 40(40)
Nov 19 01:00:03 localhost kernel: [17182702.572000] ip_tables: (C) 2000-2006 Netfilter Core Team
Nov 19 01:04:00 localhost kernel: [17182939.892000] APIC error on CPU0: 40(40)
Nov 19 01:05:47 localhost kernel: [17183046.928000] APIC error on CPU0: 40(40)
Nov 19 01:08:12 localhost kernel: [17183191.536000] APIC error on CPU0: 40(40)
Nov 19 01:16:48 localhost kernel: [17183707.300000] APIC error on CPU0: 40(40)
Nov 19 01:33:07 localhost kernel: [17184686.752000] APIC error on CPU0: 40(40)
Nov 19 01:33:08 localhost kernel: [17184687.296000] APIC error on CPU0: 40(40)
Nov 19 01:49:40 localhost kernel: [17185679.088000] APIC error on CPU0: 40(40)
```

There is a sample of the kern.log. Really, any help is greatly appreciated. I'm thinking of going back to XGL, but then I'll lose things like VLC and direct rendering. ](*,)

---

### Post by seanUSXIII on 2006-11-19
bump??

---

### Post by seanUSXIII on 2006-11-19
anyone?

---

### Post by speedy78 on 2007-02-09
Here is the same, xserver suddenly crash and restart (mostly when playing some videos).
dmesg show apic errors and messages about agpgart:
```

[17199608.280000] APIC error on CPU0: 04(08)
[17199681.728000] APIC error on CPU0: 08(04)
[17199819.024000] APIC error on CPU0: 04(04)
[17199901.732000] APIC error on CPU0: 04(04)
[17200141.940000] APIC error on CPU0: 04(04)
[17200298.564000] APIC error on CPU0: 04(02)
[17200300.264000] APIC error on CPU0: 02(02)
[17200383.520000] APIC error on CPU0: 02(02)
[17200592.060000] APIC error on CPU0: 02(04)
[17200719.240000] APIC error on CPU0: 04(02)
[17200833.668000] APIC error on CPU0: 02(04)
[17200962.592000] APIC error on CPU0: 04(04)
[17201350.320000] APIC error on CPU0: 04(02)
[17201427.452000] APIC error on CPU0: 02(02)
[17201532.508000] APIC error on CPU0: 02(08)
[17201605.968000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[17201605.968000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17201605.968000] agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode

```
latest releases of nvidia binary driver seems to be blamed for me, all was ok few weeks ago.
i'm on edgy, nvidia driver 9629 for an agp nvidia 6600, kernel 2.6.17-10-generic on an athlon xp.

---

