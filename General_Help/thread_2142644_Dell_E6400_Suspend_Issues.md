---
title: "Dell E6400 Suspend Issues"
date: 2013-05-05
forum: General Help
---

### Post by burnout40k on 2013-05-05
Throwing in my issue as well. Will suspend, but won't wake. and if it does it has a scrambled screen.

Dell Latitude E6400

[http://paste.ubuntu.com/5634374/](http://paste.ubuntu.com/5634374/)

01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G98M [Quadro NVS 160M] [10de:06eb] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Dell Device [1028:0233]
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f5000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at f2000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at df00 [size=128]
	[virtual] Expansion ROM at f4000000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [128] Power Budgeting <?>

BOOT_IMAGE=/vmlinuz-3.8.0-19-generic root=/dev/mapper/ubuntu-root ro quiet splash vt.handoff=7

---

### Post by Toz on 2013-05-06
Moving post to its own thread.

---

### Post by Toz on 2013-05-06
Have you installed the proprietary nvidia driver?

What does the following command return?
```
cat /var/log/syslog  |grep PM:
```

EDIT: This bug report looks relevant: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1156552]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1156552")

---

