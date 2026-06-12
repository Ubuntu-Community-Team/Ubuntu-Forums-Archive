---
title: "Internet drops out when using shared hub or streaming media"
date: 2014-09-08
forum: General Help
---

### Post by ashtonwar on 2014-09-08
Depending on the network I'm connected to my (wireless) internet will drop out every 30 seconds to every few hours. How often I drop out (seemingly) depends on the network, and the amount of traffic going through it. This leads me to believe packet collision is causing issues.

When dropping out the Unity icon shows I am still connected though I will be unable to ping Google, Facebook or any other site - they are still accessible via other devices on the same network.

Occasionally, but not always, this can be simply rectified by disconnecting and re-connecting, deleting the network via network manager or restarting the computer. This is not preferable.

I'm using Ubuntu 14.04, here is the output of lspci -v and lshw -C network. I don't have the expertise or the time to diagnose much further by myself. Answers to other questions haven't worked for me. I would appreciate any help.

lspci -v

    ```
ashton@laptop:~$ lspci -v
    00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
    Subsystem: Sony Corporation Device 90ab
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

    00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=06, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: c0000000-c0ffffff
    Prefetchable memory behind bridge: 00000000b0000000-00000000bfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

    00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04) (prog-if 30 [XHCI])
    Subsystem: Sony Corporation Device 90ab
    Flags: bus master, medium devsel, latency 0, IRQ 41
    Memory at c1300000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

    00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: Sony Corporation Device 90ab
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at c1314000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: mei_me

    00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Sony Corporation Device 90ab
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at c1319000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

    00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
    Subsystem: Sony Corporation Device 90ab
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at c1310000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

    00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
    Memory behind bridge: c1200000-c12fffff
    Prefetchable memory behind bridge: 00000000c1500000-00000000c15fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

    00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
    Memory behind bridge: c1100000-c11fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

    00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Prefetchable memory behind bridge: 00000000c1000000-00000000c10fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

    00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Sony Corporation Device 90ab
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at c1318000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

    00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
    Subsystem: Sony Corporation Device 90ab
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: lpc_ich

    00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
    Subsystem: Sony Corporation Device 90ab
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 44
    I/O ports at 4048 [size=8]
    I/O ports at 4054 [size=4]
    I/O ports at 4040 [size=8]
    I/O ports at 4050 [size=4]
    I/O ports at 4020 [size=32]
    Memory at c1317000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

    00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
    Subsystem: Sony Corporation Device 90ab
    Flags: medium devsel, IRQ 10
    Memory at c1315000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 4000 [size=32]

    01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Thames [Radeon HD 7550M/7570M/7650M] (prog-if 00 [VGA controller])
    Subsystem: Sony Corporation Device 90ab
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    Memory at c0000000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at 3000 [size=256]
    Expansion ROM at c0040000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon

    01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Turks/Whistler HDMI Audio [Radeon HD 6000 Series]
    Subsystem: Sony Corporation Device 90ab
    Flags: bus master, fast devsel, latency 0, IRQ 48
    Memory at c0020000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

    07:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
    Subsystem: Foxconn International, Inc. Device e044
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at c1200000 (64-bit, non-prefetchable) [size=512K]
    Expansion ROM at c1500000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath9k

    08:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
    Subsystem: Sony Corporation Device 90ab
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at c1100000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: rtsx_pci

    09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 07)
    Subsystem: Sony Corporation Device 90ab
    Flags: bus master, fast devsel, latency 0, IRQ 43
    I/O ports at 2000 [size=256]
    Memory at c1004000 (64-bit, prefetchable) [size=4K]
    Memory at c1000000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
```

lshw -C network

    ```
ashton@laptop:~$ sudo lshw -C network
    *-network               
    description: Wireless interface
    product: AR9485 Wireless Network Adapter
    vendor: Qualcomm Atheros
    physical id: 0
    bus info: pci@0000:07:00.0
    logical name: wlan0
    version: 01
    serial: 08:3e:8e:d2:5d:81
    width: 64 bits
    clock: 33MHz
    capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
    configuration: broadcast=yes driver=ath9k driverversion=3.13.0-29-generic firmware=N/A ip=192.168.0.6 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
    resources: irq:16 memory:c1200000-c127ffff memory:c1500000-c150ffff
    *-network
    description: Ethernet interface
    product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
    vendor: Realtek Semiconductor Co., Ltd.
    physical id: 0
    bus info: pci@0000:09:00.0
    logical name: eth0
    version: 07
    serial: 30:f9:ed:c3:f2:e3
    size: 10Mbit/s
    capacity: 1Gbit/s
    width: 64 bits
    clock: 33MHz
    capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
    configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
    resources: irq:43 ioport:2000(size=256) memory:c1004000-c1004fff memory:c1000000-c1003fff
```

I've noticed in the "Connection Information" window accessible through networkManager the speed generally shows as 16Mb/s upwards whether or not I can currently access the internet. Unsure what the importance of this is but importance it surely has?

Will appreciate any help.

Note: This question was orignally posted on [AskUbuntu.com]("http://askubuntu.com/questions/513539/internet-drops-out-when-using-shared-hub-or-streaming-media") in August, it was up-voted twice but remained unanswered and unsolved.

---

### Post by uRock on 2014-09-08
Hello and welcome to the forums. 

Did you say you are using a hub? [http://www.thebryantadvantage.com/CCNACCENTCertificationTrainingHubsCollisionDomains.htm](http://www.thebryantadvantage.com/CCNACCENTCertificationTrainingHubsCollisionDomains.htm)
[IMG]http://www.thebryantadvantage.com/images/Hub%202%20Data%20Collision.jpg[/IMG]
If this is what you are using, then the best way to fix it is to get a switch.

---

### Post by ashtonwar on 2014-09-08
> **uRock said:**
> Hello and welcome to the forums. 

Did you say you are using a hub? [http://www.thebryantadvantage.com/CCNACCENTCertificationTrainingHubsCollisionDomains.htm](http://www.thebryantadvantage.com/CCNACCENTCertificationTrainingHubsCollisionDomains.htm)
If this is what you are using, then the only way to fix it is to get a switch.

I'm aware of collision domains. I suspected these were the source of the problem: "This leads me to believe packet collision is causing issues". Surely Ubuntu should be able to recover from these just as other OSs do?

---

### Post by wildmanne39 on 2014-09-08
Please try this:
```
sudo ifconfig wlan0 down
sudo modprobe -rv ath9k
sudo modprobe -v ath9k nohwcrypt=1
sudo ifconfig wlan0 up
```
if it helps we will need to make it permanent, the settings will be lost after you reboot.
Thanks

---

### Post by ashtonwar on 2014-09-09
> **Wild Man said:**
> Please try this:
```
sudo ifconfig wlan0 down
sudo modprobe -rv ath9k
sudo modprobe -v ath9k nohwcrypt=1
sudo ifconfig wlan0 up
```


When trying these commands this happens, the behaviour is identical whether or not the internet was functioning correctly beforehand:


[LIST=1]
[*]The internet disconnects. 
[*]Something[SUP][1][/SUP] is logged in the console. 
[*]The networks disappear from the networkManager drop-down. 
[*]Two different scenarios encountered, unable to isolate branching behaviour.
_*Scenario A*_
Nothing happens
*_Scenario B_*
The drop-down options reappear and networkManager attempts to reconnect but always fails. 
[*]The only way I know how to regain a connection from here is to restart the computer. 
[/LIST]
 
[1] [console log] -
```
ashton@laptop:~$ sudo ifconfig wlan0 down && sudo modprobe -rv ath9k && sudo modprobe -v ath9k nohwcrypt=1 && sudo ifconfig wlan0 up
[sudo] password for ashton: 
rmmod ath9k
rmmod mac80211
rmmod ath9k_common
rmmod ath9k_hw
rmmod ath
rmmod cfg80211
insmod /lib/modules/3.13.0-29-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.13.0-29-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko 
insmod /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko 
insmod /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko nohwcrypt=1 
```

---

### Post by ashtonwar on 2014-09-16
Will pay $30 USD (via PayPal) to anyone who can fully resolve this issue. That means making my laptop capable of connecting to any network where reasonable and not dropping out constantly. Very preferably without having to spend additional money on a hardware fix or similar.

---

### Post by uRock on 2014-09-18
For that price you could buy a 24 port Cisco switch on Ebay.

---

