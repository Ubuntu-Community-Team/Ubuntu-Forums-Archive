---
title: "Interrupts and freezes with rtl8723ae"
date: 2018-01-19
forum: General Help
---

### Post by Daneel.Olivaw on 2018-01-19
Using xubuntu 17.04, my laptop randomly freezes with no apparent reason. It can happen right after boot, or after some time. The whole OS freezes and it doesn't react to any input from mouse or keyboard and the only solution would be to force restart.

I know it's a pain in the a* to troubleshoot these unreplicable problems, but I have no idea how to go about it. 

My only clue right now seems to point to the wifi card (but I'm not 100% sure, so that's why I post this in General Help). A couple of times after rebooting from a freeze, the laptop was still unresponsive and top showed that ksoftirqd was using 100% of my CPU and in /proc/interrups there where 60+ million interrupts from PCI-MSI-1048576-edge     rtl_pci which, I gather, has to do with wifi. 

I have had some problems with this card before. Sometimes, my laptop's wifi would drop randomly. Internet would suddenly stop working (only for my laptop) and after turning off wifi to try to reconnect, it just would not connect or even detect APs. After installing [these drivers]("https://github.com/lwfinger/rtlwifi_new") the problem seemed to go away. 

Hopefully useful information:

```
    pao@pao:~$ lspci -v
    00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
        Subsystem: Pegatron Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>
        Kernel modules: ie31200_edac
    
    00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06) (prog-if 00 [VGA controller])
        Subsystem: Pegatron 4th Gen Core Processor Integrated Graphics Controller
        Flags: bus master, fast devsel, latency 0, IRQ 30
        Memory at f7800000 (64-bit, non-prefetchable) [size=4M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at f000 [size=64]
        [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: i915
    
    00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
        Subsystem: Pegatron Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
        Flags: bus master, fast devsel, latency 0, IRQ 34
        Memory at f7e14000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd_hda_intel
    
    00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05) (prog-if 30 [XHCI])
        Subsystem: Pegatron 8 Series/C220 Series Chipset Family USB xHCI
        Flags: bus master, medium devsel, latency 0, IRQ 27
        Memory at f7e00000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: xhci_hcd
    
    00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
        Subsystem: Pegatron 8 Series/C220 Series Chipset Family MEI Controller
        Flags: bus master, fast devsel, latency 0, IRQ 31
        Memory at f7e1e000 (64-bit, non-prefetchable) [size=16]
        Capabilities: <access denied>
        Kernel driver in use: mei_me
        Kernel modules: mei_me
    
    00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05) (prog-if 20 [EHCI])
        Subsystem: Pegatron 8 Series/C220 Series Chipset Family USB EHCI
        Flags: bus master, medium devsel, latency 0, IRQ 21
        Memory at f7e1c000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: ehci-pci
    
    00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
        Subsystem: Pegatron 8 Series/C220 Series Chipset High Definition Audio Controller
        Flags: bus master, fast devsel, latency 0, IRQ 32
        Memory at f7e10000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd_hda_intel
    
    00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0, IRQ 24
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: df200000-df3fffff
        Prefetchable memory behind bridge: 00000000df400000-00000000df5fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp
    
    00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0, IRQ 25
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: f7d00000-f7dfffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp
    
    00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0, IRQ 26
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: f7c00000-f7cfffff
        Prefetchable memory behind bridge: 00000000f0000000-00000000f00fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp
    
    00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05) (prog-if 20 [EHCI])
        Subsystem: Pegatron 8 Series/C220 Series Chipset Family USB EHCI
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at f7e1b000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: ehci-pci
    
    00:1f.0 ISA bridge: Intel Corporation HM86 Express LPC Controller (rev 05)
        Subsystem: Pegatron HM86 Express LPC Controller
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>
        Kernel driver in use: lpc_ich
        Kernel modules: lpc_ich
    
    00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05) (prog-if 01 [AHCI 1.0])
        Subsystem: Pegatron 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode]
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 28
        I/O ports at f0b0 [size=8]
        I/O ports at f0a0 [size=4]
        I/O ports at f090 [size=8]
        I/O ports at f080 [size=4]
        I/O ports at f060 [size=32]
        Memory at f7e1a000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>
        Kernel driver in use: ahci
        Kernel modules: ahci
    
    00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
        Subsystem: Pegatron 8 Series/C220 Series Chipset Family SMBus Controller
        Flags: medium devsel, IRQ 4
        Memory at f7e19000 (64-bit, non-prefetchable) [size=256]
        I/O ports at f040 [size=32]
        Kernel modules: i2c_i801
    
    02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter
        Subsystem: AzureWave RTL8723AE PCIe Wireless Network Adapter
        Flags: bus master, fast devsel, latency 0, IRQ 33
        I/O ports at e000 [size=256]
        Memory at f7d00000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: rtl8723ae
        Kernel modules: rtl8723ae
    
    03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
        Subsystem: Pegatron RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
        Flags: bus master, fast devsel, latency 0, IRQ 29
        I/O ports at d000 [size=256]
        Memory at f7c00000 (64-bit, non-prefetchable) [size=4K]
        Memory at f0000000 (64-bit, prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: r8169
        Kernel modules: r8169


```

---

### Post by Yellow Pasque on 2018-01-19
Are you loading the rtl8723ae module with "msi=1" parameter?

Before anyone else tells you, 17.04 is officially EOL now:
[https://lists.ubuntu.com/archives/ubuntu-announce/2018-January/000227.html](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January/000227.html)

---

### Post by Daneel.Olivaw on 2018-01-19
I think I am. It was recommended as a way of solving the wifi problem. 

> Before anyone else tells you, 17.04 is officially EOL now:
[https://lists.ubuntu.com/archives/ub...ry/000227.html]("https://lists.ubuntu.com/archives/ubuntu-announce/2018-January/000227.html")

I didn't realised. Ok. I will upgrade.

---

