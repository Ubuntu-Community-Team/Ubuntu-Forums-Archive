---
title: "[ubuntu] Ubuntu 16.04.04 64 bit LTS &amp; Oppo Digital HA-1 DAC &amp; Headphone Amplifier"
date: 2016-06-16
forum: General Help
---

### Post by Welly Wu on 2016-06-16
```
wellywu@ZareasonZeto:~$ lsusb
Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 004: ID 05e3:0616 Genesys Logic, Inc. hub
Bus 004 Device 003: ID 174c:55aa ASMedia Technology Inc. ASM1051E SATA 6Gb/s bridge, ASM1053E SATA 6Gb/s bridge, ASM1153 SATA 3Gb/s bridge
Bus 004 Device 005: ID 0bc2:ab2a Seagate RSS LLC 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 020: ID 046d:082d Logitech, Inc. HD Pro Webcam C920
Bus 003 Device 006: ID 046d:c24d Logitech, Inc. G710 Gaming Keyboard
Bus 003 Device 004: ID 046d:c07d Logitech, Inc. 
Bus 003 Device 005: ID 045e:028e Microsoft Corp. Xbox360 Controller
Bus 003 Device 003: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 003 Device 002: ID 046d:0a15 Logitech, Inc. 
Bus 003 Device 012: ID 8087:07dc Intel Corp. 
Bus 003 Device 021: ID 22d9:0416  
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
wellywu@ZareasonZeto:~$
```

I performed a clean installation of Ubuntu 16.04.0 64 bit LTS GNU/Linux on my mid-2015 Zareason Zeto desktop PC system. I own an Oppo Digital HA-1 which is connected directly to my desktop PC using a USB 2.0 High Speed cable. I can not see my Oppo Digital HA-1 desktop DAC in my Sound devices. For some unknown reason, my desktop DAC says that it is in DSD 12.288 MHz mode and it seems to be stuck there. Can someone help me to figure out what is going on here? Thank you.

I found this, but I need to know what it is before I try something I don't fully understand:

[http://lkml.iu.edu/hypermail/linux/kernel/1602.1/05498.html](http://lkml.iu.edu/hypermail/linux/kernel/1602.1/05498.html)

Please take a look into this and let me know what is going on here. Thank you.

I also found this:

[https://lkml.org/lkml/2016/1/27/590](https://lkml.org/lkml/2016/1/27/590)

wellywu@ZareasonZeto:~$ uname -r
4.4.0-24-generic

It seems that Linux Kernel 4.4.0-24-generic AMD64 is buggy with regard to my Oppo Digital HA-1. Linux kernel 4.4.1 should fix it. I am wondering when Canonical, Ltd. is going to push out that patch?

[URL="https://wiki.ubuntu.com/KernelTeam/Newsletter"]https://wiki.ubuntu.com/KernelTeam/Newsletter

Now, I am confused: [/URL][http://news.softpedia.com/news/ubuntu-16-04-lts-is-now-using-the-latest-linux-kernel-4-4-1-500201.shtml](http://news.softpedia.com/news/ubuntu-16-04-lts-is-now-using-the-latest-linux-kernel-4-4-1-500201.shtml)

According to this Softpedia article, Canonical, Ltd. is already using Linux kernel 4.4.1 AMD64, but they named it Linux kernel 4.4.0 AMD64.

Can someone please help me to look into this problem? I can not select my Oppo Digital HA-1 desktop DAC and headphone amplifier within the sound devices panel and I can not get audio or sound from it. I don't fully understand this problem and I need help.

According to this LWN.Net post, Linux kernel 4.4.2 fixes the Oppo Digital HA-1 vendor ID: [https://lwn.net/Articles/676136/](https://lwn.net/Articles/676136/). So, can someone please explain to me what this means and when it is coming to Ubuntu 16.04.x?

I found this article as well: [https://github.com/lintweaker/xmos-native-dsd/issues/5](https://github.com/lintweaker/xmos-native-dsd/issues/5). It seems that adding native DSD support to the Oppo Digital HA-1 is a work in progress. At this point, I can't make heads or tails about when this is going to get fixed.

Here is yet more information from the Linux kernel team about Linux kernel 4.4.2: [https://www.kernel.org/pub/linux/kernel/v4.x/ChangeLog-4.4.2](https://www.kernel.org/pub/linux/kernel/v4.x/ChangeLog-4.4.2). It seems that Oppo Digital is using the XMOS chipset, but their own vendor ID. Linux kernel 4.4.1 which is the same as Ubuntu Linux kernel 4.4.0 uses the wrong vendor ID. It seems that I need to upgrade to Linux kernel 4.4.2 AMD64 with the correct Oppo vendor ID. Unless I am missing something.

According to this Github post, Linux kernel 4.5 will support the Oppo Digital HA-1 using the XMOS chipset and their own unique vendor ID. I may be reading the wrong information. I got up early this morning.

update:

I went to Kernel.org and I downloaded and installed the latest Ubuntu Xenial Xerus and Yakkety Yak Linux kernels separately which are at 4.4.13 AMD64 for Xenial and 4.6.2 for Yakkety. After restarting my desktop PC, I still can not see or use my Oppo Digital HA-1 desktop DAC or headphone amplifier. I am at a complete loss as how to understand this problem further. I would appreciate help at this point.

---

### Post by Welly Wu on 2016-06-17
This is my most recent information about my sound devices on my desktop PC:

```
wellywu@ZareasonZeto:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Headset [Logitech G35 Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 4: DAC [OPPO HA-1 USB AUDIO 2.0 DAC], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
wellywu@ZareasonZeto:~$ lsusb
Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 004: ID 05e3:0616 Genesys Logic, Inc. hub
Bus 004 Device 003: ID 174c:55aa ASMedia Technology Inc. ASM1051E SATA 6Gb/s bridge, ASM1053E SATA 6Gb/s bridge, ASM1153 SATA 3Gb/s bridge
Bus 004 Device 002: ID 0bc2:ab2a Seagate RSS LLC 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 007: ID 046d:082d Logitech, Inc. HD Pro Webcam C920
Bus 003 Device 006: ID 046d:c24d Logitech, Inc. G710 Gaming Keyboard
Bus 003 Device 004: ID 046d:c07d Logitech, Inc. 
Bus 003 Device 005: ID 045e:028e Microsoft Corp. Xbox360 Controller
Bus 003 Device 003: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 003 Device 002: ID 046d:0a15 Logitech, Inc. 
Bus 003 Device 012: ID 8087:07dc Intel Corp. 
Bus 003 Device 017: ID 22d9:0416  
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
wellywu@ZareasonZeto:~$ find /lib/modules/'uname-r' | grep snd
find: ‘/lib/modules/uname-r’: No such file or directory
wellywu@ZareasonZeto:~$ find /lib/modules/'uname -r' | grep snd
find: ‘/lib/modules/uname -r’: No such file or directory
wellywu@ZareasonZeto:~$ lspci -v | grep -A7 -i "audio"
00:1b.0 Audio device: Intel Corporation 9 Series Chipset Family HD Audio Controller
    Subsystem: Gigabyte Technology Co., Ltd 9 Series Chipset Family HD Audio Controller
    Flags: bus master, fast devsel, latency 0, IRQ 31
    Memory at f7330000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 1 (rev d0) (prog-if 00 [Normal decode])
--
01:00.1 Audio device: NVIDIA Corporation Device 0fb0 (rev a1)
    Subsystem: eVga.com. Corp. Device 2992
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f7080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

wellywu@ZareasonZeto:~$
```

I contacted both Oppo Digital and Zareason for more help and technical support. It seems like the logical things to do at this point. I will wait for their replies via e-mail.

---

### Post by Welly Wu on 2016-06-18
Does anyone here know how to download Linux kernel 4.6.2 and include the Oppo Digital HA-1 patch?

---

### Post by jeremy31 on 2016-06-18
[http://lkml.iu.edu/hypermail/linux/kernel/1602.1/05498.html](http://lkml.iu.edu/hypermail/linux/kernel/1602.1/05498.html) has already been added to the Ubuntu 4.4.0 kernel.  I just checked the source code

I would do a search for the device ID ```
NVIDIA Corporation Device 0fb0 (rev a1)
```
And see what can be found

---

### Post by Welly Wu on 2016-06-18
Look, forgive me because I overslept last night and I am a bit tired this morning.

How do I do a device ID lookup for the nVidia GPU?

At this point, Zareason told me to downgrade to Ubuntu 14.04.4 64 bit LTS because everything worked. I don't want to do that, but I will if I am forced to do so.

Why do you want me to do a device ID lookup for the nVidia GPU? What information can be learned?

What should I do? I know that the Oppo Digital HA-1 patch has already been included in Ubuntu Linux kernel 4.4.0, but why I can't I select it under sound devices?

I think that I will wait for replies before changing my desktop OS again.

```
wellywu@ZareasonZeto:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd 4th Gen Core Processor DRAM Controller
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: hsw_uncore

00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 25
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: f6000000-f70fffff
    Prefetchable memory behind bridge: 00000000e0000000-00000000f1ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:14.0 USB controller: Intel Corporation 9 Series Chipset Family USB xHCI Controller (prog-if 30 [XHCI])
    Subsystem: Gigabyte Technology Co., Ltd 9 Series Chipset Family USB xHCI Controller
    Flags: bus master, medium devsel, latency 0, IRQ 26
    Memory at f7320000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation 9 Series Chipset Family ME Interface #1
    Subsystem: Gigabyte Technology Co., Ltd 9 Series Chipset Family ME Interface
    Flags: bus master, fast devsel, latency 0, IRQ 30
    Memory at f7339000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: mei_me
    Kernel modules: mei_me

00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-V
    DeviceName:  Onboard LAN
    Subsystem: Gigabyte Technology Co., Ltd Ethernet Connection I217-V
    Flags: bus master, fast devsel, latency 0, IRQ 29
    Memory at f7300000 (32-bit, non-prefetchable) [size=128K]
    Memory at f7338000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at f040 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: e1000e
    Kernel modules: e1000e

00:1a.0 USB controller: Intel Corporation 9 Series Chipset Family USB EHCI Controller #2 (prog-if 20 [EHCI])
    Subsystem: Gigabyte Technology Co., Ltd 9 Series Chipset Family USB EHCI Controller
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f7337000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1b.0 Audio device: Intel Corporation 9 Series Chipset Family HD Audio Controller
    Subsystem: Gigabyte Technology Co., Ltd 9 Series Chipset Family HD Audio Controller
    Flags: bus master, fast devsel, latency 0, IRQ 31
    Memory at f7330000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 1 (rev d0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 4 (rev d0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: f7200000-f72fffff
    Prefetchable memory behind bridge: 00000000f2100000-00000000f21fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 5 (rev d0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    Memory behind bridge: f7100000-f71fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 9 Series Chipset Family USB EHCI Controller #1 (prog-if 20 [EHCI])
    Subsystem: Gigabyte Technology Co., Ltd 9 Series Chipset Family USB EHCI Controller
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f7336000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1f.0 ISA bridge: Intel Corporation 9 Series Chipset Family H97 Controller
    Subsystem: Gigabyte Technology Co., Ltd 9 Series Chipset Family H97 Controller
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich

00:1f.2 SATA controller: Intel Corporation 9 Series Chipset Family SATA Controller [AHCI Mode] (prog-if 01 [AHCI 1.0])
    Subsystem: Gigabyte Technology Co., Ltd 9 Series Chipset Family SATA Controller [AHCI Mode]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 27
    I/O ports at f090 [size=8]
    I/O ports at f080 [size=4]
    I/O ports at f070 [size=8]
    I/O ports at f060 [size=4]
    I/O ports at f020 [size=32]
    Memory at f7335000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 9 Series Chipset Family SMBus Controller
    Subsystem: Gigabyte Technology Co., Ltd 9 Series Chipset Family SMBus Controller
    Flags: medium devsel, IRQ 11
    Memory at f7334000 (64-bit, non-prefetchable) [disabled] [size=256]
    I/O ports at f000 [size=32]
    Kernel modules: i2c_i801

01:00.0 VGA compatible controller: NVIDIA Corporation GM200 [GeForce GTX TITAN X] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: eVga.com. Corp. GM200 [GeForce GTX TITAN X]
    Flags: bus master, fast devsel, latency 0, IRQ 33
    Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    [virtual] Expansion ROM at f7000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_367, nvidia_367_drm

01:00.1 Audio device: NVIDIA Corporation Device 0fb0 (rev a1)
    Subsystem: eVga.com. Corp. Device 2992
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f7080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard
    Flags: bus master, fast devsel, latency 0, IRQ 28
    I/O ports at d000 [size=256]
    Memory at f7200000 (64-bit, non-prefetchable) [size=4K]
    Memory at f2100000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

04:00.0 Network controller: Intel Corporation Wireless 7260 (rev bb)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260
    Flags: bus master, fast devsel, latency 0, IRQ 32
    Memory at f7100000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

wellywu@ZareasonZeto:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 4th Gen Core Processor DRAM Controller [8086:0c00] (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd 4th Gen Core Processor DRAM Controller [1458:5000]
    Kernel driver in use: hsw_uncore
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller [8086:0c01] (rev 06)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:14.0 USB controller [0c03]: Intel Corporation 9 Series Chipset Family USB xHCI Controller [8086:8cb1]
    Subsystem: Gigabyte Technology Co., Ltd 9 Series Chipset Family USB xHCI Controller [1458:5007]
    Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation 9 Series Chipset Family ME Interface #1 [8086:8cba]
    Subsystem: Gigabyte Technology Co., Ltd 9 Series Chipset Family ME Interface [1458:1c3a]
    Kernel driver in use: mei_me
    Kernel modules: mei_me
00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-V [8086:153b]
    DeviceName:  Onboard LAN
    Subsystem: Gigabyte Technology Co., Ltd Ethernet Connection I217-V [1458:e000]
    Kernel driver in use: e1000e
    Kernel modules: e1000e
00:1a.0 USB controller [0c03]: Intel Corporation 9 Series Chipset Family USB EHCI Controller #2 [8086:8cad]
    Subsystem: Gigabyte Technology Co., Ltd 9 Series Chipset Family USB EHCI Controller [1458:5006]
    Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 9 Series Chipset Family HD Audio Controller [8086:8ca0]
    Subsystem: Gigabyte Technology Co., Ltd 9 Series Chipset Family HD Audio Controller [1458:a182]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 9 Series Chipset Family PCI Express Root Port 1 [8086:8c90] (rev d0)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 9 Series Chipset Family PCI Express Root Port 4 [8086:8c96] (rev d0)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.4 PCI bridge [0604]: Intel Corporation 9 Series Chipset Family PCI Express Root Port 5 [8086:8c98] (rev d0)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 9 Series Chipset Family USB EHCI Controller #1 [8086:8ca6]
    Subsystem: Gigabyte Technology Co., Ltd 9 Series Chipset Family USB EHCI Controller [1458:5006]
    Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation 9 Series Chipset Family H97 Controller [8086:8cc6]
    Subsystem: Gigabyte Technology Co., Ltd 9 Series Chipset Family H97 Controller [1458:5001]
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 9 Series Chipset Family SATA Controller [AHCI Mode] [8086:8c82]
    Subsystem: Gigabyte Technology Co., Ltd 9 Series Chipset Family SATA Controller [AHCI Mode] [1458:b005]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 9 Series Chipset Family SMBus Controller [8086:8ca2]
    Subsystem: Gigabyte Technology Co., Ltd 9 Series Chipset Family SMBus Controller [1458:5001]
    Kernel modules: i2c_i801
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GM200 [GeForce GTX TITAN X] [10de:17c2] (rev a1)
    Subsystem: eVga.com. Corp. GM200 [GeForce GTX TITAN X] [3842:2992]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_367, nvidia_367_drm
01:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:0fb0] (rev a1)
    Subsystem: eVga.com. Corp. Device [3842:2992]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169
    Kernel modules: r8169
04:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev bb)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4070]
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi
wellywu@ZareasonZeto:~$ lspci -vmmnn
Slot:    00:00.0
Class:    Host bridge [0600]
Vendor:    Intel Corporation [8086]
Device:    4th Gen Core Processor DRAM Controller [0c00]
SVendor:    Gigabyte Technology Co., Ltd [1458]
SDevice:    4th Gen Core Processor DRAM Controller [5000]
Rev:    06

Slot:    00:01.0
Class:    PCI bridge [0604]
Vendor:    Intel Corporation [8086]
Device:    Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller [0c01]
Rev:    06

Slot:    00:14.0
Class:    USB controller [0c03]
Vendor:    Intel Corporation [8086]
Device:    9 Series Chipset Family USB xHCI Controller [8cb1]
SVendor:    Gigabyte Technology Co., Ltd [1458]
SDevice:    9 Series Chipset Family USB xHCI Controller [5007]
ProgIf:    30

Slot:    00:16.0
Class:    Communication controller [0780]
Vendor:    Intel Corporation [8086]
Device:    9 Series Chipset Family ME Interface #1 [8cba]
SVendor:    Gigabyte Technology Co., Ltd [1458]
SDevice:    9 Series Chipset Family ME Interface [1c3a]

Slot:    00:19.0
Class:    Ethernet controller [0200]
Vendor:    Intel Corporation [8086]
Device:    Ethernet Connection I217-V [153b]
SVendor:    Gigabyte Technology Co., Ltd [1458]
SDevice:    Ethernet Connection I217-V [e000]

Slot:    00:1a.0
Class:    USB controller [0c03]
Vendor:    Intel Corporation [8086]
Device:    9 Series Chipset Family USB EHCI Controller #2 [8cad]
SVendor:    Gigabyte Technology Co., Ltd [1458]
SDevice:    9 Series Chipset Family USB EHCI Controller [5006]
ProgIf:    20

Slot:    00:1b.0
Class:    Audio device [0403]
Vendor:    Intel Corporation [8086]
Device:    9 Series Chipset Family HD Audio Controller [8ca0]
SVendor:    Gigabyte Technology Co., Ltd [1458]
SDevice:    9 Series Chipset Family HD Audio Controller [a182]

Slot:    00:1c.0
Class:    PCI bridge [0604]
Vendor:    Intel Corporation [8086]
Device:    9 Series Chipset Family PCI Express Root Port 1 [8c90]
Rev:    d0

Slot:    00:1c.3
Class:    PCI bridge [0604]
Vendor:    Intel Corporation [8086]
Device:    9 Series Chipset Family PCI Express Root Port 4 [8c96]
Rev:    d0

Slot:    00:1c.4
Class:    PCI bridge [0604]
Vendor:    Intel Corporation [8086]
Device:    9 Series Chipset Family PCI Express Root Port 5 [8c98]
Rev:    d0

Slot:    00:1d.0
Class:    USB controller [0c03]
Vendor:    Intel Corporation [8086]
Device:    9 Series Chipset Family USB EHCI Controller #1 [8ca6]
SVendor:    Gigabyte Technology Co., Ltd [1458]
SDevice:    9 Series Chipset Family USB EHCI Controller [5006]
ProgIf:    20

Slot:    00:1f.0
Class:    ISA bridge [0601]
Vendor:    Intel Corporation [8086]
Device:    9 Series Chipset Family H97 Controller [8cc6]
SVendor:    Gigabyte Technology Co., Ltd [1458]
SDevice:    9 Series Chipset Family H97 Controller [5001]

Slot:    00:1f.2
Class:    SATA controller [0106]
Vendor:    Intel Corporation [8086]
Device:    9 Series Chipset Family SATA Controller [AHCI Mode] [8c82]
SVendor:    Gigabyte Technology Co., Ltd [1458]
SDevice:    9 Series Chipset Family SATA Controller [AHCI Mode] [b005]
ProgIf:    01

Slot:    00:1f.3
Class:    SMBus [0c05]
Vendor:    Intel Corporation [8086]
Device:    9 Series Chipset Family SMBus Controller [8ca2]
SVendor:    Gigabyte Technology Co., Ltd [1458]
SDevice:    9 Series Chipset Family SMBus Controller [5001]

Slot:    01:00.0
Class:    VGA compatible controller [0300]
Vendor:    NVIDIA Corporation [10de]
Device:    GM200 [GeForce GTX TITAN X] [17c2]
SVendor:    eVga.com. Corp. [3842]
SDevice:    GM200 [GeForce GTX TITAN X] [2992]
Rev:    a1

Slot:    01:00.1
Class:    Audio device [0403]
Vendor:    NVIDIA Corporation [10de]
Device:    Device [0fb0]
SVendor:    eVga.com. Corp. [3842]
SDevice:    Device [2992]
Rev:    a1

Slot:    03:00.0
Class:    Ethernet controller [0200]
Vendor:    Realtek Semiconductor Co., Ltd. [10ec]
Device:    RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [8168]
SVendor:    Gigabyte Technology Co., Ltd [1458]
SDevice:    Motherboard [e000]
Rev:    0c

Slot:    04:00.0
Class:    Network controller [0280]
Vendor:    Intel Corporation [8086]
Device:    Wireless 7260 [08b1]
SVendor:    Intel Corporation [8086]
SDevice:    Dual Band Wireless-AC 7260 [4070]
Rev:    bb

wellywu@ZareasonZeto:~$
```

---

### Post by jeremy31 on 2016-06-18
It may be an issue with alsa and not a kernel issue, see [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Please use code tags when posting terminal output, see the link in my signature

---

### Post by Welly Wu on 2016-06-18
I looked at that Ubuntu Sound Troubleshooting guide and I am not prepared to go through with it step-by-step.

I wanted to ask a question. Zareason told me to downgrade to Ubuntu 14.04.4 64 bit LTS because everything worked. I am considering to do just that. However, I like Ubuntu 16.04.0 64 bit LTS.

Rather than ask which version should I use, I would like to know what exactly is going on here? Why can't I select and use my Oppo Digital HA-1? I am concerned that Ubuntu 14.04.5 64 bit LTS will break compatibility with my Oppo Digital HA-1 if it upgrades to Ubuntu Linux kernel 4.4.0.

What are my other options here?

---

### Post by jeremy31 on 2016-06-18
Try one thing before going back to 14.04
```
wget https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+files/oem-audio-hda-daily-dkms_0.201606180501~ubuntu16.04.1_all.deb
sudo dpkg -i oem-audio-hda-daily-dkms_0.201606180501~ubuntu16.04.1_all.deb
```

Reboot and see if it fixes

If you install 14.04.4 it will not upgrade by itself to 14.04.5.  I think it can only be done through terminal but there is likely another way.  I would usually suggest filing a bug report but I think that they would also have you do the sound troubleshooting

---

### Post by Welly Wu on 2016-06-18
I downgraded to Ubuntu 14.04.4 64 bit LTS GNU/Linux on my mid-2015 Zareason Zeto desktop PC system.

I will check for the next 14.04.x 64 bit LTS Hardware Enablement Stack and see if it causes USB 2.0 audio problems or more problems for my Oppo Digital HA-1 desktop DAC and headphone amplifier.

I can now select it and listen to audio, music, and sound. It is fixed for now.

I miss Ubuntu 16.04.0 64 bit LTS GNU/Linux, but I still own my Sager NP8657 [Clevo P650-RE3] gaming laptop and it has the latest Ubuntu version. I like it on my gaming laptop because Linux kernel 4.4.x 64 bit has better support for Intel 6th Generation "Skylake" CPUs.

---

### Post by Welly Wu on 2016-06-19
[https://bugs.launchpad.net/ubuntu/+source/fwupd/+bug/1574079](https://bugs.launchpad.net/ubuntu/+source/fwupd/+bug/1574079)

I got the fix working.

If you are using Ubuntu 16.04.0 64 bit LTS, then enable xenial-proposed in developer options under the system settings -> Software & Updates -> Developer Options. Do a sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade. Make sure to unplug and reset your USB 2.0 DAC and headphone amplifier back to factory default settings. Unplug the USB 2.0 cable from your PC. After doing the Ubuntu upgrades and dist-upgrade, shut down your PC. Boot it back up. Log into your Ubuntu Administrator account. Plug in your USB 2.0 DAC. Find it under sound devices and select it. Test the audio with the left and right channel. Play an audio file. It works with my Oppo Digital HA-1 and Chord Mojo now. It is fixed.

---

