---
title: "Atolla USB 3.0 Hub not recognised"
date: 2017-02-03
forum: General Help
---

### Post by 3246251196 on 2017-02-03
No longer recognises my external hub. This was not a problem about a week ago. I guess I have done an update at somepoint and there is some sort of regression? This works with my other SSD running Windows - the hub works as normal there.

Any ideas?

Cheers (see attached)


```
lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial
```
```

sudo lsusb 
Bus 002 Device 006: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 002 Device 005: ID 045e:0719 Microsoft Corp. Xbox 360 Wireless Adapter
Bus 002 Device 004: ID 058f:9410 Alcor Micro Corp. Keyboard
Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 28de:1142  
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

