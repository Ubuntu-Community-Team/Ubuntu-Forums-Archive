---
title: "Semi-freezes with error irq timeout: status=0x80 { Busy }"
date: 2007-06-03
forum: General Help
---

### Post by FuturePilot on 2007-06-03
This keeps happening to me more and more. My computer will semi-freeze. It will lock up for a few seconds and then it will be fine for a few moments. Then it will lock up again. It keeps going on like that until I reboot. Then when I go to reboot it takes a long time to shut down and sometimes the splash screen goes away and I get these messages about ```
hdb: drive not ready for command
```.

I looked in /var/log and found these errors when these freezes happen
```
Jun  3 17:15:22 localhost kernel: [17186112.972000] hdb: irq timeout: status=0xd0 { Busy }
Jun  3 17:15:22 localhost kernel: [17186112.972000] ide: failed opcode was: unknown
Jun  3 17:15:22 localhost kernel: [17186112.972000] hdb: DMA disabled
Jun  3 17:15:22 localhost kernel: [17186113.020000] hdb: ATAPI reset complete
Jun  3 17:15:28 localhost kernel: [17186118.292000] hdb: irq timeout: status=0x80 { Busy }
Jun  3 17:15:28 localhost kernel: [17186118.292000] ide: failed opcode was: unknown
Jun  3 17:15:28 localhost kernel: [17186118.340000] hdb: ATAPI reset complete
Jun  3 17:15:33 localhost kernel: [17186123.612000] hdb: irq timeout: status=0x80 { Busy }
Jun  3 17:15:33 localhost kernel: [17186123.612000] ide: failed opcode was: unknown
Jun  3 17:15:38 localhost kernel: [17186128.880000] hdb: status timeout: status=0x80 { Busy }
Jun  3 17:15:38 localhost kernel: [17186128.880000] ide: failed opcode was: unknown
Jun  3 17:15:38 localhost kernel: [17186128.880000] hdb: drive not ready for command
Jun  3 17:15:38 localhost kernel: [17186128.928000] hdb: ATAPI reset complete
Jun  3 17:15:43 localhost kernel: [17186134.204000] hdb: irq timeout: status=0xd0 { Busy }
Jun  3 17:15:43 localhost kernel: [17186134.204000] ide: failed opcode was: unknown
Jun  3 17:15:44 localhost kernel: [17186134.252000] hdb: ATAPI reset complete
Jun  3 17:15:49 localhost kernel: [17186139.524000] hdb: irq timeout: status=0x80 { Busy }
Jun  3 17:15:49 localhost kernel: [17186139.524000] ide: failed opcode was: unknown
Jun  3 17:15:49 localhost kernel: [17186139.572000] hdb: ATAPI reset complete
Jun  3 17:15:54 localhost kernel: [17186144.844000] hdb: irq timeout: status=0x80 { Busy }
Jun  3 17:15:54 localhost kernel: [17186144.844000] ide: failed opcode was: unknown
Jun  3 17:15:59 localhost kernel: [17186150.116000] hdb: status timeout: status=0x80 { Busy }
Jun  3 17:15:59 localhost kernel: [17186150.116000] ide: failed opcode was: unknown
Jun  3 17:15:59 localhost kernel: [17186150.116000] hdb: drive not ready for command
Jun  3 17:15:59 localhost kernel: [17186150.164000] hdb: ATAPI reset complete
Jun  3 17:16:05 localhost kernel: [17186155.440000] hdb: irq timeout: status=0xd0 { Busy }
Jun  3 17:16:05 localhost kernel: [17186155.440000] ide: failed opcode was: unknown
Jun  3 17:16:05 localhost kernel: [17186155.488000] hdb: ATAPI reset complete
Jun  3 17:16:10 localhost kernel: [17186160.756000] hdb: irq timeout: status=0x80 { Busy }
Jun  3 17:16:10 localhost kernel: [17186160.756000] ide: failed opcode was: unknown
Jun  3 17:16:10 localhost kernel: [17186160.804000] hdb: ATAPI reset complete
Jun  3 17:16:15 localhost kernel: [17186166.108000] hdb: irq timeout: status=0x80 { Busy }
Jun  3 17:16:15 localhost kernel: [17186166.108000] ide: failed opcode was: unknown
Jun  3 17:16:21 localhost kernel: [17186171.420000] hdb: status timeout: status=0x80 { Busy }
Jun  3 17:16:21 localhost kernel: [17186171.420000] ide: failed opcode was: unknown
Jun  3 17:16:21 localhost kernel: [17186171.420000] hdb: drive not ready for command
Jun  3 17:16:21 localhost kernel: [17186171.468000] hdb: ATAPI reset complete
Jun  3 17:16:26 localhost kernel: [17186176.784000] hdb: irq timeout: status=0xd0 { Busy }
Jun  3 17:16:26 localhost kernel: [17186176.784000] ide: failed opcode was: unknown
Jun  3 17:16:26 localhost kernel: [17186176.832000] hdb: ATAPI reset complete
```
What's going on? Is this hardware related? Could this mean my hard drive is going to crap out on me?

---

### Post by FuturePilot on 2007-06-03
hdb is actually referring to my CD drive?

---

### Post by FuturePilot on 2007-06-04
Bump

---

### Post by FuturePilot on 2007-06-05
Does someone at least know what these errors are referring to? Anything at all?

---

