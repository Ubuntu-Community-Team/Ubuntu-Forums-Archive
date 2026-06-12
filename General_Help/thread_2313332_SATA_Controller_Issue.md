---
title: "SATA Controller Issue"
date: 2016-02-11
forum: General Help
---

### Post by bumperjeep on 2016-02-11
Hello - Could use some help with this syslogd error. My disks are working fine - I'm not sure what that's about. Any suggestions? 

Thanks

```
Feb 11 13:40:06 tv kernel: [4386831.237055] ata11.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Feb 11 13:40:06 tv kernel: [4386831.237156] ata11.00: failed command: IDENTIFY DEVICE
Feb 11 13:40:06 tv kernel: [4386831.237215] ata11.00: cmd ec/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
Feb 11 13:40:06 tv kernel: [4386831.237215]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
Feb 11 13:40:06 tv kernel: [4386831.237405] ata11.00: status: { DRDY }
Feb 11 13:40:06 tv kernel: [4386831.237457] ata11: hard resetting link
Feb 11 13:40:07 tv kernel: [4386831.728599] ata11: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Feb 11 13:40:07 tv kernel: [4386831.730054] ata11.00: configured for UDMA/33
Feb 11 13:40:07 tv kernel: [4386831.730085] ata11: EH complete
Feb 11 14:00:11 tv kernel: [4388035.165187] ata10.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Feb 11 14:00:11 tv kernel: [4388035.165288] ata10.00: failed command: IDENTIFY DEVICE
Feb 11 14:00:11 tv kernel: [4388035.165347] ata10.00: cmd ec/00:01:00:00:00/00:00:00:00:00/00 tag 24 pio 512 in
Feb 11 14:00:11 tv kernel: [4388035.165347]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
Feb 11 14:00:11 tv kernel: [4388035.165537] ata10.00: status: { DRDY }
Feb 11 14:00:11 tv kernel: [4388035.165588] ata10: hard resetting link
Feb 11 14:00:12 tv kernel: [4388035.656712] ata10: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Feb 11 14:00:12 tv kernel: [4388035.668691] ata10.00: configured for UDMA/133
Feb 11 14:00:12 tv kernel: [4388035.668747] ata10: EH complete
Feb  1 00:42:11 tv pulseaudio[23897]: [pulseaudio] main.c: User-configured server at localhost:30002, refusing to start/autospawn.
```

---

### Post by bumperjeep on 2016-02-16
Does anybody have any suggestions?

---

