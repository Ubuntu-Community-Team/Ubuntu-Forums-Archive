---
title: "sound problems ac97 intel8x0"
date: 2007-09-28
forum: General Help
---

### Post by driectly3d on 2007-09-28
Alright, ive been through the comprehensive sound guide, and tried the realtek audio drivers. Ubuntu is recognizing my sound card:

 lspci -v
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
        Subsystem: nVidia Corporation Unknown device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
        Subsystem: nVidia Corporation Unknown device cb84
        Flags: 66MHz, fast devsel, IRQ 5
        I/O ports at fc00 [size=32]
        I/O ports at 1c00 [size=64]
        I/O ports at 1c40 [size=64]
        Capabilities: <access denied>

00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10 [OHCI])
        Subsystem: nVidia Corporation Unknown device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
        Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3) (prog-if 20 [EHCI])
        Subsystem: nVidia Corporation Unknown device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at feb00000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
        Subsystem: nVidia Corporation Unknown device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
        I/O ports at f000 [size=256]
        I/O ports at ec00 [size=256]
        Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2) (prog-if 8a [Master SecP PriP])
        Subsystem: nVidia Corporation Unknown device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at e800 [size=16]
        Capabilities: <access denied>

00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
        Subsystem: nVidia Corporation Unknown device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        I/O ports at 09f0 [size=8]
        I/O ports at 0bf0 [size=4]
        I/O ports at 0970 [size=8]
        I/O ports at 0b70 [size=4]
        I/O ports at d400 [size=16]
        Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
        Subsystem: nVidia Corporation Unknown device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
        I/O ports at 09e0 [size=8]
        I/O ports at 0be0 [size=4]
        I/O ports at 0960 [size=8]
        I/O ports at 0b60 [size=4]
        I/O ports at c000 [size=16]
        Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 00009000-0000afff
        Memory behind bridge: fde00000-fdefffff
        Prefetchable memory behind bridge: fdf00000-fdffffff

00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
        Subsystem: nVidia Corporation Unknown device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
        Memory at fe02a000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at bc00 [size=8]
        Capabilities: <access denied>

00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00008000-00008fff
        Memory behind bridge: fdd00000-fddfffff
        Prefetchable memory behind bridge: 00000000fdc00000-00000000fdcfffff
        Capabilities: <access denied>

00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 00007000-00007fff
        Memory behind bridge: fdb00000-fdbfffff
        Prefetchable memory behind bridge: 00000000fda00000-00000000fdafffff
        Capabilities: <access denied>

00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 00006000-00006fff
        Memory behind bridge: fa000000-fcffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: <access denied>

00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        I/O behind bridge: 00005000-00005fff
        Memory behind bridge: f7000000-f9ffffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
        Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel

01:08.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
        Subsystem: Silicon Image, Inc. Unknown device 7114
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
        I/O ports at ac00 [size=8]
        I/O ports at a800 [size=4]
        I/O ports at a400 [size=8]
        I/O ports at a000 [size=4]
        I/O ports at 9c00 [size=16]
        Memory at fdeff000 (32-bit, non-prefetchable) [size=1K]
        [virtual] Expansion ROM at fdf00000 [disabled] [size=512K]
        Capabilities: <access denied>

01:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: DFI Inc Unknown device 1006
        Flags: bus master, stepping, medium devsel, latency 32, IRQ 17
        Memory at fdefe000 (32-bit, non-prefetchable) [size=2K]
        I/O ports at 9800 [size=128]
        Capabilities: <access denied>

01:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
        Subsystem: DFI Inc Unknown device 100a
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
        Memory at fdef8000 (32-bit, non-prefetchable) [size=16K]
        I/O ports at 9400 [size=256]
        [virtual] Expansion ROM at fdf80000 [disabled] [size=128K]
        Capabilities: <access denied>

04:00.0 VGA compatible controller: nVidia Corporation NV42 [Geforce 6800 XT] (rev a2) (prog-if 00 [VGA])
        Subsystem: XFX Pine Group Inc. Unknown device 2177
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at fb000000 (64-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at fc000000 [disabled] [size=128K]
        Capabilities: <access denied>

05:00.0 VGA compatible controller: nVidia Corporation NV42 [Geforce 6800 XT] (rev a2) (prog-if 00 [VGA])
        Subsystem: XFX Pine Group Inc. Unknown device 2177
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at f7000000 (32-bit, non-prefetchable) [disabled] [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [disabled] [size=256M]
        Memory at f8000000 (64-bit, non-prefetchable) [disabled] [size=16M]
        [virtual] Expansion ROM at f9000000 [disabled] [size=128K]
        Capabilities: <access denied>




But when I do this:


 lsmod
Module                  Size  Used by
nls_cp437               8192  1 
isofs                  38628  1 
udf                    86664  0 
nfnetlink_queue        15104  1 
binfmt_misc            14604  1 
ppdev                  11272  0 
rfcomm                 45352  0 
l2cap                  28160  5 rfcomm
xt_tcpudp               4992  2 
bluetooth              62468  4 rfcomm,l2cap
nf_conntrack_ipv4      22160  3 
iptable_filter          4480  1 
ip_tables              23080  1 iptable_filter
xt_NFQUEUE              3328  3 
xt_state                3968  3 
nf_conntrack           73180  2 nf_conntrack_ipv4,xt_state
nfnetlink               9160  4 nfnetlink_queue,nf_conntrack_ipv4,nf_conntrack
x_tables               23688  4 xt_tcpudp,ip_tables,xt_NFQUEUE,xt_state
powernow_k8            16480  0 
cpufreq_ondemand       10640  1 
cpufreq_userspace       6176  0 
cpufreq_powersave       3072  0 
cpufreq_stats           8416  0 
freq_table              6336  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     9736  0 
tc1100_wmi              9224  0 
pcc_acpi               15616  0 
sony_acpi               7064  0 
dev_acpi               17028  0 
video                  19080  0 
button                 10016  0 
sbs                    17856  0 
i2c_ec                  6912  1 sbs
dock                   11992  0 
asus_acpi              19756  0 
backlight               8448  1 asus_acpi
battery                12040  0 
container               6144  0 
ac                      6920  0 
ipv6                  307456  10 
fuse                   51888  3 
sbp2                   26628  0 
parport_pc             40104  0 
lp                     15048  0 
parport                43404  3 ppdev,parport_pc,lp
nvidia               5659736  0 
irtty_sir              10752  0 
sir_dev                19336  1 irtty_sir
ide_cd                 35104  1 
cdrom                  40744  1 ide_cd
irda                  217708  2 irtty_sir,sir_dev
pcspkr                  4736  0 
k8temp                  7552  0 
crc_ccitt               3456  1 irda
ide_disk               18304  2 
i2c_nforce2             7680  0 
sk98lin               160352  0 
af_packet              27020  2 
shpchp                 37404  0 
pci_hotplug            36228  1 shpchp
i2c_core               26496  3 i2c_ec,nvidia,i2c_nforce2
tsdev                  10112  0 
evdev                  13056  3 
ext3                  143760  1 
jbd                    68208  1 ext3
mbcache                11400  1 ext3
sg                     40616  0 
sd_mod                 25092  3 
amd74xx                16944  0 [permanent]
generic                 6532  0 [permanent]
ata_generic            10628  0 
usbhid                 29088  0 
hid                    34048  1 usbhid
floppy                 67944  0 
skge                   44432  0 
ohci1394               38088  0 
ieee1394              369784  2 sbp2,ohci1394
sata_sil               15112  0 
forcedeth              48776  0 
sata_nv                24196  2 
libata                137000  3 ata_generic,sata_sil,sata_nv
scsi_mod              166968  4 sbp2,sg,sd_mod,libata
ehci_hcd               37004  0 
ohci_hcd               24196  0 
usbcore               154416  4 usbhid,ehci_hcd,ohci_hcd
thermal                16912  0 
processor              34952  2 powernow_k8,thermal
fan                     6536  0 
fbcon                  44416  0 
tileblit                4096  1 fbcon
font                    9856  1 fbcon
bitblit                 7296  1 fbcon
softcursor              3712  1 bitblit
vesafb                 10376  0 
cfbcopyarea             5120  1 vesafb
cfbimgblt               4096  1 vesafb
cfbfillrect             5632  1 vesafb
capability              7048  0 
commoncap               9472  1 capability




No soundcard module, I have installed, reinstalled, and been up down and through it all. At one point I had it working for about 20 minutes, then everything failed after i rebooted, and ive been unable to duplicate the results.


For some reason I have been having problems with hplip printer support when working with the ubuntu-desktop. Both ubuntu-desktop and alsa drivers see hplip as a dependency?! 

And before you ask, the bios is configured correctly, and i have and have tried reinstalling gstreamer and everything with the word alsa in it


Any suggestions would be greatly appreciated ^^, sorry for the lengthy post

---

### Post by tbroderick on 2007-09-28
Did you try manually loading the modules?

sudo modprobe snd
sudo modprobe snd_intel8x0

---

