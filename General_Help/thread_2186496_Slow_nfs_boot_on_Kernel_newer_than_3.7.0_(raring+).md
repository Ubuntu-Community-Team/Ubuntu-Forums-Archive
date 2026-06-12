---
title: "Slow nfs boot on Kernel newer than 3.7.0 (raring+)"
date: 2013-11-07
forum: General Help
---

### Post by futuebox on 2013-11-07
After updating the ubuntu linux folder on my nfs server from precise (Kernel 3.2.0) to saucy (Kernel 3.11.0) I noticed that the boot now takes 10 seconds longer.
A local installation of saucy does not show that boot pause.
The problem also exists in raring (Kernel 3.8.0) so I used a raring installation and tried different Kernel versions from the mainline repository.
As Hardware platform I used VMware Workstation 9 with E1000 as nic.

Kernel 3.7.0 ist working fine, Kernel 3.7.1 is not.

**Kernel 3.7.0:**
http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-raring/linux-image-3.7.0-030700-generic_3.7.0-030700.201212102335_amd64.deb

*dmesg:*
```

...
[    0.851347] rtc_cmos 00:04: setting system clock to 2013-10-02 07:22:56 UTC (1380698576)
[    0.851522] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.851604] EDD information not available.
[    1.002401] Freeing unused kernel memory: 992k freed
[    1.002709] Write protecting the kernel read-only data: 12288k
[    1.007047] Freeing unused kernel memory: 1176k freed
[    1.009750] Freeing unused kernel memory: 968k freed
[    1.022939] udevd[92]: starting version 175
[    1.131957] e1000: Intel(R) PRO/1000 Network Driver - version 7.3.21-k8-NAPI
[    1.132078] e1000: Copyright (c) 1999-2006 Intel Corporation.
[    1.132266] e1000 0000:02:01.0: setting latency timer to 64
[    1.144744] usb 2-1: new full-speed USB device number 2 using uhci_hcd
[    1.506780] e1000 0000:02:01.0 eth0: (PCI:66MHz:32-bit) 00:0c:29:1c:49:98
[    1.507048] e1000 0000:02:01.0 eth0: Intel(R) PRO/1000 Network Connection
[    1.981035] usb 2-1: New USB device found, idVendor=0e0f, idProduct=0003
[    1.981206] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.981367] usb 2-1: Product: VMware Virtual USB Mouse
[    1.981498] usb 2-1: Manufacturer: VMware
[    2.103877] usb 2-2: new full-speed USB device number 3 using uhci_hcd
[    2.244820] usb 2-2: New USB device found, idVendor=0e0f, idProduct=0002
[    2.244991] usb 2-2: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    2.245590] usb 2-2: Product: VMware Virtual USB Hub
[    2.255809] hub 2-2:1.0: USB hub found
[    2.257771] hub 2-2:1.0: 7 ports detected
[    2.287687] FS-Cache: Loaded
[    2.297031] RPC: Registered named UNIX socket transport module.
[    2.297122] RPC: Registered udp transport module.
[    2.297190] RPC: Registered tcp transport module.
[    2.297258] RPC: Registered tcp NFSv4.1 backchannel transport module.
[    2.303706] FS-Cache: Netfs 'nfs' registered for caching
[    2.312230] e1000: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[    2.314659] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    2.314747] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[    2.566056] init: ureadahead main process (232) terminated with status 5
...
```

**Kernel 3.7.1:**
http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7.1-raring/linux-image-3.7.1-030701-generic_3.7.1-030701.201212171620_amd64.deb

*dmesg:*
```

...
[    0.860012] rtc_cmos 00:04: setting system clock to 2013-11-07 19:23:43 UTC (1383852223)
[    0.860191] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.860290] EDD information not available.
[    1.154064] usb 2-1: new full-speed USB device number 2 using uhci_hcd
[    1.995300] usb 2-1: New USB device found, idVendor=0e0f, idProduct=0003
[    1.995483] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.995655] usb 2-1: Product: VMware Virtual USB Mouse
[    1.995796] usb 2-1: Manufacturer: VMware
[    2.121148] usb 2-2: new full-speed USB device number 3 using uhci_hcd
[    2.266056] usb 2-2: New USB device found, idVendor=0e0f, idProduct=0002
[    2.266239] usb 2-2: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    2.266410] usb 2-2: Product: VMware Virtual USB Hub
[    2.275039] hub 2-2:1.0: USB hub found
[    2.276032] hub 2-2:1.0: 7 ports detected
[   12.896233] Freeing unused kernel memory: 996k freed
[   12.896558] Write protecting the kernel read-only data: 12288k
[   12.901872] Freeing unused kernel memory: 1184k freed
[   12.906611] Freeing unused kernel memory: 1012k freed
[   12.928339] udevd[93]: starting version 175
[   13.059894] e1000: Intel(R) PRO/1000 Network Driver - version 7.3.21-k8-NAPI
[   13.060012] e1000: Copyright (c) 1999-2006 Intel Corporation.
[   13.060198] e1000 0000:02:01.0: setting latency timer to 64
[   13.422908] e1000 0000:02:01.0 eth0: (PCI:66MHz:32-bit) 00:0c:29:1c:49:98
[   13.423217] e1000 0000:02:01.0 eth0: Intel(R) PRO/1000 Network Connection
[   13.427884] FS-Cache: Loaded
[   13.433383] RPC: Registered named UNIX socket transport module.
[   13.433469] RPC: Registered udp transport module.
[   13.433537] RPC: Registered tcp transport module.
[   13.433605] RPC: Registered tcp NFSv4.1 backchannel transport module.
[   13.440027] FS-Cache: Netfs 'nfs' registered for caching
[   13.449868] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.450511] e1000: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[   13.451637] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   13.708759] init: ureadahead main process (235) terminated with status 5
...
```


Any idea why there is a 10 seconds boot pause?

---

### Post by futuebox on 2013-11-08
The 3.10 Kernel from Debian works fine.
So I gess it is a Ubuntu kernel konfig problem.

```

echo "deb [http://ftp.de.debian.org/debian](http://ftp.de.debian.org/debian) wheezy-backports main" > /etc/apt/sources.list
apt-get update
apt-get -t wheezy-backports install linux-image-3.10-0.bpo.3-amd64 initramfs-tools
```

---

