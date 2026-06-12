---
title: "Trusty server boot fails, but works on reboot"
date: 2014-06-01
forum: General Help
---

### Post by ScottJ97 on 2014-06-01
My Trusty server occasionally fails to reboot properly. The attached screen shows the console where it hangs. A hard reset always fixes it.

This time, it failed after an `apt-get upgrade; reboot` sequence, but IIRC it has failed before even without any upgrades involved.

After reboot, I cannot find any log files in /var/log relating to the failed boot.

The failed boot:
[ATTACH=CONFIG]253662[/ATTACH]

A successful boot looks like this:

```

...
[   16.399307] ipmi_si 00:0d: Found new BMC (man_id: 0x000000, prod_id: 0xaabb, dev_id: 0x20)
[   16.399312] ipmi_si 00:0d: IPMI kcs interface initialized
[   16.406427] mei_me 0000:00:16.0: Device doesn't have valid ME Interface
[   16.406429] mei_me 0000:00:16.0: initialization failed.
[   16.695086] [drm] Initialized drm 1.1.0 20060810
[   16.817821] [drm] AST 2300 detected
[   16.817846] [drm] dram 1632000000 1 32 01000000
[   16.817876] [TTM] Zone  kernel: Available graphics memory: 4056314 kiB
[   16.817877] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[   16.817878] [TTM] Initializing pool allocator
[   16.817881] [TTM] Initializing DMA pool allocator
[   16.826421] checking generic (f6000000 130000) vs hw (f6000000 1000000)
[   16.826422] fb: conflicting fb hw usage astdrmfb vs VESA VGA - removing generic driver
[   16.826443] Console: switching to colour dummy device 80x25
[   16.826662] fbcon: astdrmfb (fb0) is primary device
[   16.846140] Console: switching to colour frame buffer device 128x48
[   16.873796] ast 0000:04:00.0: fb0: astdrmfb frame buffer device
[   16.873797] ast 0000:04:00.0: registered panic notifier
[   16.873801] [drm] Initialized ast 0.1.0 20120228 for 0000:04:00.0 on minor 0
...

```

---

