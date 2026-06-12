---
title: "Strange SATA Issues with new HDD"
date: 2008-01-26
forum: General Help
---

### Post by gdi2k on 2008-01-26
I recently added a second 500 GB SATA drive to my machine. Since then, I've had occasional freezes. When it freezes, the system tends to recover after about a minute.

dmesg shows the following when this occurs: 

```
[ 4327.784000] ata4: timeout waiting for ADMA IDLE, stat=0x440
[ 4327.784000] ata4.00: exception Emask 0x0 SAct 0x3ffff SErr 0x0 action 0x0
[ 4327.784000] ata4.00: (CPB resp_flags 0x11: CMD error)
[ 4327.784000] ata4.00: cmd 61/18:00:5c:4e:ed/00:00:02:00:00/40 tag 0 cdb 0x0 data 12288 out
[ 4327.784000]          res 41/04:18:5c:4e:ed/00:00:02:00:00/40 Emask 0x1 (device error)
[ 4327.784000] ata4.00: cmd 61/38:08:3c:52:ed/00:00:02:00:00/40 tag 1 cdb 0x0 data 28672 out
[ 4327.784000]          res 41/04:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x1 (device error)
[ 4327.784000] ata4.00: cmd 61/28:10:8c:52:ed/00:00:02:00:00/40 tag 2 cdb 0x0 data 20480 out
[ 4327.784000]          res 41/04:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x1 (device error)
[ 4327.784000] ata4.00: cmd 61/38:18:3c:56:ed/00:00:02:00:00/40 tag 3 cdb 0x0 data 28672 out
[ 4327.784000]          res 41/04:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x1 (device error)
[ 4327.784000] ata4.00: cmd 61/38:20:7c:64:ed/00:00:02:00:00/40 tag 4 cdb 0x0 data 28672 out
[ 4327.784000]          res 41/04:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x1 (device error)
[ 4327.784000] ata4.00: cmd 61/38:28:3c:6a:ed/00:00:02:00:00/40 tag 5 cdb 0x0 data 28672 out
[ 4327.784000]          res 41/04:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x1 (device error)
[ 4327.784000] ata4.00: cmd 61/38:30:3c:6e:ed/00:00:02:00:00/40 tag 6 cdb 0x0 data 28672 out
[ 4327.784000]          res 41/04:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x1 (device error)
[ 4327.784000] ata4.00: cmd 61/38:38:3c:70:ed/00:00:02:00:00/40 tag 7 cdb 0x0 data 28672 out
[ 4327.784000]          res 41/04:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x1 (device error)
[ 4327.784000] ata4.00: cmd 61/10:40:a4:70:ed/00:00:02:00:00/40 tag 8 cdb 0x0 data 8192 out
[ 4327.784000]          res 41/04:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x1 (device error)
[ 4327.784000] ata4.00: cmd 61/30:48:44:77:ed/00:00:02:00:00/40 tag 9 cdb 0x0 data 24576 out
[ 4327.784000]          res 41/04:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x1 (device error)
[ 4327.784000] ata4.00: cmd 61/38:50:3c:4a:f6/00:00:02:00:00/40 tag 10 cdb 0x0 data 28672 out
[ 4327.784000]          res 41/04:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x1 (device error)
[ 4327.784000] ata4.00: cmd 61/38:58:bc:4a:f6/00:00:02:00:00/40 tag 11 cdb 0x0 data 28672 out
[ 4327.784000]          res 41/04:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x1 (device error)
[ 4327.784000] ata4.00: cmd 61/18:60:54:e3:e7/00:00:02:00:00/40 tag 12 cdb 0x0 data 12288 out
[ 4327.784000]          res 41/04:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x1 (device error)
[ 4327.784000] ata4.00: cmd 61/08:68:14:eb:e7/00:00:02:00:00/40 tag 13 cdb 0x0 data 4096 out
[ 4327.784000]          res 41/04:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x1 (device error)
[ 4327.784000] ata4.00: cmd 61/20:70:94:4c:ed/00:00:02:00:00/40 tag 14 cdb 0x0 data 16384 out
[ 4327.784000]          res 41/04:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x1 (device error)
[ 4327.784000] ata4.00: cmd 61/10:78:4c:4e:ed/00:00:02:00:00/40 tag 15 cdb 0x0 data 8192 out
[ 4327.784000]          res 41/04:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x1 (device error)
[ 4327.784000] ata4.00: cmd 61/08:80:7c:db:e8/00:00:02:00:00/40 tag 16 cdb 0x0 data 4096 out
[ 4327.784000]          res 41/04:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x1 (device error)
[ 4327.784000] ata4.00: cmd 61/28:88:f4:de:e8/00:00:02:00:00/40 tag 17 cdb 0x0 data 20480 out
[ 4327.784000]          res 41/04:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x1 (device error)
[ 4327.800000] ata4.00: configured for UDMA/133
[ 4327.800000] ata4: EH complete
[ 4327.800000] ata4: timeout waiting for ADMA LEGACY clear and IDLE, stat=0x440
[ 4327.804000] sd 4:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[ 4327.804000] sd 4:0:0:0: [sdb] Write Protect is off
[ 4327.804000] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[ 4327.804000] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 4357.800000] ata4: EH in ADMA mode, notifier 0x0 notifier_error 0x0 gen_ctl 0x1501000 status 0x400 next cpb count 0x20 next cpb idx 0x0
[ 4357.800000] ata4: CPB 1: ctl_flags 0x1f, resp_flags 0x0
[ 4357.800000] ata4: CPB 2: ctl_flags 0x1f, resp_flags 0x0
[ 4357.800000] ata4: CPB 3: ctl_flags 0x1f, resp_flags 0x0
[ 4357.800000] ata4: CPB 4: ctl_flags 0x1f, resp_flags 0x0
[ 4357.800000] ata4: CPB 5: ctl_flags 0x1f, resp_flags 0x0
[ 4357.800000] ata4: CPB 6: ctl_flags 0x1f, resp_flags 0x0
[ 4357.800000] ata4: CPB 7: ctl_flags 0x1f, resp_flags 0x0
[ 4357.800000] ata4: CPB 8: ctl_flags 0x1f, resp_flags 0x0
[ 4357.800000] ata4: CPB 9: ctl_flags 0x1f, resp_flags 0x0
[ 4357.800000] ata4: CPB 10: ctl_flags 0x1f, resp_flags 0x0
[ 4357.800000] ata4: CPB 11: ctl_flags 0x1f, resp_flags 0x0
[ 4357.800000] ata4: CPB 12: ctl_flags 0x1f, resp_flags 0x0
[ 4357.800000] ata4: CPB 13: ctl_flags 0x1f, resp_flags 0x0
[ 4357.800000] ata4: CPB 14: ctl_flags 0x1f, resp_flags 0x0
[ 4357.800000] ata4: CPB 15: ctl_flags 0x1f, resp_flags 0x0
[ 4357.800000] ata4: CPB 16: ctl_flags 0x1f, resp_flags 0x0
[ 4357.800000] ata4: CPB 17: ctl_flags 0x1f, resp_flags 0x0
[ 4357.800000] ata4: timeout waiting for ADMA IDLE, stat=0x400
[ 4357.800000] ata4: timeout waiting for ADMA LEGACY, stat=0x400
[ 4357.800000] ata4.00: exception Emask 0x0 SAct 0x3fffe SErr 0x0 action 0x2 frozen
[ 4357.800000] ata4.00: cmd 61/08:08:7c:db:e8/00:00:02:00:00/40 tag 1 cdb 0x0 data 4096 out
[ 4357.800000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4357.800000] ata4.00: cmd 61/10:10:4c:4e:ed/00:00:02:00:00/40 tag 2 cdb 0x0 data 8192 out
[ 4357.800000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4357.800000] ata4.00: cmd 61/20:18:94:4c:ed/00:00:02:00:00/40 tag 3 cdb 0x0 data 16384 out
[ 4357.800000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4357.800000] ata4.00: cmd 61/08:20:14:eb:e7/00:00:02:00:00/40 tag 4 cdb 0x0 data 4096 out
[ 4357.800000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4357.800000] ata4.00: cmd 61/18:28:54:e3:e7/00:00:02:00:00/40 tag 5 cdb 0x0 data 12288 out
[ 4357.800000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4357.800000] ata4.00: cmd 61/38:30:bc:4a:f6/00:00:02:00:00/40 tag 6 cdb 0x0 data 28672 out
[ 4357.800000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4357.800000] ata4.00: cmd 61/38:38:3c:4a:f6/00:00:02:00:00/40 tag 7 cdb 0x0 data 28672 out
[ 4357.800000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4357.800000] ata4.00: cmd 61/30:40:44:77:ed/00:00:02:00:00/40 tag 8 cdb 0x0 data 24576 out
[ 4357.800000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4357.800000] ata4.00: cmd 61/10:48:a4:70:ed/00:00:02:00:00/40 tag 9 cdb 0x0 data 8192 out
[ 4357.800000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4357.800000] ata4.00: cmd 61/38:50:3c:70:ed/00:00:02:00:00/40 tag 10 cdb 0x0 data 28672 out
[ 4357.800000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4357.800000] ata4.00: cmd 61/38:58:3c:6e:ed/00:00:02:00:00/40 tag 11 cdb 0x0 data 28672 out
[ 4357.800000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4357.800000] ata4.00: cmd 61/38:60:3c:6a:ed/00:00:02:00:00/40 tag 12 cdb 0x0 data 28672 out
[ 4357.800000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4357.800000] ata4.00: cmd 61/38:68:7c:64:ed/00:00:02:00:00/40 tag 13 cdb 0x0 data 28672 out
[ 4357.800000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4357.800000] ata4.00: cmd 61/38:70:3c:56:ed/00:00:02:00:00/40 tag 14 cdb 0x0 data 28672 out
[ 4357.800000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4357.800000] ata4.00: cmd 61/28:78:8c:52:ed/00:00:02:00:00/40 tag 15 cdb 0x0 data 20480 out
[ 4357.800000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4357.800000] ata4.00: cmd 61/38:80:3c:52:ed/00:00:02:00:00/40 tag 16 cdb 0x0 data 28672 out
[ 4357.800000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4357.800000] ata4.00: cmd 61/18:88:5c:4e:ed/00:00:02:00:00/40 tag 17 cdb 0x0 data 12288 out
[ 4357.800000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4358.112000] ata4: soft resetting port
[ 4358.268000] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 4358.304000] ata4.00: configured for UDMA/133
[ 4358.304000] ata4: EH complete
[ 4358.304000] ata4: timeout waiting for ADMA LEGACY clear and IDLE, stat=0x400
[ 4358.304000] sd 4:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[ 4358.304000] sd 4:0:0:0: [sdb] Write Protect is off
[ 4358.304000] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[ 4358.304000] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 4404.712000] ata4: EH in ADMA mode, notifier 0x0 notifier_error 0x0 gen_ctl 0x1501000 status 0x400 next cpb count 0x14 next cpb idx 0x0
[ 4404.712000] ata4: CPB 0: ctl_flags 0x1f, resp_flags 0x2
[ 4404.712000] ata4: CPB 1: ctl_flags 0x1f, resp_flags 0x0
[ 4404.712000] ata4: CPB 2: ctl_flags 0x1f, resp_flags 0x0
[ 4404.712000] ata4: CPB 3: ctl_flags 0x1f, resp_flags 0x0
[ 4404.712000] ata4: CPB 4: ctl_flags 0x1f, resp_flags 0x0
[ 4404.712000] ata4: CPB 5: ctl_flags 0x1f, resp_flags 0x0
[ 4404.712000] ata4: CPB 6: ctl_flags 0x1f, resp_flags 0x0
[ 4404.712000] ata4: CPB 7: ctl_flags 0x1f, resp_flags 0x0
[ 4404.712000] ata4: CPB 8: ctl_flags 0x1f, resp_flags 0x0
[ 4404.712000] ata4: CPB 9: ctl_flags 0x1f, resp_flags 0x0
[ 4404.712000] ata4: CPB 10: ctl_flags 0x1f, resp_flags 0x0
[ 4404.712000] ata4: CPB 11: ctl_flags 0x1f, resp_flags 0x0
[ 4404.712000] ata4: CPB 12: ctl_flags 0x1f, resp_flags 0x0
[ 4404.712000] ata4: CPB 13: ctl_flags 0x1f, resp_flags 0x0
[ 4404.712000] ata4: CPB 14: ctl_flags 0x1f, resp_flags 0x0
[ 4404.712000] ata4: CPB 15: ctl_flags 0x1f, resp_flags 0x0
[ 4404.712000] ata4: CPB 16: ctl_flags 0x1f, resp_flags 0x0
[ 4404.712000] ata4: CPB 17: ctl_flags 0x1f, resp_flags 0x0
[ 4404.712000] ata4: CPB 18: ctl_flags 0x1f, resp_flags 0x0
[ 4404.712000] ata4: CPB 19: ctl_flags 0x1f, resp_flags 0x0
[ 4404.712000] ata4: CPB 20: ctl_flags 0x1f, resp_flags 0x0
[ 4404.712000] ata4: timeout waiting for ADMA IDLE, stat=0x400
[ 4404.712000] ata4: timeout waiting for ADMA LEGACY, stat=0x400
[ 4404.712000] ata4.00: exception Emask 0x0 SAct 0x1fffff SErr 0x0 action 0x2 frozen
[ 4404.712000] ata4.00: cmd 61/18:00:5c:4e:ed/00:00:02:00:00/40 tag 0 cdb 0x0 data 12288 out
[ 4404.712000]          res 40/00:18:5c:4e:ed/00:00:02:00:00/40 Emask 0x4 (timeout)
[ 4404.712000] ata4.00: cmd 61/38:08:3c:52:ed/00:00:02:00:00/40 tag 1 cdb 0x0 data 28672 out
[ 4404.712000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4404.712000] ata4.00: cmd 61/28:10:8c:52:ed/00:00:02:00:00/40 tag 2 cdb 0x0 data 20480 out
[ 4404.712000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4404.712000] ata4.00: cmd 61/38:18:3c:56:ed/00:00:02:00:00/40 tag 3 cdb 0x0 data 28672 out
[ 4404.712000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4404.712000] ata4.00: cmd 61/38:20:7c:64:ed/00:00:02:00:00/40 tag 4 cdb 0x0 data 28672 out
[ 4404.712000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4404.712000] ata4.00: cmd 61/38:28:3c:6a:ed/00:00:02:00:00/40 tag 5 cdb 0x0 data 28672 out
[ 4404.712000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4404.712000] ata4.00: cmd 61/38:30:3c:6e:ed/00:00:02:00:00/40 tag 6 cdb 0x0 data 28672 out
[ 4404.712000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4404.712000] ata4.00: cmd 61/38:38:3c:70:ed/00:00:02:00:00/40 tag 7 cdb 0x0 data 28672 out
[ 4404.712000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4404.712000] ata4.00: cmd 61/10:40:a4:70:ed/00:00:02:00:00/40 tag 8 cdb 0x0 data 8192 out
[ 4404.712000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4404.712000] ata4.00: cmd 61/30:48:44:77:ed/00:00:02:00:00/40 tag 9 cdb 0x0 data 24576 out
[ 4404.712000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4404.712000] ata4.00: cmd 61/38:50:3c:4a:f6/00:00:02:00:00/40 tag 10 cdb 0x0 data 28672 out
[ 4404.712000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4404.712000] ata4.00: cmd 61/38:58:bc:4a:f6/00:00:02:00:00/40 tag 11 cdb 0x0 data 28672 out
[ 4404.712000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4404.712000] ata4.00: cmd 61/18:60:54:e3:e7/00:00:02:00:00/40 tag 12 cdb 0x0 data 12288 out
[ 4404.712000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4404.712000] ata4.00: cmd 61/08:68:14:eb:e7/00:00:02:00:00/40 tag 13 cdb 0x0 data 4096 out
[ 4404.712000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4404.712000] ata4.00: cmd 61/20:70:94:4c:ed/00:00:02:00:00/40 tag 14 cdb 0x0 data 16384 out
[ 4404.712000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4404.712000] ata4.00: cmd 61/10:78:4c:4e:ed/00:00:02:00:00/40 tag 15 cdb 0x0 data 8192 out
[ 4404.712000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4404.712000] ata4.00: cmd 61/08:80:7c:db:e8/00:00:02:00:00/40 tag 16 cdb 0x0 data 4096 out
[ 4404.712000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4404.712000] ata4.00: cmd 60/01:88:3f:1e:bf/00:00:01:00:00/40 tag 17 cdb 0x0 data 512 in
[ 4404.712000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4404.712000] ata4.00: cmd 60/01:90:40:1e:bf/00:00:01:00:00/40 tag 18 cdb 0x0 data 512 in
[ 4404.712000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[ 4404.712000] ata4.00: cmd 60/01:98:41:1e:bf/00:00:01:00:00/40 tag 19 cdb 0x0 data 512 in
[ 4404.712000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[ 4404.712000] ata4.00: cmd 60/01:a0:42:1e:bf/00:00:01:00:00/40 tag 20 cdb 0x0 data 512 in
[ 4404.712000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[ 4405.024000] ata4: soft resetting port
[ 4405.180000] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 4405.216000] ata4.00: configured for UDMA/133
[ 4405.216000] ata4: EH complete
[ 4405.216000] ata4: timeout waiting for ADMA LEGACY clear and IDLE, stat=0x400
[ 4405.216000] sd 4:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[ 4405.216000] sd 4:0:0:0: [sdb] Write Protect is off
[ 4405.216000] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[ 4405.216000] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 4435.216000] ata4: EH in ADMA mode, notifier 0x0 notifier_error 0x0 gen_ctl 0x1501000 status 0x400 next cpb count 0x14 next cpb idx 0x0
[ 4435.216000] ata4: CPB 0: ctl_flags 0x1f, resp_flags 0x2
[ 4435.216000] ata4: CPB 1: ctl_flags 0x1f, resp_flags 0x0
[ 4435.216000] ata4: CPB 2: ctl_flags 0x1f, resp_flags 0x0
[ 4435.216000] ata4: CPB 3: ctl_flags 0x1f, resp_flags 0x0
[ 4435.216000] ata4: CPB 4: ctl_flags 0x1f, resp_flags 0x0
[ 4435.216000] ata4: CPB 5: ctl_flags 0x1f, resp_flags 0x0
[ 4435.216000] ata4: CPB 6: ctl_flags 0x1f, resp_flags 0x0
[ 4435.216000] ata4: CPB 7: ctl_flags 0x1f, resp_flags 0x0
[ 4435.216000] ata4: CPB 8: ctl_flags 0x1f, resp_flags 0x0
[ 4435.216000] ata4: CPB 9: ctl_flags 0x1f, resp_flags 0x0
[ 4435.216000] ata4: CPB 10: ctl_flags 0x1f, resp_flags 0x0
[ 4435.216000] ata4: CPB 11: ctl_flags 0x1f, resp_flags 0x0
[ 4435.216000] ata4: CPB 12: ctl_flags 0x1f, resp_flags 0x0
[ 4435.216000] ata4: CPB 13: ctl_flags 0x1f, resp_flags 0x0
[ 4435.216000] ata4: CPB 14: ctl_flags 0x1f, resp_flags 0x0
[ 4435.216000] ata4: CPB 15: ctl_flags 0x1f, resp_flags 0x0
[ 4435.216000] ata4: CPB 16: ctl_flags 0x1f, resp_flags 0x0
[ 4435.216000] ata4: CPB 17: ctl_flags 0x1f, resp_flags 0x0
[ 4435.216000] ata4: CPB 18: ctl_flags 0x1f, resp_flags 0x0
[ 4435.216000] ata4: CPB 19: ctl_flags 0x1f, resp_flags 0x0
[ 4435.216000] ata4: CPB 20: ctl_flags 0x1f, resp_flags 0x0
[ 4435.216000] ata4: timeout waiting for ADMA IDLE, stat=0x400
[ 4435.216000] ata4: timeout waiting for ADMA LEGACY, stat=0x400
[ 4435.216000] ata4.00: NCQ disabled due to excessive errors
[ 4435.216000] ata4.00: exception Emask 0x0 SAct 0x1fffff SErr 0x0 action 0x2 frozen
[ 4435.216000] ata4.00: cmd 60/01:00:42:1e:bf/00:00:01:00:00/40 tag 0 cdb 0x0 data 512 in
[ 4435.216000]          res 40/00:18:5c:4e:ed/00:00:02:00:00/40 Emask 0x4 (timeout)
[ 4435.216000] ata4.00: cmd 60/01:08:41:1e:bf/00:00:01:00:00/40 tag 1 cdb 0x0 data 512 in
[ 4435.216000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4435.216000] ata4.00: cmd 60/01:10:40:1e:bf/00:00:01:00:00/40 tag 2 cdb 0x0 data 512 in
[ 4435.216000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4435.216000] ata4.00: cmd 60/01:18:3f:1e:bf/00:00:01:00:00/40 tag 3 cdb 0x0 data 512 in
[ 4435.216000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4435.216000] ata4.00: cmd 61/08:20:7c:db:e8/00:00:02:00:00/40 tag 4 cdb 0x0 data 4096 out
[ 4435.216000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4435.216000] ata4.00: cmd 61/10:28:4c:4e:ed/00:00:02:00:00/40 tag 5 cdb 0x0 data 8192 out
[ 4435.216000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4435.216000] ata4.00: cmd 61/20:30:94:4c:ed/00:00:02:00:00/40 tag 6 cdb 0x0 data 16384 out
[ 4435.216000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4435.216000] ata4.00: cmd 61/08:38:14:eb:e7/00:00:02:00:00/40 tag 7 cdb 0x0 data 4096 out
[ 4435.216000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4435.216000] ata4.00: cmd 61/18:40:54:e3:e7/00:00:02:00:00/40 tag 8 cdb 0x0 data 12288 out
[ 4435.216000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4435.216000] ata4.00: cmd 61/38:48:bc:4a:f6/00:00:02:00:00/40 tag 9 cdb 0x0 data 28672 out
[ 4435.216000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4435.216000] ata4.00: cmd 61/38:50:3c:4a:f6/00:00:02:00:00/40 tag 10 cdb 0x0 data 28672 out
[ 4435.216000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4435.216000] ata4.00: cmd 61/30:58:44:77:ed/00:00:02:00:00/40 tag 11 cdb 0x0 data 24576 out
[ 4435.216000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4435.216000] ata4.00: cmd 61/10:60:a4:70:ed/00:00:02:00:00/40 tag 12 cdb 0x0 data 8192 out
[ 4435.216000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4435.216000] ata4.00: cmd 61/38:68:3c:70:ed/00:00:02:00:00/40 tag 13 cdb 0x0 data 28672 out
[ 4435.216000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4435.216000] ata4.00: cmd 61/38:70:3c:6e:ed/00:00:02:00:00/40 tag 14 cdb 0x0 data 28672 out
[ 4435.216000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4435.216000] ata4.00: cmd 61/38:78:3c:6a:ed/00:00:02:00:00/40 tag 15 cdb 0x0 data 28672 out
[ 4435.216000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4435.216000] ata4.00: cmd 61/38:80:7c:64:ed/00:00:02:00:00/40 tag 16 cdb 0x0 data 28672 out
[ 4435.216000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4435.216000] ata4.00: cmd 61/38:88:3c:56:ed/00:00:02:00:00/40 tag 17 cdb 0x0 data 28672 out
[ 4435.216000]          res 40/00:ff:bb:3e:e9/04:ff:02:00:00/40 Emask 0x4 (timeout)
[ 4435.216000] ata4.00: cmd 61/28:90:8c:52:ed/00:00:02:00:00/40 tag 18 cdb 0x0 data 20480 out
[ 4435.216000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[ 4435.216000] ata4.00: cmd 61/38:98:3c:52:ed/00:00:02:00:00/40 tag 19 cdb 0x0 data 28672 out
[ 4435.216000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[ 4435.216000] ata4.00: cmd 61/18:a0:5c:4e:ed/00:00:02:00:00/40 tag 20 cdb 0x0 data 12288 out
[ 4435.216000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[ 4435.528000] ata4: soft resetting port
[ 4435.684000] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 4435.712000] ata4.00: configured for UDMA/133
[ 4435.712000] ata4: EH complete
[ 4435.712000] ata4: timeout waiting for ADMA LEGACY clear and IDLE, stat=0x400
[ 4465.712000] ata4: EH in ADMA mode, notifier 0x0 notifier_error 0x0 gen_ctl 0x1501000 status 0x400 next cpb count 0x0 next cpb idx 0x0
[ 4465.712000] ata4: CPB 0: ctl_flags 0xd, resp_flags 0x0
[ 4465.712000] ata4: timeout waiting for ADMA IDLE, stat=0x400
[ 4465.712000] ata4: timeout waiting for ADMA LEGACY, stat=0x400
[ 4465.712000] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 4465.712000] ata4.00: cmd ca/00:18:5c:4e:ed/00:00:00:00:00/e2 tag 0 cdb 0x0 data 12288 out
[ 4465.712000]          res 40/00:18:5c:4e:ed/00:00:02:00:00/40 Emask 0x4 (timeout)
[ 4466.024000] ata4: soft resetting port
[ 4466.180000] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 4466.216000] ata4.00: configured for UDMA/133
[ 4466.216000] ata4: EH complete
[ 4466.232000] sd 4:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[ 4466.232000] sd 4:0:0:0: [sdb] Write Protect is off
[ 4466.232000] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[ 4466.232000] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 4466.232000] sd 4:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[ 4466.232000] sd 4:0:0:0: [sdb] Write Protect is off
[ 4466.232000] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[ 4466.232000] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
```

Do you think it's a SATA issue or a HDD issue? It always relates to sdb, which is my new drive. 

Any ideas? 

Thanks!

---

### Post by dcstar on 2008-01-26
> **gdi2k said:**
> I recently added a second 500 GB SATA drive to my machine. Since then, I've had occasional freezes. When it freezes, the system tends to recover after about a minute.
............
Do you think it's a SATA issue or a HDD issue? It always relates to sdb, which is my new drive. 

Any ideas? 

Thanks!

You should install the **smartmontools** package and run tests on the drive.

---

### Post by gdi2k on 2008-01-26
Thanks dcstar. I downloaded the package and ran both a short and a long test. The results look fine: 
```
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%       193         -
# 2  Short offline       Completed without error       00%       191         -

```

I'm going to do some more digging around with those tools to see if I can come up with anything. Are there any specific tests that you could recommend?

---

### Post by gna on 2008-05-28
Same problem here with (K)Ubuntu 7.10, a Sata SiL 3512, and 2 WD 500GB SATAII drives. They are in Soft Raid 1, and the raid always rebuilds.

Did you found out what causes this?

---

### Post by gdi2k on 2008-05-28
No I didn't, but it stopped happening somewhere between a house move and me fiddling with the innards of the machine. I suspect it might have been a loose cable connection - it's tough to find decent SATA cables that don't slip off the mainboard connectors these days! 

Check your SATA cables...sorry I can't be of more help.

---

