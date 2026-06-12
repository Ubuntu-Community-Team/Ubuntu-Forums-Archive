---
title: "External HDDs stopped mounting automatically"
date: 2019-05-09
forum: General Help
---

### Post by FarJumper on 2019-05-09
I noticed that after last updates my external HDDs are not being mounted automatically anymore when I plug them. Checked with two disks today, both detects but silently failed to mount:

dmesg for HDD 1:

```
May  9 11:45:55 linilla kernel: [15519.543604] sd 8:0:0:0: [sdc] Spinning up disk...
May  9 11:45:55 linilla mtp-probe: checking bus 9, device 4: "/sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0/usb9/9-1"
May  9 11:45:55 linilla mtp-probe: bus: 9, device: 4 was not an MTP device
May  9 11:46:00 linilla kernel: [15524.338443] .ready
May  9 11:46:00 linilla kernel: [15524.356392] sd 8:0:0:0: [sdc] 3907029167 512-byte logical blocks: (2.00 TB/1.82 TiB)
May  9 11:46:00 linilla kernel: [15524.356813] sd 8:0:0:0: [sdc] Write Protect is off
May  9 11:46:00 linilla kernel: [15524.356816] sd 8:0:0:0: [sdc] Mode Sense: 2b 00 10 08
May  9 11:46:00 linilla kernel: [15524.357667] sd 8:0:0:0: [sdc] Write cache: enabled, read cache: enabled, supports DPO and FUA
May  9 11:46:00 linilla kernel: [15524.408004]  sdc: sdc1
May  9 11:46:00 linilla kernel: [15524.428201] sd 8:0:0:0: [sdc] Attached SCSI disk
May  9 11:46:00 linilla systemd-udevd[24424]: Process 'ata_id --export /dev/sdc' failed with exit code 2.
```

I see udev failing with an error "Process 'ata_id --export /dev/sdc' failed with exit code 2". I thought that this might be the cause, but it's clean for the second drive, so might be not an issue:


dmesg for HDD 2:

```
May  9 12:07:34 linilla kernel: [16818.745886] scsi 9:0:0:0: Direct-Access     TOSHIBA  External USB 3.0 0    PQ: 0 ANSI: 6
May  9 12:07:34 linilla kernel: [16818.746628] sd 9:0:0:0: Attached scsi generic sg3 type 0
May  9 12:07:36 linilla kernel: [16820.986897] sd 9:0:0:0: [sdd] 1953525168 512-byte logical blocks: (1.00 TB/932 GiB)
May  9 12:07:36 linilla kernel: [16820.987433] sd 9:0:0:0: [sdd] Write Protect is off
May  9 12:07:36 linilla kernel: [16820.987436] sd 9:0:0:0: [sdd] Mode Sense: 43 00 00 00
May  9 12:07:36 linilla kernel: [16820.987894] sd 9:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  9 12:07:36 linilla kernel: [16820.993943]  sdd: sdd1
May  9 12:07:36 linilla kernel: [16820.995993] sd 9:0:0:0: [sdd] Attached SCSI disk
May  9 12:07:45 linilla kernel: [16829.930316] usb 9-3: reset SuperSpeed Gen 1 USB device number 5 using xhci_hcd
```

Another observation is that Nautilus started showing all mount points in the list of devices including /proc:

[ATTACH=CONFIG]283235[/ATTACH]

Ubuntu 19.04
Kernel: Linux linzilla 5.0.0-14-generic #15-Ubuntu SMP Wed Apr 24 15:39:57 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by FarJumper on 2019-05-09
Did apt-upgrade to the latest, rebooted and the problem gone. Don't know whether it was some sporadic issue or upgrade actually did help. Anyway, here is the list of packages which were upgraded and helped (or didn't):

Start-Date: 2019-05-09  13:15:26
Upgrade: linux-firmware:amd64 (1.178, 1.178.1), ubuntu-settings:amd64 (19.04.3, 19.04.3.1), gnome-control-center-data:amd64 (1:3.32.1-1ubuntu4, 1:3.32.1-1ubuntu4.1), gnome-control-center:amd64 (1:3.32.1-1ubuntu4, 1:3.32.1-1ubuntu4.1), python3-distupgrade:amd64 (1:19.04.16.3, 1:19.04.16.4), ubuntu-release-upgrader-core:amd64 (1:19.04.16.3, 1:19.04.16.4), gnome-shell-extension-appindicator:amd64 (28-1, 29-1~ubuntu19.04.1), gnome-control-center-faces:amd64 (1:3.32.1-1ubuntu4, 1:3.32.1-1ubuntu4.1), ubuntu-release-upgrader-gtk:amd64 (1:19.04.16.3, 1:19.04.16.4), libibverbs1:amd64 (22.1-1, 22.1-1ubuntu0.1), ibverbs-providers:amd64 (22.1-1, 22.1-1ubuntu0.1), librdmacm1:amd64 (22.1-1, 22.1-1ubuntu0.1), bash:amd64 (5.0-3ubuntu1, 5.0-3ubuntu1.1)
End-Date: 2019-05-09  13:15:33)

---

