---
title: "Ubuntu freezes regulary"
date: 2008-01-02
forum: General Help
---

### Post by serrghi on 2008-01-02
My Ubuntu 7.10 freezes regulary for 3-10sec on a regular basis.
My current setup is a Asus A6Ja laptop.

Anyway, i checked my syslog and this came up over and over again, including the times the system froze.

```
Jan  2 22:53:14 serrghi-laptop kernel: [19300.872000] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Jan  2 22:53:25 serrghi-laptop kernel: [19300.872000] ata1.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x25 data 8 in
Jan  2 22:53:25 serrghi-laptop kernel: [19300.872000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
Jan  2 22:53:25 serrghi-laptop kernel: [19305.912000] ata1: port is slow to respond, please be patient (Status 0xd0)
Jan  2 22:53:25 serrghi-laptop kernel: [19310.896000] ata1: device not ready (errno=-16), forcing hardreset
Jan  2 22:53:25 serrghi-laptop kernel: [19310.896000] ata1: soft resetting port
Jan  2 22:53:25 serrghi-laptop kernel: [19311.264000] ata1.00: configured for UDMA/100
Jan  2 22:53:25 serrghi-laptop kernel: [19311.452000] ata1.01: configured for UDMA/25
Jan  2 22:53:25 serrghi-laptop kernel: [19311.452000] ata1: EH complete
Jan  2 22:53:25 serrghi-laptop kernel: [19311.468000] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
Jan  2 22:53:25 serrghi-laptop kernel: [19311.484000] sd 0:0:0:0: [sda] Write Protect is off
Jan  2 22:53:25 serrghi-laptop kernel: [19311.484000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jan  2 22:53:25 serrghi-laptop kernel: [19311.508000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan  2 22:53:25 serrghi-laptop kernel: [19311.540000] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
Jan  2 22:53:25 serrghi-laptop kernel: [19311.556000] sd 0:0:0:0: [sda] Write Protect is off
Jan  2 22:53:25 serrghi-laptop kernel: [19311.556000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jan  2 22:53:25 serrghi-laptop kernel: [19311.588000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
```

Im kinda a noob with linux, so i have absolutely no idea what to do :(
Anyone encountered this before?:confused:

---

