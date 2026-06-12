---
title: "ACPI Error: No pointer back to namespace node in package"
date: 2019-12-06
forum: General Help
---

### Post by Arcken on 2019-12-06
Hello guys , I got a Dell Inspiron 3000 and it came with Ubuntu 18.04. I installed the 19.10 on it and after running the journalctl command i saw these errors:
```

kernel: ACPI Error: No pointer back to namespace node in package 000000000c1198b2 (20190703/dsargs-301)
kernel: ACPI Error: No pointer back to namespace node in package 00000000e9d37f71 (20190703/dsargs-301)
kernel: ACPI Error: No pointer back to namespace node in package 0000000027bb1834 (20190703/dsargs-301)
kernel: ACPI Error: No pointer back to namespace node in package 000000000c1198b2 (20190703/dsargs-301)
kernel: ACPI Error: No pointer back to namespace node in package 00000000e9d37f71 (20190703/dsargs-301)
kernel: ACPI Error: No pointer back to namespace node in package 0000000027bb1834 (20190703/dsargs-301)
kernel: ACPI Error: No pointer back to namespace node in package 000000000c1198b2 (20190703/dsargs-301)
kernel: ACPI Error: No pointer back to namespace node in package 00000000e9d37f71 (20190703/dsargs-301)
kernel: ACPI Error: No pointer back to namespace node in package 0000000027bb1834 (20190703/dsargs-301)
kernel: ACPI Error: No pointer back to namespace node in package 000000000c1198b2 (20190703/dsargs-301)
kernel: ACPI Error: No pointer back to namespace node in package 00000000e9d37f71 (20190703/dsargs-301)
kernel: ACPI Error: No pointer back to namespace node in package 0000000027bb1834 (20190703/dsargs-301)
kernel: ACPI Error: No pointer back to namespace node in package 000000000c1198b2 (20190703/dsargs-301)
kernel: ACPI Error: No pointer back to namespace node in package 00000000e9d37f71 (20190703/dsargs-301)
kernel: ACPI Error: No pointer back to namespace node in package 0000000027bb1834 (20190703/dsargs-301)
kernel: ACPI Error: No pointer back to namespace node in package 000000000c1198b2 (20190703/dsargs-301)
kernel: ACPI Error: No pointer back to namespace node in package 00000000e9d37f71 (20190703/dsargs-301)
kernel: ACPI Error: No pointer back to namespace node in package 0000000027bb1834 (20190703/dsargs-301)
kernel: ACPI Error: No pointer back to namespace node in package 000000000c1198b2 (20190703/dsargs-301)
kernel: ACPI Error: No pointer back to namespace node in package 00000000e9d37f71 (20190703/dsargs-301)
kernel: ACPI Error: No pointer back to namespace node in package 0000000027bb1834 (20190703/dsargs-301)
kernel: ACPI Error: No pointer back to namespace node in package 000000000c1198b2 (20190703/dsargs-301)
kernel: ACPI Error: No pointer back to namespace node in package 00000000e9d37f71 (20190703/dsargs-301)
kernel: ACPI Error: No pointer back to namespace node in package 0000000027bb1834 (20190703/dsargs-301)
kernel: psmouse serio1: elantech: elantech_send_cmd query 0x02 failed.
kernel: psmouse serio1: elantech: failed to query capabilities.
kernel: ACPI Error: No pointer back to namespace node in package 000000000c1198b2 (20190703/dsargs-301)
kernel: ACPI Error: Aborting method \_SB.PCI0.B0D4.PPCC due to previous error (AE_AML_INTERNAL) (20190703/pspars
bluetoothd[882]: Failed to set mode: Blocked through rfkill (0x12)
bluetoothd[882]: Failed to set mode: Blocked through rfkill (0x12)
gdm-password][1426]: gkr-pam: unable to locate daemon control file
bluetoothd[882]: Failed to set mode: Blocked through rfkill (0x12)

```

I can boot normally and haven't noticed any problems. 

Ty for you help

---

