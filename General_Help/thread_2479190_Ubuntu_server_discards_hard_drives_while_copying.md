---
title: "Ubuntu server discards hard drives while copying"
date: 2022-09-17
forum: General Help
---

### Post by xeno0402 on 2022-09-17
Hi!
I have a Raspberry pi4, with an ubuntu server, 2 HDDs in an external USB dock. When copying large files, it drops the hard drives and only restarts after a complete shutdown. What could this be? I can't make a backup. What could be the problem, does anyone have an idea?
I tried using rsync to create a tar-cpz from a larger folder, but both HDDs in the external HDD dock definitely drop it.
If necessary, I am happy to provide a log file. Please someone help me.


syslog: grep "smartd" log:


> Sep 17 10:39:31 ubuntu smartd[808]: Device: /dev/sdb [SAT], SMART usage attribute: 194 Temperature_Celsius changed from 142 139Sep 57:10:50 25 ubuntu smartd [809]: smartd 7.1 2019-12-30 r5022 [aarch64-linux-5.4.0-1069-raspi] (local build)
Sep 17 10:50:25 ubuntu smartd[809]: Copyright (C) 2002-19, Bruce Allen, Christian Franke, [www.smartmontools.org]("http://www.smartmontools.org")
Sep 17 10:50:25 ubuntu smartd[809]: Opened configuration file /etc /smartd.conf
Sep 17 10:50:25 ubuntu smartd[809]: Driver: DEVICESCAN, directive '-a' in line 21 of /etc/smartd.conf,
Sep 17 10:50:25 ubuntu smartd[809] : /etc/smartd.conf config file parsed, found DEVICESCAN, scanning for devices
ubuntu smartd[809]: Device: /dev/sda [SAT], opened
Sep 17 10:50:25 ubuntu smartd [809]: Device: /dev/sda [SAT], SAMSUNG HD502HJ, S/N:S20BJDWSA07725, WWN:5-0024e9-00235a826, FW:1AJ100E4, 500GB,
September 17 10:50 : 8 smart Device: /dev/sda [SAT], located in smartd database: SAMSUNG SpinPoint F3
Sep 17 10:50:25 ubuntu smartd[809]: Device: /dev/sda [SAT], unable to check SMART status
Sep 17 10:50:26 ubuntu smartd[809]: Device: /dev/sda [ SAT], no ATA CHECK POWER STATUS support, ignoring -n directive
Sep 17 10:50:26 ubuntu smartd[809]: Device: /dev/sda [SAT], SMART capable. Add to "monitor" list.
Sep 17 10:50:26 ubuntu smartd[809]: Device: /dev/sda [SAT], reading state from /var/lib/smartmontools/smartd.SAMSUNG_HD502HJ-S20BJDWSA07725.ata.state
Sep 17: ubun 26:ubuntu smartd[809]: Device: /dev/sdb [SAT], opened:
Sep 17 10:50:26 ubuntu smartd[809]: Device: /dev/sdb [SAT], TOSHIBA HDWD130, S/N:78DW656AS, WWN: 5-000039-fe6e88c2e, FW:MX6OACF0, 3.00 TB
Sep 17 10:50:26 ubuntu smartd[809]: Device: /dev/sdb [SAT], located in smartd database: Toshiba P300
Sep 17 10:50:26 ubuntu smartd[809]: Device: /dev/sdb [ SAT], unable to SMART
for condition check Sept. 17. 10:50:27 ubuntu smartd[809]: Device: /dev/sdb [SAT], no ATA CHECK POWER STATUS support, ignoring -n directive,
Sep 17 10:50:27 ubuntu smartd[809]: Device: /dev/sdb [SAT], SMART enabled. Add to "monitor" list.
Sep 17 10:50:27 ubuntu smartd[809]: Device: /dev/sdb [SAT], reading state from /var/lib/smartmontools/smartd.TOSHIBA_HDWD130-78DW656AS.ata.state
Sep 17 10:50:27 smartd[809]: Monitoring 2 ATA/SATA, 0 SCSI/SAS and 0 NVMe devices
Sep 17 10:50:27 ubuntu smartd[809]: Device: /dev/sda [SAT], SMART pre-failure attribute: 3 Spin_Up_Time changed from 86 to 84
Sep 17 10:50:27 ubuntu smartd[809]: Device: /dev/sda [SAT], SMART usage attribute: 194 Temperature_Celsius changed from 61 to 60
Sep 17 10:50:28 ubuntu smartd[809]: Device: /dev/sdb [SAT], SMART pre-failure attribute: 3 Spin_2 from Up1_2 Spin_9 changed 143.
Sep 17 10:50:28 ubuntu smartd[809]: Device: /dev/sda [SAT], state is /var/lib/smartmontools/smartd.SAMSUNG_HD502HJ-S20BJDWSA07725.ata.state
10:507. 28 ubuntu smartd[809]: Device: /dev/sdb [SAT], state written to /var/lib/smartmontools/smartd.TOSHIBA_HDWD130-78DW656AS.ata.state










---

### Post by TheFu on 2022-09-17
USB connections are flaky and should be avoided whenever possible.  Also the SAT driver says the USB controller is one of the less-great controllers.  Typically, this is part of the external USB hardware, not the disk.

Always prefer connectors with screws and clips to hold it in place correctly - SCSI, SATA, eSATA. Avoid USB.

Have your run smartctl to perform a long test of the drive?  Seems that would be step 1.  I'd be concerned with so many SMART errors for that Samsung device.  Not good.

---

### Post by HermanAB on 2022-09-17
Sounds like an inadequate PSU.

---

