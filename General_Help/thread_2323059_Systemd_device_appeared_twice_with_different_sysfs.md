---
title: "Systemd device appeared twice with different sysfs paths log message"
date: 2016-05-02
forum: General Help
---

### Post by karambit27 on 2016-05-02
I recently upgraded my server after running 12.04 for years to 16.04. Everything went fairly well but recently systemd has been spamming my syslog with the following messages.

```
May  2 15:48:05 gibson systemd[2872]: dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d2.device: Dev dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d2.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata2/host1/target1:0:1/1:0:1:0/block/sdd and /sys/devices/pci0000:00/0000:00:1f.2/ata2/host1/target1:0:0/1:0:0:0/block/sdcMay  2 15:48:05 gibson systemd[1]: dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d2.device: Dev dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d2.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata2/host1/target1:0:1/1:0:1:0/block/sdd and /sys/devices/pci0000:00/0000:00:1f.2/ata2/host1/target1:0:0/1:0:0:0/block/sdc
May  2 15:48:05 gibson systemd[1]: dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d1.device: Dev dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d1.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata1/host0/target0:0:1/0:0:1:0/block/sdb and /sys/devices/pci0000:00/0000:00:1f.2/ata1/host0/target0:0:0/0:0:0:0/block/sda
May  2 15:48:05 gibson systemd[2872]: dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d1.device: Dev dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d1.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata1/host0/target0:0:1/0:0:1:0/block/sdb and /sys/devices/pci0000:00/0000:00:1f.2/ata1/host0/target0:0:0/0:0:0:0/block/sda
May  2 15:48:05 gibson systemd[2872]: dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d2\x2dpart1.device: Dev dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d2\x2dpart1.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata2/host1/target1:0:1/1:0:1:0/block/sdd/sdd1 and /sys/devices/pci0000:00/0000:00:1f.2/ata2/host1/target1:0:0/1:0:0:0/block/sdc/sdc1
May  2 15:48:05 gibson systemd[1]: dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d2\x2dpart1.device: Dev dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d2\x2dpart1.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata2/host1/target1:0:1/1:0:1:0/block/sdd/sdd1 and /sys/devices/pci0000:00/0000:00:1f.2/ata2/host1/target1:0:0/1:0:0:0/block/sdc/sdc1
May  2 15:48:05 gibson systemd[2872]: dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d2.device: Dev dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d2.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata2/host1/target1:0:1/1:0:1:0/block/sdd and /sys/devices/pci0000:00/0000:00:1f.2/ata2/host1/target1:0:0/1:0:0:0/block/sdc
May  2 15:48:05 gibson systemd[1]: dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d2.device: Dev dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d2.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata2/host1/target1:0:1/1:0:1:0/block/sdd and /sys/devices/pci0000:00/0000:00:1f.2/ata2/host1/target1:0:0/1:0:0:0/block/sdc
May  2 15:48:05 gibson systemd[2872]: dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d1\x2dpart1.device: Dev dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d1\x2dpart1.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata1/host0/target0:0:1/0:0:1:0/block/sdb/sdb1 and /sys/devices/pci0000:00/0000:00:1f.2/ata1/host0/target0:0:0/0:0:0:0/block/sda/sda1
May  2 15:48:05 gibson systemd[1]: dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d1\x2dpart1.device: Dev dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d1\x2dpart1.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata1/host0/target0:0:1/0:0:1:0/block/sdb/sdb1 and /sys/devices/pci0000:00/0000:00:1f.2/ata1/host0/target0:0:0/0:0:0:0/block/sda/sda1

```

All of the drives it mentions are part of a raid6 array using madadm. I believe it is because they have the same UUID as is typical with a raid. I don't recall seeing these messages after the upgrade so I am wondering if there was an update to cause these. I can't seem to find any real in formation searching around. I did read somewhere that this is a debug level message but /etc/systemd/system.conf has never been changed and everything is commented out so they should be the defaults. I'd like to figure how to stop these messages from filling up my logs. They don't appear to be causing any real problems.

---

### Post by karambit27 on 2016-05-03
I tried to specifically set the systemd log level to info in the config file and rebooted and these log messages are still coming in. They repeat every 5 minutes. I can't find any information anywhere on what is causing this or how to stop it.

---

