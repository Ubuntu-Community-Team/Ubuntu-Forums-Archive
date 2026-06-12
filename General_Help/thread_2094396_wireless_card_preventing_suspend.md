---
title: "wireless card preventing suspend"
date: 2012-12-13
forum: General Help
---

### Post by Dave6187 on 2012-12-13
I'm having a weird issue with my machine, everything worked beautifully on 10.10, decided to upgrade up the chain to 12.04

I know there's issues with the broadcom wireless drivers but this one has me stumped, especially since it seems related to a new issue where my machine won't suspend any more. It does everything like it should, screen goes black, and everything shuts down for about a half second, then boots back on and logs me back in.

its as if something is waking it back up, or preventing it from entirely suspending.

this is my lspci -v

```
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
    Subsystem: ASUSTeK Computer Inc. Device 8383
    Flags: fast devsel
    Capabilities: <access denied>

00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: f8000000-fb8fffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
    Subsystem: Device 0043:0083
    Flags: fast devsel
    Capabilities: <access denied>

00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
    Subsystem: Device 0043:0083
    Flags: fast devsel
    Capabilities: <access denied>

00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
    Subsystem: Device 0043:0083
    Flags: fast devsel
    Capabilities: <access denied>

00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
    Flags: fast devsel

00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
    Flags: fast devsel

00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
    Flags: fast devsel

00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 8383
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f7ffe000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device 83d0
    Flags: bus master, fast devsel, latency 0, IRQ 59
    Memory at f7ff8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=0b, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fbb00000-fbdfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fba00000-fbafffff
    Prefetchable memory behind bridge: 00000000f6f00000-00000000f6ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.6 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 7 (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: fb900000-fb9fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.7 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 8 (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: c0000000-c01fffff
    Prefetchable memory behind bridge: 00000000c0200000-00000000c03fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 8383
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f7ffd000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=32
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fbe00000-fbefffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device 8383
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: ASUSTeK Computer Inc. Device 8383
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 21
    I/O ports at 8c00 [size=8]
    I/O ports at 8880 [size=4]
    I/O ports at 8800 [size=8]
    I/O ports at 8480 [size=4]
    I/O ports at 8400 [size=16]
    I/O ports at 8080 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device 8383
    Flags: medium devsel, IRQ 15
    Memory at f7ffc000 (64-bit, non-prefetchable) [size=256]
    I/O ports at ffe0 [size=32]
    Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 06) (prog-if 85 [Master SecO PriO])
    Subsystem: ASUSTeK Computer Inc. Device 8383
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 21
    I/O ports at 9c00 [size=8]
    I/O ports at 9880 [size=4]
    I/O ports at 9800 [size=8]
    I/O ports at 9480 [size=4]
    I/O ports at 9400 [size=16]
    I/O ports at 9080 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

01:00.0 VGA compatible controller: NVIDIA Corporation G92 [GeForce GTS 250] (rev a2) (prog-if 00 [VGA controller])
    Subsystem: Device 196e:079e
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at ac00 [size=128]
    [virtual] Expansion ROM at fb8e0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia_current, nouveau, nvidiafb

03:00.0 SATA controller: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 03) (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. Device 824f
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at fb9fe000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

03:00.1 IDE interface: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 03) (prog-if 85 [Master SecO PriO])
    Subsystem: ASUSTeK Computer Inc. Device 824f
    Flags: bus master, fast devsel, latency 0, IRQ 19
    I/O ports at bc00 [size=8]
    I/O ports at b880 [size=4]
    I/O ports at b800 [size=8]
    I/O ports at b480 [size=4]
    I/O ports at b400 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_jmicron
    Kernel modules: pata_jmicron

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard
    Flags: bus master, fast devsel, latency 0, IRQ 58
    I/O ports at c800 [size=256]
    Memory at f6fff000 (64-bit, prefetchable) [size=4K]
    Memory at f6ff8000 (64-bit, prefetchable) [size=16K]
    Expansion ROM at fbaf0000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

06:00.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Memory at fbbe0000 (32-bit, non-prefetchable) [size=128K]
    Bus: primary=06, secondary=07, subordinate=0b, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fbc00000-fbdfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

07:01.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=07, secondary=08, subordinate=08, sec-latency=0
    Memory behind bridge: fbc00000-fbcfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

07:05.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=07, secondary=09, subordinate=09, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fbd00000-fbdfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

07:07.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=07, secondary=0a, subordinate=0a, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

07:09.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=07, secondary=0b, subordinate=0b, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

08:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03) (prog-if 30 [XHCI])
    Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at fbcfe000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

09:00.0 IDE interface: Marvell Technology Group Ltd. Device 914d (rev 10) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: ASUSTeK Computer Inc. Device 8400
    Flags: fast devsel, IRQ 17
    I/O ports at dc00 [size=8]
    I/O ports at d880 [size=4]
    I/O ports at d800 [size=8]
    I/O ports at d480 [size=4]
    I/O ports at d400 [size=16]
    Memory at fbdff800 (32-bit, non-prefetchable) [size=2K]
    Expansion ROM at fbde0000 [disabled] [size=64K]
    Capabilities: <access denied>

0c:02.0 Network controller: Broadcom Corporation BCM4321 802.11b/g/n (rev 01)
    Subsystem: Netgear WN311B RangeMax Next 270 Mbps Wireless PCI Adapter
    Flags: fast devsel, IRQ 17
    Memory at fbefc000 (32-bit, non-prefetchable) [size=16K]
    Kernel driver in use: wl
    Kernel modules: wl, ssb

0c:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0) (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. M4A series motherboard
    Flags: bus master, medium devsel, latency 64, IRQ 18
    Memory at fbefb800 (32-bit, non-prefetchable) [size=2K]
    I/O ports at ec00 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci

ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0
    Kernel driver in use: i7core_edac
    Kernel modules: i7core_edac

ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0
```

and this is why i believe the two issues are related

```
~$ lsmod | grep -e b43 -e wl -e bcma
wl                   2568249  0 
lib80211               14381  2 lib80211_crypt_tkip,wl

~$ dmesg | grep -i -e wl -e 0c:02
[    1.206406] pci 0000:0c:02.0: [14e4:4329] type 0 class 0x000280
[    1.206417] pci 0000:0c:02.0: reg 10: [mem 0xfbefc000-0xfbefffff]
[   12.235692] wl 0000:0c:02.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  210.092543] wl 0000:0c:02.0: PCI INT A disabled
[  210.092588] pci_legacy_suspend(): wl_suspend+0x0/0xa0 [wl] returns -5
[  210.092601] PM: Device 0000:0c:02.0 failed to suspend async: error -5
```

i even tried reinstalling and updating the root files from the cd (i have my home on a separate partition) which didn't make any difference.

this is driving me insane though because it worked fine on 10.10. I'm considering upgrading to 12.10 to see if that changes anything but i don't think it will

---

### Post by Dave6187 on 2012-12-13
bump?

---

### Post by Dave6187 on 2012-12-13
more pieces to the puzzle...  

in my pm-suspend log i found this after a suspend attempt:
```
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.
```

also thought that it couldn't find wl0 was interesting:

```
sudo lshw -C network
[sudo] password for dave6187: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 03
       serial: 48:5b:39:36:1a:94
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-2.fw ip=192.168.137.104 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:58 ioport:c800(size=256) memory:f6fff000-f6ffffff memory:f6ff8000-f6ffbfff memory:fbaf0000-fbafffff
  *-network
       description: Wireless interface
       product: BCM4321 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:0c:02.0
       logical name: eth2
       version: 01
       serial: e0:91:f5:67:34:d1
       width: 32 bits
       clock: 33MHz
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=64 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fbefc000-fbefffff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: 02:e5:f1:43:60:51
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device link=yes multicast=yes
dave6187@Ubuntu-Dave:~$ sudo modprobe -r wl0
FATAL: Module wl0 not found.

```

i stopped network-manager before trying to suspend, both from the console and the dropdown, neither of which worked, and resulted in the same errors in the log file

---

### Post by Rexilion on 2012-12-14
Could you provide the output of 'dmesg' (full version, including an attempted suspend!) on pastebin.com.

And in a reply, the outpuf of 'lsmod'.

---

### Post by Dave6187 on 2012-12-14
i tried suspending it, then pulled a copy of dmesg: [http://pastebin.com/Bsv0gnkW](http://pastebin.com/Bsv0gnkW)

and here's my lsmod

```
Module                  Size  Used by
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
vesafb                 13844  1 
usblp                  18307  0 
snd_hda_codec_via      51398  1 
snd_usb_audio         122982  2 
snd_hda_intel          33773  3 
snd_hda_codec         127706  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
snd_usbmidi_lib        25395  1 snd_usb_audio
snd_pcm                97188  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
nvidia              11257276  40 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
lib80211_crypt_tkip    17390  0 
mxm_wmi                12979  0 
joydev                 17693  0 
wmi                    19256  1 mxm_wmi
snd                    78855  21 snd_hda_codec_via,snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_usbmidi_lib,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wl                   2568210  0 
asus_atk0110           18078  0 
soundcore              15091  1 snd
lib80211               14381  2 lib80211_crypt_tkip,wl
psmouse                97443  0 
serio_raw              13211  0 
i7core_edac            28102  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
edac_core              53746  3 i7core_edac
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
uas                    18180  0 
usb_storage            49198  0 
hid_logitech           26520  0 
ff_memless             13097  1 hid_logitech
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
usbhid                 47199  1 hid_logitech
hid                    99592  2 hid_logitech,usbhid
crc_itu_t              12707  1 firewire_core
r8169                  62099  0 
pata_jmicron           12747  0 

```

thanks again for helping me out with this...

---

### Post by Rexilion on 2012-12-15
I had a hunch it was ndiswrapper you were using. But it seems to be a propietary kernel module.

Any reason why you are using that?

There is an opensource kernel module which works pretty good these days (b43).

FIY the card is: 'product: BCM4321 802.11b/g/n' . And I think I have the same.

---

### Post by Dave6187 on 2012-12-15
Honestly,  this is on a clean install now. I've been messing around trying to get the wireless to work again, then noticed the suspend issue, couldn't remember everything I tweaked so I decided to just start fresh and ask for help, but neither of the issues went away after reinstall

---

### Post by Rexilion on 2012-12-15
Looks like the wl driver is part of a restricted module install offered by Ubuntu. Didn't knew that ([link here]("http://ubuntuforums.org/showthread.php?t=824931")).

The page of the opensource driver [lists]("http://linuxwireless.org/en/users/Drivers/b43") it as supported since 2.6.39.

Easiest (and best) IMHO is to disable the wl driver.

Could you post the output of:

```
dpkg --get-selections | grep -e bcmwl -e broadcom
```

---

### Post by Dave6187 on 2012-12-15
here ya go

```
dave6187@Ubuntu-Dave:~$ dpkg --get-selections | grep -e bcmwl -e broadcom
bcmwl-kernel-source                install

```

---

### Post by Dave6187 on 2012-12-15
I went ahead and removed/blacklisted the wl driver. From what i was reading, i should have the STA driver installed for this card, so i installed them:

```
dave6187@Ubuntu-Dave:~$ dpkg --get-selections | grep -e bcmwl -e broadcom.
broadcom-sta-common                install
broadcom-sta-source                install

```


now it seems that my suispend/shutdown/etc are working as they should, but now wireless doesn't even show up as a network option, which presumably is a different problem entirely.

---

### Post by Rexilion on 2012-12-16
You could provide another snippet of dmesg so I can take a look.

Why not try the in kernel driver (b43?), by not installing anything else?

---

### Post by Dave6187 on 2012-12-17
I tried the b43 kernel/firmware and i was able to get network manager to list all available networks, but it would not successfully connect to mine, would just keep saying connect. retried the wl driver and such, started with the suspend issue again.

---

### Post by Rexilion on 2012-12-17
Can you post dmesg output with the b43 kernel driver? Make sure you attempt to connect to another network before you do so.

---

### Post by Dave6187 on 2012-12-18
[http://pastebin.com/kdTe1mFR](http://pastebin.com/kdTe1mFR)

---

### Post by Rexilion on 2012-12-18
You are still using the 'wl' driver:

'[   12.340265] wl 0000:0c:02.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17'

---

### Post by Dave6187 on 2012-12-18
thats... interesting:

```

0c:02.0 Network controller: Broadcom Corporation BCM4321 802.11b/g/n (rev 01)
    Subsystem: Netgear WN311B RangeMax Next 270 Mbps Wireless PCI Adapter
    Flags: bus master, fast devsel, latency 64, IRQ 17
    Memory at fbefc000 (32-bit, non-prefetchable) [size=16K]
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

```


```

Module                  Size  Used by
arc4                   12529  2 
b43                   365785  0 
mac80211              506816  1 b43
cfg80211              205544  2 b43,mac80211
bcma                   26696  1 b43
ssb                    52752  1 b43
nls_utf8               12557  1 
isofs                  40257  1 
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               287082  4 vboxpci,vboxnetadp,vboxnetflt
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
vesafb                 13844  1 
lib80211_crypt_tkip    17390  0 
snd_hda_codec_via      51398  1 
mxm_wmi                12979  0 
lib80211               14381  1 lib80211_crypt_tkip
snd_usb_audio         122982  2 
snd_usbmidi_lib        25395  1 snd_usb_audio
snd_seq_midi           13324  0 
snd_rawmidi            30748  2 snd_usbmidi_lib,snd_seq_midi
snd_hda_intel          33773  3 
snd_hda_codec         127706  2 snd_hda_codec_via,snd_hda_intel
snd_seq_midi_event     14899  1 snd_seq_midi
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_pcm                97188  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
i7core_edac            28102  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
edac_core              53746  3 i7core_edac
snd_timer              29990  2 snd_seq,snd_pcm
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
snd                    78855  21 snd_hda_codec_via,snd_usb_audio,snd_usbmidi_lib,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_seq,snd_pcm,snd_seq_device,snd_timer
soundcore              15091  1 snd
usblp                  18307  0 
joydev                 17693  0 
nvidia              11257276  50 
psmouse                97443  0 
serio_raw              13211  0 
wmi                    19256  1 mxm_wmi
asus_atk0110           18078  0 
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
uas                    18180  0 
usb_storage            49198  0 
hid_logitech           26520  0 
ff_memless             13097  1 hid_logitech
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
usbhid                 47199  1 hid_logitech
hid                    99592  2 hid_logitech,usbhid
crc_itu_t              12707  1 firewire_core
pata_jmicron           12747  0 
r8169                  62099  0 

```

i had completely uninstalled and blacklisted it

---

### Post by Rexilion on 2012-12-19
Under the above conditions: Does it work? Will it suspend? Can you provide me a dmesg? Does it connect?

---

