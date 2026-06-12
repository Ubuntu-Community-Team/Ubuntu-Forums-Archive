---
title: "message when boots up &quot;terminate ...&quot;"
date: 2014-12-10
forum: General Help
---

### Post by kccv42 on 2014-12-10
I get this weid message when i boot up ubuntu. It says something like "terminated...". I only shows the message for a second or two. I would like to know what the message is?

---

### Post by oldfred on 2014-12-10
Where in boot process.
If before grub menu then it may be BIOS/UEFI.
If part of Ubuntu loading it may be in the log file. Long file but you only need to look for errors or long times between the timestamps.
       sudo nano /var/log/dmesg

---

### Post by kccv42 on 2014-12-10
GNU nano 2.2.6            File: /var/log/dmesg                                

Here is what i got.


[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-40-generic (buildd@comet) (gcc version 4.8.$
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-40-generic root=UU$
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000006e455fff] usable
[    0.000000] BIOS-e820: [mem 0x000000006e456000-0x000000006e655fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000006e656000-0x000000006fd3efff] usable
[    0.000000] BIOS-e820: [mem 0x000000006fd3f000-0x000000006fdbefff] reserved
[    0.000000] BIOS-e820: [mem 0x000000006fdbf000-0x000000006febefff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000006febf000-0x000000006fef5fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000006fef6000-0x000000006fefffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec10000-0x00000000fec10fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffe00000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.6 present.
[    0.000000] DMI: Hewlett-Packard Presario CQ56 Notebook PC/1604, BIOS F.00 0$
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved

---

### Post by oldfred on 2014-12-10
All those are time stamped 0, or very beginning and show no errors.
I think you are just looking at page 1, page down until you see error message if any, or end of file.

---

### Post by kccv42 on 2014-12-11
Would this be something?

4.787439] ACPI Warning: 0x0000000000000b00-0x0000000000000b07 SystemIO con$

---

### Post by oldfred on 2014-12-11
What brand/model computer and what video card?

That is just a warning, are there any setting with long spaces between time stamps? Or outright errors.

Does it boot in spite of message on screen or just then black screen? 
Black screen is usually video issues.

[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by kccv42 on 2014-12-11
Presario CQ56. Video Card is and AMD Radeon HD mobility. Not sure exactly what graphic card it is.

---

### Post by oldfred on 2014-12-11
I do not know AMD, but they did stop supporting older video cards with current driver. You probably have to install a legacy driver.

       This repository provides AMD Catalyst drivers for legacy graphics Radeon HD 2xxx - 4xxx for several versions of Ubuntu.
[https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)

---

### Post by kccv42 on 2014-12-12
I never really had a problem with the graphic card because ubuntu installed my graghic driver by defult.

---

