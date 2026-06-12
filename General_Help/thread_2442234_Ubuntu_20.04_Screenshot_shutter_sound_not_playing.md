---
title: "Ubuntu 20.04: Screenshot shutter sound not playing"
date: 2020-05-01
forum: General Help
---

### Post by f00bar3 on 2020-05-01
```

uname -a
Linux n552vw 5.4.0-28-generic #32-Ubuntu SMP Wed Apr 22 17:40:10 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

```

Latest boot journal:

```

journalctl -b 0 -p 0..3
-- Logs begin at Wed 2020-04-29 18:57:09 EEST, end at Fri 2020-05-01 14:24:19 EEST. --
May 01 10:02:23 n552vw kernel: Initramfs unpacking failed: Decoding failed
May 01 10:02:23 n552vw kernel: tpm_crb MSFT0101:00: [Firmware Bug]: ACPI region does not cover the entire command/response buffer. [mem 0xfed40000-0xfed4087f flags 0x200] vs fed40080 f80
May 01 10:02:23 n552vw kernel: tpm_crb MSFT0101:00: [Firmware Bug]: ACPI region does not cover the entire command/response buffer. [mem 0xfed40000-0xfed4087f flags 0x200] vs fed40080 f80
May 01 10:02:23 n552vw kernel: pcieport 0000:00:1c.4: AER: PCIe Bus Error: severity=Corrected, type=Data Link Layer, (Transmitter ID)
May 01 10:02:23 n552vw kernel: pcieport 0000:00:1c.4: AER:   device [8086:a114] error status/mask=00000100/00002000
May 01 10:02:23 n552vw kernel: pcieport 0000:00:1c.4: AER:    [ 8] Rollover              
May 01 10:02:23 n552vw kernel: Bluetooth: hci0: unexpected event for opcode 0xfc2f
May 01 10:02:24 n552vw systemd[1]: Failed to start VirtualBox Web Service.
May 01 10:02:24 n552vw bluetoothd[1129]: Failed to set mode: Blocked through rfkill (0x12)
May 01 10:02:25 n552vw rtkit-daemon[1514]: Failed to make ourselves RT: Operation not permitted

```

- Can hear system sounds.
- Can hear music/videos (e.g. YouTube).

When taking screenshots (e.g. Ctrl+Shift+P) - the screenshot is taken, but no shutter sound is heard.

---

