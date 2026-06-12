---
title: "Strange (for me) error messages"
date: 2008-03-09
forum: General Help
---

### Post by Silvernail on 2008-03-09
Several months ago I installed 'ubuntu 7.04' on a  Compaq Presario. Don't play with it much. One day a  window   pops  up and says that vers 7.11 is available for download and installation. I do so. Then I find that eleven is not the latest stable version. I also notice that this message is appearing when I boot.

8.972188 cannot allocate resource  region 7 of bridge 0000:00:1c.0
8.972245 cannot allocate resource  region 8 of bridge 0000:00:1c.0
8.972315 cannot allocate resource  region 7 of bridge 0000:00:1c.2
8.972375 cannot allocate resource  region 8 of bridge 0000:00:1c.2
8.972471 cannot allocate resource  region 0 of device 0000:06:00.0

Would someone tell me what this means and is it detrimental to the health of my laptop?

I am assuming that is is falling short of memory.

TIA
Dave

---

### Post by jeffus_il on 2008-03-10
Do```
 lspci
``` in a terminal and post the output. We may be able to see which devices are giving you the problem.

---

### Post by jeffus_il on 2008-03-10
Some one solved a similar problem with "pci=routeirq"  to the kernel options.
See:
[http://ubuntuforums.org/showthread.php?t=601828](http://ubuntuforums.org/showthread.php?t=601828)

---

### Post by prshah on 2008-03-10
> **jeffus_il said:**
> Do```
 lspci
``` in a terminal and post the output. We may be able to see which devices are giving you the problem.

Slight modification: try:

```

lspci | grep -i 1c

```

for more to-the-point info. If this is blank then please post the entire lspci output.

Cheers,
PRShah

---

### Post by Silvernail on 2008-03-13
Thanks for ressponding. I will try these suggestion and get back this weekend.

Dave

---

### Post by Silvernail on 2008-03-15
> **prshah said:**
> Slight modification: try:

```

lspci | grep -i 1c

```

for more to-the-point info. If this is blank then please post the entire lspci output.

Cheers,
PRShah

```

dave@gadabout:~$ lspci | grep 1c
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
dave@gadabout:~$

```

---

### Post by Silvernail on 2008-03-16
lshw -C network

WARNING: you should run this program as super-user.
  *-network DISABLED
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 01
       serial: 00:1a:73:39:c1:83
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=0 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:c5:d9:e0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.115 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes

---

### Post by prshah on 2008-03-16
> **Silvernail said:**
> ```

dave@gadabout:~$ lspci | grep 1c
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
dave@gadabout:~$

```

Looks like a clash between your network card and your Intel on-board graphics adapter. Do you have Plug and Play enabled in your BIOS settings? 

When your computer is starting up, keep tapping F2. This will open the BIOS screen. Look for an option like "Plug And Play" or "PnP OS" or "Resouces Managed by" something similar, and enable it, or set it to automatic, depending on whatever options are available.

---

