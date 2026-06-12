---
title: "PC performing like a pig"
date: 2016-01-06
forum: General Help
---

### Post by Jonners59 on 2016-01-06
Sorry about the description, but it really is.  It is so, so very slow.  It does not always shut down or boot properly.  SOmetimes even watch the screen build!!!

Does anyone know what might be wrong with my baby, please!?!?!?

```
[COLOR=#111111][FONT=Consolas]uname-a
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]Linuxbaronipc 4.2.0-18-generic #22-Ubuntu SMP Fri Nov 6 18:25:50 UTC 2015x86_64 x86_64 x86_64 GNU/Linux[/FONT][/COLOR]
```

```
lspci -v00:00.0 Host bridge:Intel Corporation 2nd Generation Core Processor Family DRAMController (rev 09)
	Subsystem: ASUSTeKComputer Inc. P8P67/P8H67 Series Motherboard
	Flags: bus master,fast devsel, latency 0
	Capabilities:<access denied>
	Kernel driver inuse: snb_uncore


00:01.0 PCI bridge:Intel Corporation Xeon E3-1200/2nd Generation Core Processor FamilyPCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
	Flags: bus master,fast devsel, latency 0, IRQ 24
	Bus: primary=00,secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge:0000e000-0000efff
	Memory behindbridge: fa000000-fb0fffff
	Prefetchable memorybehind bridge: 00000000c0000000-00000000d1ffffff
	Capabilities:<access denied>
	Kernel driver inuse: pcieport


00:16.0Communication controller: Intel Corporation 6 Series/C200 SeriesChipset Family MEI Controller #1 (rev 04)
	Subsystem: ASUSTeKComputer Inc. P8 series motherboard
	Flags: bus master,fast devsel, latency 0, IRQ 40
	Memory at fb408000(64-bit, non-prefetchable) [size=16]
	Capabilities:<access denied>
	Kernel driver inuse: mei_me


00:1a.0 USBcontroller: Intel Corporation 6 Series/C200 Series Chipset Family USBEnhanced Host Controller #2 (rev 05) (prog-if 20 [EHCI])
	Subsystem: ASUSTeKComputer Inc. P8 series motherboard
	Flags: bus master,medium devsel, latency 0, IRQ 23
	Memory at fb407000(32-bit, non-prefetchable) [size=1K]
	Capabilities:<access denied>
	Kernel driver inuse: ehci-pci


00:1b.0 Audiodevice: Intel Corporation 6 Series/C200 Series Chipset Family HighDefinition Audio Controller (rev 05)
	Subsystem: ASUSTeKComputer Inc. Device 8469
	Flags: bus master,fast devsel, latency 0, IRQ 41
	Memory at fb400000(64-bit, non-prefetchable) [size=16K]
	Capabilities:<access denied>
	Kernel driver inuse: snd_hda_intel


00:1c.0 PCI bridge:Intel Corporation 6 Series/C200 Series Chipset Family PCI ExpressRoot Port 1 (rev b5) (prog-if 00 [Normal decode])
	Flags: bus master,fast devsel, latency 0, IRQ 25
	Bus: primary=00,secondary=02, subordinate=02, sec-latency=0
	Capabilities:<access denied>
	Kernel driver inuse: pcieport


00:1c.2 PCI bridge:Intel Corporation 6 Series/C200 Series Chipset Family PCI ExpressRoot Port 3 (rev b5) (prog-if 00 [Normal decode])
	Flags: bus master,fast devsel, latency 0, IRQ 26
	Bus: primary=00,secondary=03, subordinate=03, sec-latency=0
	Capabilities:<access denied>
	Kernel driver inuse: pcieport


00:1c.3 PCI bridge:Intel Corporation 6 Series/C200 Series Chipset Family PCI ExpressRoot Port 4 (rev b5) (prog-if 00 [Normal decode])
	Flags: bus master,fast devsel, latency 0, IRQ 27
	Bus: primary=00,secondary=04, subordinate=04, sec-latency=0
	Capabilities:<access denied>
	Kernel driver inuse: pcieport


00:1c.4 PCI bridge:Intel Corporation 6 Series/C200 Series Chipset Family PCI ExpressRoot Port 5 (rev b5) (prog-if 00 [Normal decode])
	Flags: bus master,fast devsel, latency 0, IRQ 28
	Bus: primary=00,secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge:0000d000-0000dfff
	Memory behindbridge: fb300000-fb3fffff
	Capabilities:<access denied>
	Kernel driver inuse: pcieport


00:1c.5 PCI bridge:Intel Corporation 6 Series/C200 Series Chipset Family PCI ExpressRoot Port 6 (rev b5) (prog-if 00 [Normal decode])
	Flags: bus master,fast devsel, latency 0, IRQ 29
	Bus: primary=00,secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge:0000c000-0000cfff
	Prefetchable memorybehind bridge: 00000000d2100000-00000000d21fffff
	Capabilities:<access denied>
	Kernel driver inuse: pcieport


00:1c.6 PCI bridge:Intel Corporation 6 Series/C200 Series Chipset Family PCI ExpressRoot Port 7 (rev b5) (prog-if 00 [Normal decode])
	Flags: bus master,fast devsel, latency 0, IRQ 30
	Bus: primary=00,secondary=07, subordinate=07, sec-latency=0
	I/O behind bridge:0000b000-0000bfff
	Memory behindbridge: fb200000-fb2fffff
	Capabilities:<access denied>
	Kernel driver inuse: pcieport


00:1c.7 PCI bridge:Intel Corporation 6 Series/C200 Series Chipset Family PCI ExpressRoot Port 8 (rev b5) (prog-if 00 [Normal decode])
	Flags: bus master,fast devsel, latency 0, IRQ 31
	Bus: primary=00,secondary=08, subordinate=08, sec-latency=0
	Memory behindbridge: fb100000-fb1fffff
	Capabilities:<access denied>
	Kernel driver inuse: pcieport


00:1d.0 USBcontroller: Intel Corporation 6 Series/C200 Series Chipset Family USBEnhanced Host Controller #1 (rev 05) (prog-if 20 [EHCI])
	Subsystem: ASUSTeKComputer Inc. P8 series motherboard
	Flags: bus master,medium devsel, latency 0, IRQ 23
	Memory at fb406000(32-bit, non-prefetchable) [size=1K]
	Capabilities:<access denied>
	Kernel driver inuse: ehci-pci


00:1f.0 ISA bridge:Intel Corporation P67 Express Chipset Family LPC Controller (rev 05)
	Subsystem: ASUSTeKComputer Inc. P8P67 Deluxe Motherboard
	Flags: bus master,medium devsel, latency 0
	Capabilities:<access denied>
	Kernel driver inuse: lpc_ich


00:1f.2 SATAcontroller: Intel Corporation 6 Series/C200 Series Chipset FamilySATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
	Subsystem: ASUSTeKComputer Inc. P8 series motherboard
	Flags: bus master,66MHz, medium devsel, latency 0, IRQ 38
	I/O ports at f070[size=8]
	I/O ports at f060[size=4]
	I/O ports at f050[size=8]
	I/O ports at f040[size=4]
	I/O ports at f020[size=32]
	Memory at fb405000(32-bit, non-prefetchable) [size=2K]
	Capabilities:<access denied>
	Kernel driver inuse: ahci


00:1f.3 SMBus: IntelCorporation 6 Series/C200 Series Chipset Family SMBus Controller (rev05)
	Subsystem: ASUSTeKComputer Inc. P8 series motherboard
	Flags: mediumdevsel, IRQ 10
	Memory at fb404000(64-bit, non-prefetchable) [size=256]
	I/O ports at f000[size=32]


01:00.0 VGAcompatible controller: NVIDIA Corporation GK107 [GeForce GTX 650](rev a1) (prog-if 00 [VGA controller])
	Subsystem: GigabyteTechnology Co., Ltd Device 362b
	Flags: bus master,fast devsel, latency 0, IRQ 42
	Memory at fa000000(32-bit, non-prefetchable) [size=16M]
	Memory at c0000000(64-bit, prefetchable) [size=256M]
	Memory at d0000000(64-bit, prefetchable) [size=32M]
	I/O ports at e000[size=128]
	[virtual] ExpansionROM at fb000000 [disabled] [size=512K]
	Capabilities:<access denied>
	Kernel driver inuse: nvidia


01:00.1 Audiodevice: NVIDIA Corporation GK107 HDMI Audio Controller (rev a1)
	Subsystem: GigabyteTechnology Co., Ltd Device 362b
	Flags: bus master,fast devsel, latency 0, IRQ 17
	Memory at fb080000(32-bit, non-prefetchable) [size=16K]
	Capabilities:<access denied>
	Kernel driver inuse: snd_hda_intel


05:00.0 FireWire(IEEE 1394): VIA Technologies, Inc. VT6315 Series Firewire Controller(rev 01) (prog-if 10 [OHCI])
	Subsystem: ASUSTeKComputer Inc. P8P67 Deluxe Motherboard
	Flags: bus master,fast devsel, latency 0, IRQ 16
	Memory at fb300000(64-bit, non-prefetchable) [size=2K]
	I/O ports at d000[size=256]
	Capabilities:<access denied>
	Kernel driver inuse: firewire_ohci


06:00.0 Ethernetcontroller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCIExpress Gigabit Ethernet Controller (rev 06)
	Subsystem: ASUSTeKComputer Inc. P8P67 and other motherboards
	Flags: bus master,fast devsel, latency 0, IRQ 37
	I/O ports at c000[size=256]
	Memory at d2104000(64-bit, prefetchable) [size=4K]
	Memory at d2100000(64-bit, prefetchable) [size=16K]
	Capabilities:<access denied>
	Kernel driver inuse: r8169


07:00.0 IDEinterface: Marvell Technology Group Ltd. 88SE912x SATA 6Gb/sController [IDE mode] (rev 12) (prog-if 8f [Master SecP SecO PriPPriO])
	Subsystem: ASUSTeKComputer Inc. Device 83ba
	Flags: bus master,fast devsel, latency 0, IRQ 39
	I/O ports at b090[size=8]
	I/O ports at b080[size=4]
	I/O ports at b070[size=8]
	I/O ports at b060[size=4]
	I/O ports at b050[size=16]
	Memory at fb215000(32-bit, non-prefetchable) [size=2K]
	Expansion ROM atfb200000 [disabled] [size=64K]
	Capabilities:<access denied>
	Kernel driver inuse: ahci


08:00.0 USBcontroller: ASMedia Technology Inc. ASM1042 SuperSpeed USB HostController (prog-if 30 [XHCI])
	Subsystem: ASUSTeKComputer Inc. P8B WS Motherboard
	Flags: bus master,fast devsel, latency 0, IRQ 19
	Memory at fb100000(64-bit, non-prefetchable) [size=32K]
	Capabilities:<access denied>
	Kernel driver inuse: xhci_hcd
```




```
sudo fdisk -l
[sudo] password forbaronipc: 
Disk /dev/ram0: 64MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1* 512 = 512 bytes
Sector size(logical/physical): 512 bytes / 4096 bytes
I/O size(minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram1: 64MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1* 512 = 512 bytes
Sector size(logical/physical): 512 bytes / 4096 bytes
I/O size(minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram2: 64MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1* 512 = 512 bytes
Sector size(logical/physical): 512 bytes / 4096 bytes
I/O size(minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram3: 64MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1* 512 = 512 bytes
Sector size(logical/physical): 512 bytes / 4096 bytes
I/O size(minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram4: 64MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1* 512 = 512 bytes
Sector size(logical/physical): 512 bytes / 4096 bytes
I/O size(minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram5: 64MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1* 512 = 512 bytes
Sector size(logical/physical): 512 bytes / 4096 bytes
I/O size(minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram6: 64MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1* 512 = 512 bytes
Sector size(logical/physical): 512 bytes / 4096 bytes
I/O size(minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram7: 64MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1* 512 = 512 bytes
Sector size(logical/physical): 512 bytes / 4096 bytes
I/O size(minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram8: 64MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1* 512 = 512 bytes
Sector size(logical/physical): 512 bytes / 4096 bytes
I/O size(minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram9: 64MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1* 512 = 512 bytes
Sector size(logical/physical): 512 bytes / 4096 bytes
I/O size(minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram10: 64MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1* 512 = 512 bytes
Sector size(logical/physical): 512 bytes / 4096 bytes
I/O size(minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram11: 64MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1* 512 = 512 bytes
Sector size(logical/physical): 512 bytes / 4096 bytes
I/O size(minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram12: 64MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1* 512 = 512 bytes
Sector size(logical/physical): 512 bytes / 4096 bytes
I/O size(minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram13: 64MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1* 512 = 512 bytes
Sector size(logical/physical): 512 bytes / 4096 bytes
I/O size(minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram14: 64MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1* 512 = 512 bytes
Sector size(logical/physical): 512 bytes / 4096 bytes
I/O size(minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram15: 64MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1* 512 = 512 bytes
Sector size(logical/physical): 512 bytes / 4096 bytes
I/O size(minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/sda: 465.8GiB, 500106780160 bytes, 976771055 sectors
Units: sectors of 1* 512 = 512 bytes
Sector size(logical/physical): 512 bytes / 512 bytes
I/O size(minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier:0x0009f620


Device     Boot    Start       End   Sectors   Size Id Type
/dev/sda1             63  78116863  78116801  37.3G 83 Linux
/dev/sda3       78116864 771809279 693692416 330.8G  7 HPFS/NTFS/exFAT
/dev/sda4      771813374 976766500 204953127  97.7G  5 Extended
/dev/sda5  *   771813376 976766500 204953125  97.7G 83 Linux




Disk /dev/sdb: 232.9GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1* 512 = 512 bytes
Sector size(logical/physical): 512 bytes / 512 bytes
I/O size(minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier:0x000a9a63


Device     Boot    Start       End   Sectors   Size Id Type
/dev/sdb1           2048 307734527 307732480 146.8G  7 HPFS/NTFS/exFAT
/dev/sdb2      402946048 467871743  64925696    31G 83 Linux
/dev/sdb3  *   307734528 402946047  95211520  45.4G 83 Linux
/dev/sdb4      467871744 488390655  20518912   9.8G 82 Linux swap / Solaris


Partition tableentries are not in disk order
```

---

### Post by QDR06VV9 on 2016-01-06
@Jonners59 there seems to be a lot related to the kernel..4.2.0-18-generic
And I am also asumeing here that you are running 15.10
If this is the case then try booting to a older kernel to see if the same happens..

---

### Post by Jonners59 on 2016-01-07
Yes, sorry, [COLOR=#000000]runrickus,[/COLOR] thought with all the muck I put out that it said 15:10....  :-D

OK, so I tried one of the other's and it opened and worked ok, but the screen res was really poor, so I check my settings and found that it was set to default screen res and there were no options to raise above the basics.  I then checked the nVidia manager and there were no options, which is an indication that the driver has not properly installed.  So I have rebooted back in to my 15:10 as it is un usable.

Is it better since the experience, not really, though it does seem a little quicker, but that could just be me wishful thinking, esp as there is no reason for anything to be different.  So other thoughts, please.....

---

### Post by Bucky Ball on 2016-01-07
*Thread moved to **General Help***.

Do an update and check in Additional Drivers. Anything there for your card?

---

### Post by Jonners59 on 2016-01-07
Hiya.
No, I went back to 15:10....  To sort the nVidia is not so straight fwd.  Had to do it a number of times.  Need to purge it and then reboot in to cmd line (or whatever it's called), not terminal and clear everything out, and reinstall, making sig changes to LightDm and the like.  also quite risky.  Any other ideas, why 15:10 runs like a pig and how to fix it....  or are the comments implying 15:10 has an underlying problem?

---

### Post by QDR06VV9 on 2016-01-07
You know I just don't see the problems on Wily(15.10) that most are seeing.
Back in the Development cycle of Wily and still on going to Xenial most are reporting that Graphic Drivers was confusing..
I went with this PPA [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa) and I have not had any issues.
I do however like the Nvidia 352.63 Driver over the 355. or even 358.series, just my 2 cents worth
My Card is 
> $ inxi -G
Graphics:  Card: NVIDIA GF119 [GeForce GT 520]
           Display Server: X.Org 1.17.4 driver: nvidia
           Resolution: 1920x1080@60.00hz
           GLX Renderer: GeForce GT 520/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 352.63

**EDIT: **You know I always forget to mention that I also Always run a Low latency kernel.

---

### Post by Yellow Pasque on 2016-01-07
Have you investigated what processes are using the CPU when the system is running slow?
```
sudo apt-get install htop
htop
```
Have you checked for a memory leak when the system is running slow?:
```
free -m
```

---

### Post by Jonners59 on 2016-01-14
> **Temüjin said:**
> Have you investigated what processes are using the CPU when the system is running slow?
```
sudo apt-get install htop
htop
```
Have you checked for a memory leak when the system is running slow?:
```
free -m
```

Sorry for taking so long to get back.....  Been one thing after another.

That doesn't help me as I do not know what I am looking for or then hopw to deal with it if I did.

I have tried to copy the text FYI below.
```


  1  [||||||||||||||||||||||||||||||||||||||||||||||    82.4%]     Tasks: 298, 1723 thr; 4 running
  2  [||||||||||||||||||||||||||||||||||||||||||||||||||99.5%]     Load average: 10.41 8.82 6.27 
  3  [|||||||||||||||||||||||||||||||||||||||           69.6%]     Uptime: 03:07:11
  4  [||||||||||||||||||||||||||||||||||||||||||||||||||94.3%]
  Mem[||||||||||||||||||||||||||||||||||||||||||11801/16029MB]
  Swp[||||||||||||||||||||||||||||||||||         6176/10018MB]


  PID USER      PRI  NI  VIRT   RES   SHR S CPU% MEM%   TIME+  Command
13943 baronipc   20   0 3410M 2619M 67040 R 106. 16.3 15:49.00 /usr/lib/firefox/plugin-container /usr/lib/mozilla/plugins/libfresh
12976 baronipc   20   0 3592M 2123M 97756 R 98.6 13.3 22:32.44 /usr/lib/firefox/firefox http://www.capitaspecialistrecruitment.co.
27388 baronipc   20   0 1025M  177M 64856 S  8.8  1.1 12:36.05 /opt/google/chrome/chrome --force-device-scale-factor
 5208 baronipc   20   0 1162M 76632 39268 R  7.4  0.5 16:01.24 /usr/lib/chromium-browser/chromium-browser --type=renderer --enable
27488 baronipc   20   0  630M  162M 61176 R  7.0  1.0 10:18.80 /opt/google/chrome/chrome --type=gpu-process --channel=27388.0.1241
13950 baronipc   20   0 3410M 2619M 67040 S  7.0 16.3  3:04.09 /usr/lib/firefox/plugin-container /usr/lib/mozilla/plugins/libfresh
 5033 baronipc   20   0 3945M  764M 30004 S  5.1  4.8  3:55.49 /usr/lib/evolution/evolution-calendar-factory-subprocess --factory
 2475 root       20   0  441M  160M 77292 S  4.7  1.0 13:13.68 /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nol
 3665 root       20   0  360M  9168  5652 S  2.8  0.1  2:37.20 /usr/lib/udisks2/udisksd --no-debug
 3864 baronipc   20   0  595M 40244 11520 R  2.3  0.2  3:50.31 skype %U
 5365 baronipc   20   0 1162M 76632 39268 S  2.3  0.5  3:35.77 /usr/lib/chromium-browser/chromium-browser --type=renderer --enable
29948 baronipc   20   0 3945M  764M 30004 D  1.9  4.8  0:02.14 /usr/lib/evolution/evolution-calendar-factory-subprocess --factory
27484 baronipc   20   0 1025M  177M 64856 S  1.9  1.1  1:52.01 /opt/google/chrome/chrome --force-device-scale-factor
30187 baronipc   20   0 3945M  764M 30004 D  1.9  4.8  0:01.73 /usr/lib/evolution/evolution-calendar-factory-subprocess --factory
29614 baronipc   20   0 3945M  764M 30004 D  1.4  4.8  0:01.66 /usr/lib/evolution/evolution-calendar-factory-subprocess --factory
 3798 baronipc    9 -11 1324M 12136  7068 S  1.4  0.1  2:26.96 /usr/bin/pulseaudio --start --log-target=syslog
  380 baronipc   20   0 35296  5892  2964 R  1.4  0.0  0:01.69 htop
27629 baronipc   20   0  797M 43724 16500 S  0.9  0.3  1:19.73 /opt/google/chrome/chrome --type=renderer --force-device-scale-fact
 3914 baronipc   -6   0 1324M 12136  7068 S  0.9  0.1  1:11.67 /usr/bin/pulseaudio --start --log-target=syslog
 3888 baronipc   20   0 1586M  265M 84784 S  0.9  1.7  2:16.00 chromium-browser --ppapi-flash-path=/usr/lib/pepperflashplugin-nonf
 3550 baronipc   20   0  376M 25052 18444 S  0.5  0.2  0:28.33 xfwm4 --display :0.0 --sm-client-id 2e9512d83-beb8-4f1a-850a-1d06fd
28893 baronipc   20   0 1049M 67748 20964 S  0.5  0.4  0:53.14 /usr/lib/chromium-browser/chromium-browser --type=ppapi --channel=3
27492 baronipc   20   0  630M  162M 61176 S  0.5  1.0  0:40.21 /opt/google/chrome/chrome --type=gpu-process --channel=27388.0.1241
 5026 baronipc   20   0 1586M  265M 84784 S  0.5  1.7  0:44.66 chromium-browser --ppapi-flash-path=/usr/lib/pepperflashplugin-nonf
 1063 messagebu  20   0 45352  5736  3196 S  0.5  0.0  0:26.26 /usr/bin/dbus-daemon --system --address=systemd: --nofork --nopidfi
28201 baronipc   20   0 1535M  178M 33024 S  0.5  1.1  0:15.25 /usr/lib/chromium-browser/chromium-browser --type=renderer --enable
 3668 root       20   0  360M  9168  5652 S  0.5  0.1  0:21.67 /usr/lib/udisks2/udisksd --no-debug
15168 baronipc   20   0 2591M  1716   840 S  0.5  0.0  0:09.09 C:\windows\system32\winedevice.exe MountMgr
 6175 baronipc   20   0 1476M 90712 28472 R  0.5  0.6  0:13.00 /usr/lib/chromium-browser/chromium-browser --type=renderer --enable
15192 baronipc   20   0 2591M  1716   840 S  0.5  0.0  0:09.08 C:\windows\system32\winedevice.exe MountMgr
    1 root       20   0  117M  5364  3112 S  0.5  0.0  0:11.89 /sbin/init splash nomdmonddf nomdmonisw
 1184 syslog     20   0  250M  3760  2368 S  0.5  0.0  1:53.95 /usr/sbin/rsyslogd -n
28224 baronipc   20   0 1168M  113M 31032 S  0.5  0.7  0:09.29 /usr/lib/chromium-browser/chromium-browser --type=renderer --enable
 2175 baronipc   20   0 3945M  764M 30004 S  0.5  4.8  0:00.60 /usr/lib/evolution/evolution-calendar-factory-subprocess --factory
23782 baronipc   20   0 3410M 2619M 67040 S  0.5 16.3  0:00.89 /usr/lib/firefox/plugin-container /usr/lib/mozilla/plugins/libfresh
28095 baronipc   20   0 1237M  127M 31128 S  0.5  0.8  0:08.10 /usr/lib/chromium-browser/chromium-browser --type=renderer --enable
27599 baronipc   20   0  888M  104M 21904 S  0.5  0.6  0:04.94 /opt/google/chrome/chrome --type=renderer --force-device-scale-fact
15837 baronipc   20   0 3592M 2123M 97756 S  0.5 13.3  0:00.31 /usr/lib/firefox/firefox http://www.capitaspecialistrecruitment.co.
28204 baronipc   20   0 1535M  178M 33024 S  0.5  1.1  0:01.26 /usr/lib/chromium-browser/chromium-browser --type=renderer --enable

```

Can you help/decipher it.  Interestingly, Firefox has just started playing up - freezes.  Here I have killed it (xkill) but it still shows it running.  That can't be good either, but it is also new.  This problem started before.


```
free -m
             total       used       free     shared    buffers     cached
Mem:         16029      15916        113       3374         75       3965
-/+ buffers/cache:      11875       4154
Swap:        10018       6148       3870
```

Any help anyone, please?????

---

### Post by Yellow Pasque on 2016-01-14
> That doesn't help me as I do not know what I am looking for
You're going to use htop to look for processes using a lot of CPU when your system runs slow (you can click on 'CPU%' and htop will automatically sort the processes by CPU used for you). In the results you've posted, firefox (specifically Flash/freshplayer) is using a lot of CPU, but if this normally doesn't happen, you should try running htop before using firefox.

The free command shows the memory used. The key line is the middle one, which shows ~12 GB used and ~4GB free in your output. htop shows that the zombie firefox processes are the culprit for the high RAM usage.

Basically, you should try monitoring htop more often to get a better idea of what's loading the system.

---

### Post by QDR06VV9 on 2016-01-14
Has any one filed a bug against this (Firefox) bringing a system to a crawl???
This happens way to much to be just a paper cut..
I do not use firefox so I dunno!
Just Saying.

---

### Post by Jonners59 on 2016-01-23
> **runrickus said:**
> Has any one filed a bug against this (Firefox) bringing a system to a crawl???
This happens way to much to be just a paper cut..
I do not use firefox so I dunno!
Just Saying.
Sorry I missed this.  I logged in by chance, I had no alert.
It and Evolution run my CPUs at over 100% most of the time.  The PC freezes up with it,  Something is VERY, VERY wrong.

---

