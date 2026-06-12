---
title: "external usb storage not recognized"
date: 2012-12-17
forum: General Help
---

### Post by anonymus302 on 2012-12-17
Hi,
i was copying some files from my external drive (usb 2.0, ntfs) to my backup drive when my pc went down. After i rebooted him, i can still access my backup drive but not my other external drive.

Nothing useful with
dmesg
```
[  493.988367] e100: eth0 NIC Link is Down
[  505.989192] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[ 1251.423588] ecryptfs_lookup: lookup_one_len() returned [-36] on lower_dentry = 
```

lsusb
```

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Doesnt work under WinXP or OpenSuse.

Any ideas whats wrong?

[10.04]


EDIT: [SOLVED]
I dont know what happened, but i just unplugged the power supply, replugged it and it worked....
Switched the usb-plug several times but never thought unplugging and replugging would help.

---

