---
title: "Serious screen flickering on XPS 15 when WiFi is on"
date: 2018-08-08
forum: General Help
---

### Post by chimprich on 2018-08-08
Hi

I have a problem with a new Dell XPS 15 1050. After installation (or just using the live image) of 18.04 (and .1) and turning on WiFi, I get dramatic screen flickering every few seconds, especially when pulling data across WiFi. This includes bursts of coloured static for many seconds, artefacts, and the screen going black until a key is pressed.

I've tried multiple different combinations of graphics drivers with the same effects.

I have also tried Fedora with the same results.

I can't understand why no one else seems to have had this problem. I'd suspect a hardware problem but Windows seemed to work OK. Any ideas appreciated.

> $ sudo lshw -C video
  *-display UNCLAIMED       
       description: 3D controller
       product: GP107M [GeForce GTX 1050 Ti Mobile]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:ec000000-ecffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:3000(size=128) memory:ed000000-ed07ffff
  *-display
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:138 memory:eb000000-ebffffff memory:80000000-8fffffff ioport:4000(size=64) memory:c0000-dffff

> $ sudo lshw -C network
  *-network                 
       description: Wireless interface
       product: QCA6174 802.11ac Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:3b:00.0
       logical name: wlp59s0
       version: 32
       serial: 9c:b6:d0:fd:9b:55
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath10k_pci driverversion=4.17.4-041704-generic firmware=WLAN.RM.4.4.1-00079-QCARMSWPZ-1 ip=192.168.2.201 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:139 memory:ed200000-ed3fffff



---

