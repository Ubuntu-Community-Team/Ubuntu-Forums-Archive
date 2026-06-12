---
title: "Ubuntu 12.04, cannot restart degraded RAID 6"
date: 2014-03-07
forum: General Help
---

### Post by MarcusL on 2014-03-07
UPDATE:
I still do not know why the drive died, as these are only 9 months old. I run 
```
mdadm --stop /dev/md0 
```
and this released the drives, I then re run 
**```
sudo mdadm --assemble --scan --verbose
```**
and the array started in degraded mode... phew! 

I now need to replace the drive and it will all be back to normal I guess. The funny thing is I run an update last night on the server (10 items were updated from memory) so I wonder whether this caused the failure? The HDD is screwed terminally though as it will reboot any of my other machines when I tried installing it on them.

Any ideas on where to find info on the drive death would be appreciated.

Thanks!
Marc


*********************************************************************************************************************
Hi all,
My Ubuntu x64 12.04 server suffered a severe issue today and I have not been able to restart it since this morning. I have had this set up for over a year now with no problems. Essentially the sever is a:
Core2Quad processor (8 years old)
ASUS Mobo P5K (6x SATA ports)
Adaptec SATA card (2x ports)
10x WD Caviar Black 4TB drives, RAID 6
8GB RAM

The server acts as a back up as well as a media center for my kid's cartoons. They were watching a movie when it froze and upon checking the server screen a flurry of hardware errors was racing through pointing to device /dev/sdh. I had to power cycle it to stop it as no key stroke was doing anything. Upon restart the machine beeps once but it stops. I removed the offending HDD and tried it on other machines and it has the same effect. It is really screwed and not even WD drive testing tool sees it.

Now when I boot the server is lands me at an "initramfs" prompt asking if I want to start the degraded array. When I hit YES it lands me back at the prompt and lists messages to say it failed to start the array due to input/output error.

I exit this and enter the ubuntu console where I log in but no matter what I have tried the array will not start. I appreciate any help you can provide.

Here's some more info:

The command ** sudo mdadm --assemble --run --force /dev/md0 /dev/sd[bcdefghij]1** returns:```

mdadm: /dev/sdb1 is busy - skipping
mdadm: /dev/sdc1 is busy - skipping
mdadm: /dev/sdd1 is busy - skipping
mdadm: /dev/sde1 is busy - skipping
mdadm: /dev/sdf1 is busy - skipping
mdadm: /dev/sdg1 is busy - skipping
mdadm: /dev/sdh1 is busy - skipping
mdadm: /dev/sdi1 is busy - skipping
mdadm: /dev/sdj1 is busy - skipping

```

The command [COLOR=#000000]**sudo mdadm --assemble --scan --verbose** returns[/COLOR]```

mdadm: looking for devices for /dev/md/0
mdadm: /dev/sdj1 is busy - skipping
mdadm: no RAID superblock on /dev/sdj
mdadm: /dev/sdi1 is busy - skipping
mdadm: no RAID superblock on /dev/sdi
mdadm: /dev/sdh1 is busy - skipping
mdadm: no RAID superblock on /dev/sdh
mdadm: /dev/sdg1 is busy - skipping
mdadm: no RAID superblock on /dev/sdg
mdadm: /dev/sde1 is busy - skipping
mdadm: no RAID superblock on /dev/sde
mdadm: /dev/sdd1 is busy - skipping
mdadm: no RAID superblock on /dev/sdd
mdadm: /dev/sdf1 is busy - skipping
mdadm: no RAID superblock on /dev/sdf
mdadm: /dev/sdc1 is busy - skipping
mdadm: no RAID superblock on /dev/sdc
mdadm: /dev/sdb1 is busy - skipping
mdadm: no RAID superblock on /dev/sdb
mdadm: no RAID superblock on /dev/sda7
mdadm: no RAID superblock on /dev/sda6
mdadm: no RAID superblock on /dev/sda5
mdadm: no RAID superblock on /dev/sda2
mdadm: no RAID superblock on /dev/sda1
mdadm: no RAID superblock on /dev/sda

```

```
**sudo smartctl -d ata -H /dev/sdb**
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.5.0-47-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


**tm@LSERVER:~$ sudo smartctl -d ata -H /dev/sdc**
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.5.0-47-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


Smartctl: Device Read Identity Failed: Inappropriate ioctl for device


A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.


**tm@LSERVER:~$ sudo smartctl -d ata -H /dev/sdd**
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.5.0-47-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


Smartctl: Device Read Identity Failed: Inappropriate ioctl for device


A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.

**tm@LSERVER:~$ sudo smartctl -d ata -H /dev/sde**
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.5.0-47-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


Smartctl: Device Read Identity Failed: Inappropriate ioctl for device


A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.


**tm@LSERVER:~$ sudo smartctl -d ata -H /dev/sdf**
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.5.0-47-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


Smartctl: Device Read Identity Failed: Inappropriate ioctl for device


A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.


**tm@LSERVER:~$ sudo smartctl -d ata -H /dev/sdg**
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.5.0-47-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


**tm@LSERVER:~$ sudo smartctl -d ata -H /dev/sdh**
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.5.0-47-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


**tm@LSERVER:~$ sudo smartctl -d ata -H /dev/sdi**
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.5.0-47-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


**tm@LSERVER:~$ sudo smartctl -d ata -H /dev/sdj**
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.5.0-47-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

```


The command **sudo fidk -l** returns
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c06e6


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     1953791      975872   83  Linux
/dev/sda2         1955838   976771071   487407617    5  Extended
/dev/sda5         1955840    33204223    15624192   82  Linux swap / Solaris
/dev/sda6        33206272   228515839    97654784   83  Linux
/dev/sda7       228517888   976771071   374126592   83  Linux


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sdb: 4000.8 GB, 4000787030016 bytes
255 heads, 63 sectors/track, 486401 cylinders, total 7814037168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT


WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sdc: 3999.7 GB, 3999677808640 bytes
255 heads, 63 sectors/track, 486266 cylinders, total 7811870720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  4294967295  2147483647+  ee  GPT


WARNING: GPT (GUID Partition Table) detected on '/dev/sdf'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sdf: 3999.7 GB, 3999677808640 bytes
255 heads, 63 sectors/track, 486266 cylinders, total 7811870720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1  4294967295  2147483647+  ee  GPT


WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sdd: 3999.7 GB, 3999677808640 bytes
255 heads, 63 sectors/track, 486266 cylinders, total 7811870720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1  4294967295  2147483647+  ee  GPT


WARNING: GPT (GUID Partition Table) detected on '/dev/sde'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sde: 3999.7 GB, 3999677808640 bytes
255 heads, 63 sectors/track, 486266 cylinders, total 7811870720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1  4294967295  2147483647+  ee  GPT


WARNING: GPT (GUID Partition Table) detected on '/dev/sdg'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sdg: 4000.8 GB, 4000787030016 bytes
255 heads, 63 sectors/track, 486401 cylinders, total 7814037168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1  4294967295  2147483647+  ee  GPT


WARNING: GPT (GUID Partition Table) detected on '/dev/sdh'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sdh: 4000.8 GB, 4000787030016 bytes
255 heads, 63 sectors/track, 486401 cylinders, total 7814037168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1  4294967295  2147483647+  ee  GPT


WARNING: GPT (GUID Partition Table) detected on '/dev/sdi'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sdi: 4000.8 GB, 4000787030016 bytes
255 heads, 63 sectors/track, 486401 cylinders, total 7814037168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1               1  4294967295  2147483647+  ee  GPT


WARNING: GPT (GUID Partition Table) detected on '/dev/sdj'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sdj: 4000.8 GB, 4000787030016 bytes
255 heads, 63 sectors/track, 486401 cylinders, total 7814037168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1               1  4294967295  2147483647+  ee  GPT

```

The command **grep -i fail /var/log/syslog** shows:
```



Feb 24 17:22:32 LSERVER kernel: [    0.168610]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Feb 25 17:32:48 LSERVER kernel: [    0.172608]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Feb 26 15:39:34 LSERVER kernel: [    0.168610]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Feb 27 08:14:39 LSERVER kernel: [    0.172605]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Feb 28 00:40:47 LSERVER kernel: [    0.172606]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Feb 28 08:50:52 LSERVER kernel: [    0.168610]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Mar  1 08:28:59 LSERVER kernel: [    0.173313]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Mar  1 20:40:44 LSERVER kernel: [    0.168612]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Mar  2 11:48:55 LSERVER kernel: [    0.172612]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Mar  3 21:38:56 LSERVER kernel: [    0.172614]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Mar  4 13:01:56 LSERVER kernel: [    0.168611]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Mar  4 18:50:17 LSERVER udevd[12276]: symlink '../../sdi' '/dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0.udev-tmp' failed: File exists
Mar  5 09:03:28 LSERVER kernel: [    0.172612]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Mar  5 15:16:14 LSERVER kernel: [22382.623595] <unknown>: hw csum failure
Mar  5 15:16:14 LSERVER kernel: [22382.623706] <unknown>: hw csum failure
Mar  5 15:17:23 LSERVER kernel: [22450.940367] eth0: hw csum failure
Mar  5 15:17:23 LSERVER kernel: [22450.940507] eth0: hw csum failure
Mar  5 15:17:23 LSERVER kernel: [22450.940583] eth0: hw csum failure
Mar  5 15:19:09 LSERVER kernel: [    0.168610]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Mar  6 09:53:50 LSERVER kernel: [    0.172610]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Mar  7 09:38:23 LSERVER kernel: [    0.172612]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Mar  8 07:41:39 LSERVER kernel: [    0.172609]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Mar  8 08:39:03 LSERVER kernel: [ 3459.808075] ata6.00: failed command: READ FPDMA QUEUED
Mar  8 08:39:03 LSERVER kernel: [ 3459.808194] ata6.00: failed command: READ FPDMA QUEUED
Mar  8 08:39:03 LSERVER kernel: [ 3459.808310] ata6.00: failed command: READ FPDMA QUEUED
Mar  8 08:39:03 LSERVER kernel: [ 3459.808425] ata6.00: failed command: READ FPDMA QUEUED
Mar  8 08:39:17 LSERVER kernel: [ 3473.140024] ata6.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Mar  8 08:39:17 LSERVER kernel: [ 3473.140027] ata6.00: revalidation failed (errno=-5)
Mar  8 08:39:32 LSERVER kernel: [ 3488.424587] ata6.00: failed command: READ FPDMA QUEUED
Mar  8 08:39:41 LSERVER kernel: [ 3497.438459] ata6.00: failed command: READ FPDMA QUEUED
Mar  8 08:39:46 LSERVER kernel: [ 3501.962911] ata6.00: failed command: READ FPDMA QUEUED
Mar  8 08:39:46 LSERVER kernel: [ 3502.480140] ata6.00: failed command: READ DMA EXT
Mar  8 08:39:50 LSERVER kernel: [ 3506.570337] ata6.00: failed command: READ DMA EXT
Mar  8 08:39:55 LSERVER kernel: [ 3511.801657] ata6.00: failed command: READ DMA EXT
Mar  8 08:39:59 LSERVER kernel: [ 3515.927202] ata6.00: failed command: READ DMA EXT
Mar  8 08:40:04 LSERVER kernel: [ 3520.655809] ata6.00: failed command: READ DMA EXT
Mar  8 08:40:09 LSERVER kernel: [ 3525.355456] ata6.00: failed command: READ DMA EXT
Mar  8 08:40:14 LSERVER kernel: [ 3530.122196] ata6.00: failed command: READ DMA EXT
Mar  8 08:40:18 LSERVER kernel: [ 3534.874866] ata6.00: failed command: READ DMA EXT
Mar  8 08:40:23 LSERVER kernel: [ 3539.593613] ata6.00: failed command: READ DMA EXT
Mar  8 12:50:02 LSERVER kernel: [    0.172588]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Mar  8 12:50:02 LSERVER kernel: [    7.840067] md/raid:md0: failed to run raid set.
Mar  8 12:50:02 LSERVER kernel: [    7.840097] md: pers->run() failed ...
Mar  8 13:07:16 LSERVER kernel: [    0.172595]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Mar  8 13:07:16 LSERVER kernel: [    7.703911] md/raid:md0: failed to run raid set.
Mar  8 13:07:16 LSERVER kernel: [    7.703940] md: pers->run() failed ...
Mar  8 13:30:45 LSERVER kernel: [    0.172592]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Mar  8 13:30:45 LSERVER kernel: [    6.583767] md/raid:md0: failed to run raid set.
Mar  8 13:30:45 LSERVER kernel: [    6.583796] md: pers->run() failed ...
Mar  8 14:07:09 LSERVER kernel: [    0.176592]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Mar  8 14:28:53 LSERVER kernel: [    0.176598]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Mar  8 14:28:53 LSERVER kernel: [    7.532003] md/raid:md0: failed to run raid set.
Mar  8 14:28:53 LSERVER kernel: [    7.532047] md: pers->run() failed ...
Mar  8 15:07:02 LSERVER kernel: [    0.176591]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Mar  8 15:07:02 LSERVER kernel: [    7.523943] md/raid:md0: failed to run raid set.
Mar  8 15:07:02 LSERVER kernel: [    7.523972] md: pers->run() failed ...



```

The command **dmesg** shows:
```
[    0.856037] ata9: SATA link down (SStatus 0 SControl 300)
[    0.856100] ata10: SATA link down (SStatus 0 SControl 300)
[    0.920022] usb 7-2: new low-speed USB device number 2 using uhci_hcd
[    1.016022] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.017608] ata3.00: ATA-8: WDC WD4001FAEX-00MJRA0, 01.01L01, max UDMA/133
[    1.017643] ata3.00: 7814037168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    1.018582] ata3.00: configured for UDMA/133
[    1.018680] scsi 3:0:0:0: Direct-Access     ATA      WDC WD4001FAEX-0 01.0 PQ: 0 ANSI: 5
[    1.018835] sd 3:0:0:0: [sdb] 7814037168 512-byte logical blocks: (4.00 TB/3.63 TiB)
[    1.018842] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    1.018994] sd 3:0:0:0: [sdb] Write Protect is off
[    1.019028] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.019052] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.057170]  sdb: sdb1
[    1.057389] sd 3:0:0:0: [sdb] Attached SCSI disk
[    1.089562] AAC0: kernel 5.2-0[19109] Dec  6 2012
[    1.089594] AAC0: monitor 5.2-0[19109]
[    1.089623] AAC0: bios 5.2-0[19109]
[    1.089653] AAC0: serial 3A19131D77C
[    1.089682] AAC0: Non-DASD support enabled.
[    1.089711] AAC0: 64bit support enabled.
[    1.089740] AAC0: 64 Bit DAC enabled
[    1.103925] scsi0 : aacraid
[    1.117770] scsi 0:1:0:0: Direct-Access     WDC      WD4001FAEX-00MJR 01.0 PQ: 0 ANSI: 5
[    1.118245] scsi 0:1:1:0: Direct-Access     WDC      WD4001FAEX-00MJR 01.0 PQ: 0 ANSI: 5
[    1.118703] scsi 0:1:2:0: Direct-Access     WDC      WD4001FAEX-00MJR 01.0 PQ: 0 ANSI: 5
[    1.119195] scsi 0:1:3:0: Direct-Access     WDC      WD4001FAEX-00MJR 01.0 PQ: 0 ANSI: 5
[    1.176578] usb 7-2: New USB device found, idVendor=04d9, idProduct=1603
[    1.176626] usb 7-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.176663] usb 7-2: Product: USB Keyboard
[    1.176701] usb 7-2: Manufacturer:
[    1.201803] sd 0:1:0:0: Attached scsi generic sg2 type 0
[    1.202022] sd 0:1:1:0: Attached scsi generic sg3 type 0
[    1.202196] sd 0:1:2:0: Attached scsi generic sg4 type 0
[    1.202366] sd 0:1:3:0: Attached scsi generic sg5 type 0
[    1.220023] Refined TSC clocksource calibration: 3005.554 MHz.
[    1.220060] Switching to clocksource tsc
[    1.235756] sd 0:1:0:0: [sdc] 7811870720 512-byte logical blocks: (3.99 TB/3.63 TiB)
[    1.269882] sd 0:1:1:0: [sdd] 7811870720 512-byte logical blocks: (3.99 TB/3.63 TiB)
[    1.303913] sd 0:1:2:0: [sde] 7811870720 512-byte logical blocks: (3.99 TB/3.63 TiB)
[    1.337945] sd 0:1:3:0: [sdf] 7811870720 512-byte logical blocks: (3.99 TB/3.63 TiB)
[    1.339470] sd 0:1:0:0: [sdc] Write Protect is off
[    1.339501] sd 0:1:0:0: [sdc] Mode Sense: 6e 00 10 08
[    1.339900] sd 0:1:1:0: [sdd] Write Protect is off
[    1.339924] sd 0:1:2:0: [sde] Write Protect is off
[    1.339927] sd 0:1:2:0: [sde] Mode Sense: 6e 00 10 08
[    1.339949] sd 0:1:3:0: [sdf] Write Protect is off
[    1.339951] sd 0:1:3:0: [sdf] Mode Sense: 6e 00 10 08
[    1.339998] sd 0:1:1:0: [sdd] Mode Sense: 6e 00 10 08
[    1.340560] sd 0:1:0:0: [sdc] Write cache: enabled, read cache: enabled, supports DPO and FUA
[    1.341207] sd 0:1:2:0: [sde] Write cache: enabled, read cache: enabled, supports DPO and FUA
[    1.341216] sd 0:1:3:0: [sdf] Write cache: enabled, read cache: enabled, supports DPO and FUA
[    1.341243] sd 0:1:1:0: [sdd] Write cache: enabled, read cache: enabled, supports DPO and FUA
[    1.505299]  sdc: sdc1
[    1.508031] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.508961] ata4.00: ATA-8: WDC WD4001FAEX-00MJRA0, 01.01L01, max UDMA/133
[    1.509007] ata4.00: 7814037168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    1.509921] ata4.00: configured for UDMA/133
[    1.540381]  sde: sde1
[    1.540501]  sdd: sdd1
[    1.540531]  sdf: sdf1
[    1.643162] sd 0:1:0:0: [sdc] Attached SCSI removable disk
[    1.645147] sd 0:1:2:0: [sde] Attached SCSI removable disk
[    1.645183] sd 0:1:3:0: [sdf] Attached SCSI removable disk
[    1.645213] sd 0:1:1:0: [sdd] Attached SCSI removable disk
[    1.645352] scsi 4:0:0:0: Direct-Access     ATA      WDC WD4001FAEX-0 01.0 PQ: 0 ANSI: 5
[    1.645518] sd 4:0:0:0: [sdg] 7814037168 512-byte logical blocks: (4.00 TB/3.63 TiB)
[    1.645530] sd 4:0:0:0: Attached scsi generic sg6 type 0
[    1.645646] sd 4:0:0:0: [sdg] Write Protect is off
[    1.645675] sd 4:0:0:0: [sdg] Mode Sense: 00 3a 00 00
[    1.645694] sd 4:0:0:0: [sdg] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.679485]  sdg: sdg1
[    1.679733] sd 4:0:0:0: [sdg] Attached SCSI disk
[    2.136015] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.136949] ata5.00: ATA-8: WDC WD4001FAEX-00MJRA0, 01.01L01, max UDMA/133
[    2.136995] ata5.00: 7814037168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.137910] ata5.00: configured for UDMA/133
[    2.138012] scsi 5:0:0:0: Direct-Access     ATA      WDC WD4001FAEX-0 01.0 PQ: 0 ANSI: 5
[    2.138144] sd 5:0:0:0: [sdh] 7814037168 512-byte logical blocks: (4.00 TB/3.63 TiB)
[    2.138188] sd 5:0:0:0: Attached scsi generic sg7 type 0
[    2.138259] sd 5:0:0:0: [sdh] Write Protect is off
[    2.138296] sd 5:0:0:0: [sdh] Mode Sense: 00 3a 00 00
[    2.138317] sd 5:0:0:0: [sdh] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.179844]  sdh: sdh1
[    2.180113] sd 5:0:0:0: [sdh] Attached SCSI disk
[    2.456024] ata6: SATA link down (SStatus 0 SControl 300)
[    2.948024] ata7: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.948928] ata7.00: ATA-8: WDC WD4001FAEX-00MJRA0, 01.01L01, max UDMA/133
[    2.948975] ata7.00: 7814037168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.949912] ata7.00: configured for UDMA/133
[    2.950015] scsi 7:0:0:0: Direct-Access     ATA      WDC WD4001FAEX-0 01.0 PQ: 0 ANSI: 5
[    2.950142] sd 7:0:0:0: [sdi] 7814037168 512-byte logical blocks: (4.00 TB/3.63 TiB)
[    2.950159] sd 7:0:0:0: Attached scsi generic sg8 type 0
[    2.950253] sd 7:0:0:0: [sdi] Write Protect is off
[    2.950282] sd 7:0:0:0: [sdi] Mode Sense: 00 3a 00 00
[    2.950301] sd 7:0:0:0: [sdi] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.988022]  sdi: sdi1
[    2.988264] sd 7:0:0:0: [sdi] Attached SCSI disk
[    3.440014] ata8: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.441523] ata8.00: ATA-8: WDC WD4001FAEX-00MJRA0, 01.01L01, max UDMA/133
[    3.441556] ata8.00: 7814037168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    3.442477] ata8.00: configured for UDMA/133
[    3.442598] scsi 8:0:0:0: Direct-Access     ATA      WDC WD4001FAEX-0 01.0 PQ: 0 ANSI: 5
[    3.442723] sd 8:0:0:0: [sdj] 7814037168 512-byte logical blocks: (4.00 TB/3.63 TiB)
[    3.442764] sd 8:0:0:0: Attached scsi generic sg9 type 0
[    3.442839] sd 8:0:0:0: [sdj] Write Protect is off
[    3.442877] sd 8:0:0:0: [sdj] Mode Sense: 00 3a 00 00
[    3.442898] sd 8:0:0:0: [sdj] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.480453]  sdj: sdj1
[    3.480700] sd 8:0:0:0: [sdj] Attached SCSI disk
[    3.481407] xor: automatically using best checksumming function:
[    3.520006]    generic_sse: 11168.000 MB/sec
[    3.520837] md: raid6 personality registered for level 6
[    3.520867] md: raid5 personality registered for level 5
[    3.520899] md: raid4 personality registered for level 4
[    3.525194] md: raid10 personality registered for level 10
[    3.557358] md: bind<sdi1>
[    3.559220] md: bind<sdh1>
[    3.565714] md: bind<sdg1>
[    3.572024] md: bind<sdd1>
[    3.574469] md: bind<sdf1>
[    3.576837] md: bind<sdj1>
[    3.583600] md: bind<sdc1>
[    3.586848] md: bind<sdb1>
[    3.596167] md: bind<sde1>
[    3.596649] usbcore: registered new interface driver usbhid
[    3.596681] usbhid: USB HID core driver
[    3.598497] input:   USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.0/input/input2
[    3.598725] hid-generic 0003:04D9:1603.0001: input,hidraw0: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:1d.1-2/input0
[    3.618660] input:   USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.1/input/input3
[    3.618794] hid-generic 0003:04D9:1603.0002: input,hidraw1: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:1d.1-2/input1
[    7.522398] bio: create slab <bio-1> at 1
[    7.522431] md/raid:md0: not clean -- starting background reconstruction
[    7.522467] md/raid:md0: device sde1 operational as raid disk 8
[    7.522494] md/raid:md0: device sdb1 operational as raid disk 0
[    7.522522] md/raid:md0: device sdc1 operational as raid disk 6
[    7.522549] md/raid:md0: device sdj1 operational as raid disk 5
[    7.522576] md/raid:md0: device sdf1 operational as raid disk 9
[    7.522604] md/raid:md0: device sdd1 operational as raid disk 7
[    7.522631] md/raid:md0: device sdg1 operational as raid disk 2
[    7.522658] md/raid:md0: device sdh1 operational as raid disk 1
[    7.522685] md/raid:md0: device sdi1 operational as raid disk 4
[    7.523383] md/raid:md0: allocated 10672kB
[    7.523455] md/raid:md0: cannot start dirty degraded array.
[    7.523502] RAID conf printout:
[    7.523505]  --- level:6 rd:10 wd:9
[    7.523507]  disk 0, o:1, dev:sdb1
[    7.523509]  disk 1, o:1, dev:sdh1
[    7.523511]  disk 2, o:1, dev:sdg1
[    7.523513]  disk 4, o:1, dev:sdi1
[    7.523515]  disk 5, o:1, dev:sdj1
[    7.523517]  disk 6, o:1, dev:sdc1
[    7.523519]  disk 7, o:1, dev:sdd1
[    7.523521]  disk 8, o:1, dev:sde1
[    7.523523]  disk 9, o:1, dev:sdf1
[    7.523943] md/raid:md0: failed to run raid set.
[    7.523972] md: pers->run() failed ...
[  212.505079] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[  221.708840] Adding 15624188k swap on /dev/sda5.  Priority:-1 extents:1 across:15624188k
[  221.713327] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  221.713335] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[  221.744354] udevd[479]: starting version 175
[  221.829052] type=1400 audit(1394251613.891:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=551 comm="apparmor_parser"
[  221.829406] type=1400 audit(1394251613.891:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=551 comm="apparmor_parser"
[  221.829618] type=1400 audit(1394251613.891:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=551 comm="apparmor_parser"
[  221.890239] sky2 0000:02:00.0: eth0: enabling interface
[  221.891053] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  221.941542] microcode: CPU0 sig=0x6fb, pf=0x10, revision=0xb6
[  221.985191] ACPI Warning: 0x0000000000000830-0x0000000000000833 SystemIO conflicts with Region \_SB_.PCI0.SBRG.SMIE 1 (20120320/utaddress-251)
[  221.985197] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[  221.985199] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
[  222.048073] microcode: CPU1 sig=0x6fb, pf=0x10, revision=0xb6
[  222.048684] lp: driver loaded but no devices found
[  222.049698] microcode: CPU2 sig=0x6fb, pf=0x10, revision=0xb6
[  222.050841] microcode: CPU3 sig=0x6fb, pf=0x10, revision=0xb6
[  222.051884] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[  222.162158] gpio_ich: GPIO from 195 to 255 on gpio_ich
[  222.215733] [drm] Initialized drm 1.1.0 20060810
[  222.269579] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[  222.300555] coretemp coretemp.0: Using relative temperature scale!
[  222.300644] coretemp coretemp.0: Using relative temperature scale!
[  222.300658] coretemp coretemp.0: Using relative temperature scale!
[  222.300812] coretemp coretemp.0: Using relative temperature scale!
[  222.330730] [drm] radeon defaulting to kernel modesetting.
[  222.330734] [drm] radeon kernel modesetting enabled.
[  222.331039] [drm] initializing kernel modesetting (REDWOOD 0x1002:0x68D8 0x1043:0x0356).
[  222.331071] [drm] register mmio base: 0xFE1C0000
[  222.331072] [drm] register mmio size: 131072
[  222.331156] ATOM BIOS: 68D8.12.17.0.4.AS01
[  222.331178] radeon 0000:01:00.0: VRAM: 1024M 0x0000000000000000 - 0x000000003FFFFFFF (1024M used)
[  222.331180] radeon 0000:01:00.0: GTT: 512M 0x0000000040000000 - 0x000000005FFFFFFF
[  222.333648] [drm] Detected VRAM RAM=1024M, BAR=256M
[  222.333656] [drm] RAM width 128bits DDR
[  222.333751] [TTM] Zone  kernel: Available graphics memory: 4088762 kiB
[  222.333752] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[  222.333754] [TTM] Initializing pool allocator
[  222.333758] [TTM] Initializing DMA pool allocator
[  222.333786] [drm] radeon: 1024M of VRAM memory ready
[  222.333788] [drm] radeon: 512M of GTT memory ready.
[  222.333814] [drm] GART: num cpu pages 131072, num gpu pages 131072
[  222.339115] [drm] Loading REDWOOD Microcode
[  222.354522] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
[  222.354628] radeon 0000:01:00.0: WB enabled
[  222.354632] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000040000c00 and cpu addr 0xffff88020c6c0c00
[  222.354634] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[  222.354635] [drm] Driver supports precise vblank timestamp query.
[  222.354668] radeon 0000:01:00.0: irq 47 for MSI/MSI-X
[  222.354678] radeon 0000:01:00.0: radeon: using MSI.
[  222.354703] [drm] radeon: irq initialized.
[  222.371054] [drm] ring test on 0 succeeded in 1 usecs
[  222.371366] [drm] ib test on ring 0 succeeded in 0 usecs
[  222.371754] [drm] Radeon Display Connectors
[  222.371755] [drm] Connector 0:
[  222.371757] [drm]   HDMI-A-1
[  222.371758] [drm]   HPD5
[  222.371760] [drm]   DDC: 0x6470 0x6470 0x6474 0x6474 0x6478 0x6478 0x647c 0x647c
[  222.371761] [drm]   Encoders:
[  222.371762] [drm]     DFP1: INTERNAL_UNIPHY2
[  222.371763] [drm] Connector 1:
[  222.371764] [drm]   DVI-I-1
[  222.371765] [drm]   HPD1
[  222.371767] [drm]   DDC: 0x6450 0x6450 0x6454 0x6454 0x6458 0x6458 0x645c 0x645c
[  222.371768] [drm]   Encoders:
[  222.371769] [drm]     DFP2: INTERNAL_UNIPHY1
[  222.371770] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[  222.371771] [drm] Connector 2:
[  222.371772] [drm]   VGA-1
[  222.371774] [drm]   DDC: 0x6440 0x6440 0x6444 0x6444 0x6448 0x6448 0x644c 0x644c
[  222.371775] [drm]   Encoders:
[  222.371776] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[  222.371816] [drm] Internal thermal controller with fan control
[  222.371859] [drm] radeon: power management initialized
[  222.417401] [drm] fb mappable at 0xD0142000
[  222.417404] [drm] vram apper at 0xD0000000
[  222.417405] [drm] size 5324800
[  222.417406] [drm] fb depth is 24
[  222.417407] [drm]    pitch is 5888
[  222.417571] fbcon: radeondrmfb (fb0) is primary device
[  222.627428] Console: switching to colour frame buffer device 180x56
[  222.629939] fb0: radeondrmfb frame buffer device
[  222.629940] drm: registered panic notifier
[  222.629946] [drm] Initialized radeon 2.18.0 20080528 for 0000:01:00.0 on minor 0
[  222.694230] hda-intel: 0000:01:00.1: Handle VGA-switcheroo audio client
[  222.694295] snd_hda_intel 0000:01:00.1: irq 48 for MSI/MSI-X
[  222.721615] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input4
[  222.756119] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[  222.992922] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[  223.092358] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[  224.476931] sky2 0000:02:00.0: eth0: Link is up at 1000 Mbps, full duplex, flow control rx
[  224.477553] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  234.051014] init: failsafe main process (1046) killed by TERM signal
[  234.075525] type=1400 audit(1394251626.135:5): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1250 comm="apparmor_parser"
[  234.075692] type=1400 audit(1394251626.135:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1248 comm="apparmor_parser"
[  234.076053] type=1400 audit(1394251626.139:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1248 comm="apparmor_parser"
[  234.076234] type=1400 audit(1394251626.139:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1248 comm="apparmor_parser"

```

---

