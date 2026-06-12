---
title: "Help with Error - Sys Log"
date: 2019-09-21
forum: General Help
---

### Post by Quarkrad on 2019-09-21
I'm getting 'System Program Problem Detected' pop up at each boot again.  I've cleared the log files, rebooted, and been through a fresh sys log but cannot see what the problem is (well, maybe something but I'm not sure what it means).  If somebody could have a look and see if anything is obviously wrong I would be very grateful.

[https://paste.ubuntu.com/p/P8tVhsbgjN/](https://paste.ubuntu.com/p/P8tVhsbgjN/)

Something I came across is (but I'm not sure if this is a problem):

```
Sep 21 07:54:56 dadubuntu kernel: [    2.994255] ACPI Warning: SystemIO range 0x0000000000001828-0x000000000000182F conflicts with OpRegion 0x0000000000001800-0x000000000000187F (\PMIO) (20170831/utaddress-247)
Sep 21 07:54:56 dadubuntu kernel: [    2.994259] ACPI Warning: SystemIO range 0x0000000000001828-0x000000000000182F conflicts with OpRegion 0x0000000000001800-0x000000000000187F (\PMIO) (20170831/utaddress-247)
Sep 21 07:54:56 dadubuntu kernel: [    2.994262] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Sep 21 07:54:56 dadubuntu kernel: [    2.994264] ACPI Warning: SystemIO range 0x0000000000001C40-0x0000000000001C4F conflicts with OpRegion 0x0000000000001C00-0x0000000000001FFF (\GPR) (20170831/utaddress-247)
Sep 21 07:54:56 dadubuntu kernel: [    2.994267] ACPI Warning: SystemIO range 0x0000000000001C40-0x0000000000001C4F conflicts with OpRegion 0x0000000000001C00-0x0000000000001FFF (\GPR) (20170831/utaddress-247)
Sep 21 07:54:56 dadubuntu kernel: [    2.994269] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Sep 21 07:54:56 dadubuntu kernel: [    2.994270] ACPI Warning: SystemIO range 0x0000000000001C30-0x0000000000001C3F conflicts with OpRegion 0x0000000000001C00-0x0000000000001C3F (\GPRL) (20170831/utaddress-247)
Sep 21 07:54:56 dadubuntu kernel: [    2.994272] ACPI Warning: SystemIO range 0x0000000000001C30-0x0000000000001C3F conflicts with OpRegion 0x0000000000001C00-0x0000000000001C3F (\GPRL) (20170831/utaddress-247)
Sep 21 07:54:56 dadubuntu kernel: [    2.994274] ACPI Warning: SystemIO range 0x0000000000001C30-0x0000000000001C3F conflicts with OpRegion 0x0000000000001C00-0x0000000000001FFF (\GPR) (20170831/utaddress-247)
Sep 21 07:54:56 dadubuntu kernel: [    2.994276] ACPI Warning: SystemIO range 0x0000000000001C30-0x0000000000001C3F conflicts with OpRegion 0x0000000000001C00-0x0000000000001FFF (\GPR) (20170831/utaddress-247)
Sep 21 07:54:56 dadubuntu kernel: [    2.994278] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Sep 21 07:54:56 dadubuntu kernel: [    2.994278] ACPI Warning: SystemIO range 0x0000000000001C00-0x0000000000001C2F conflicts with OpRegion 0x0000000000001C00-0x0000000000001C3F (\GPRL) (20170831/utaddress-247)
Sep 21 07:54:56 dadubuntu kernel: [    2.994280] ACPI Warning: SystemIO range 0x0000000000001C00-0x0000000000001C2F conflicts with OpRegion 0x0000000000001C00-0x0000000000001C3F (\GPRL) (20170831/utaddress-247)
Sep 21 07:54:56 dadubuntu kernel: [    2.994282] ACPI Warning: SystemIO range 0x0000000000001C00-0x0000000000001C2F conflicts with OpRegion 0x0000000000001C00-0x0000000000001FFF (\GPR) (20170831/utaddress-247)
Sep 21 07:54:56 dadubuntu kernel: [    2.994284] ACPI Warning: SystemIO range 0x0000000000001C00-0x0000000000001C2F conflicts with OpRegion 0x0000000000001C00-0x0000000000001FFF (\GPR) (20170831/utaddress-247)
Sep 21 07:54:56 dadubuntu kernel: [    2.994286] ACPI: If an ACPI driver is av
```

---

### Post by Quarkrad on 2019-09-21
Hmm.... there was a crash file in /var/crash that I couldn't make sense of.  I deleted it and no pop-up.  So sys log and this crash file might be related - I don't know.  I will monitor the crash folder each log on and report back here to see if it has any relevance to a real or whatever potential issue/fault.

---

### Post by guiverc on 2019-09-21
When you get a "[COLOR=#000000]*System Program Problem Detected*", the /var/crash/[_program-that-crashed.crash is what gets uploaded.  The name, including date/time stamp are huge clue as to what program/library had the crash.  The message you were seeing would have been asking you to report the crash (where it gets changed to [_prog-crashed.crash.uploaded] and later removed).

The top of the crash file isn't that difficult to understand (if you've good IT experience anyway) but it becomes a hexdump usually towards the bottom, so the filename & date/time are the easiest to understand.[/COLOR]

---

