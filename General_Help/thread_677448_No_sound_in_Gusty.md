---
title: "No sound in Gusty"
date: 2008-01-24
forum: General Help
---

### Post by kevindubrow on 2008-01-24
Hi, so I guess this issue is nothing new. I have looked at similar posts and have found nothing that has helped. 

I have reinstalled Gusty a few times with no help. Any ideas on how I can fix this? I am running 64bit Ubuntu Studio 7.10. I don't know what information is helpful to someone who is trying to help me with this, so please ask and I will give you any information that is needed. Thanks again.

---

### Post by Mikecore on 2008-01-24
> **kevindubrow said:**
> Hi, so I guess this issue is nothing new. I have looked at similar posts and have found nothing that has helped. 

I have reinstalled Gusty a few times with no help. Any ideas on how I can fix this? I am running 64bit Ubuntu Studio 7.10. I don't know what information is helpful to someone who is trying to help me with this, so please ask and I will give you any information that is needed. Thanks again.

please post the output of ( run in a terminal ) 

```


lspci


```

and also the output of

```


lsmod


```

this info is a place to start. it should tell you what sound card you have and what kernel module is loaded for that sound card. if any.

---

### Post by kevindubrow on 2008-01-25
Thanks so much for your reply!
[B]
~$ lspci[/B]
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
08:05.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
08:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
08:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
09:00.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)




**~$ lsmod**
Module                  Size  Used by
snd_rtctimer            5344  1 
radeon                130080  2 
drm                   107688  3 radeon
ipv6                  325896  8 
ppdev                  11528  0 
powernow_k8            16864  0 
cpufreq_stats           8704  0 
cpufreq_userspace       6304  0 
cpufreq_conservative     9864  0 
cpufreq_powersave       3200  0 
cpufreq_ondemand       11024  1 
freq_table              6592  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
button                 10656  0 
ac                      7560  0 
battery                12680  0 
video                  21268  0 
container               6656  0 
sbs                    21904  0 
dock                   13248  0 
sbp2                   27784  0 
parport_pc             42792  0 
lp                     16264  0 
parport                45196  3 ppdev,parport_pc,lp
loop                   22660  0 
wlan_scan_sta          17152  1 
ath_rate_sample        15872  1 
af_packet              28812  4 
ath_pci               106160  0 
wlan                  225864  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               220272  3 ath_rate_sample,ath_pci
snd_atiixp             24468  1 
snd_pcm_oss            50560  0 
snd_atiixp_modem       19852  0 
snd_ac97_codec        122840  2 snd_atiixp,snd_atiixp_modem
snd_mixer_oss          20352  1 snd_pcm_oss
ac97_bus                4608  1 snd_ac97_codec
snd_pcm                95624  4 snd_atiixp,snd_pcm_oss,snd_atiixp_modem,snd_ac97_codec
snd_seq_dummy           5508  0 
pcmcia                 47440  0 
snd_seq_oss            37632  0 
snd_seq_midi           11136  0 
snd_rawmidi            30336  1 snd_seq_midi
snd_seq_midi_event     10240  2 snd_seq_oss,snd_seq_midi
joydev                 13568  0 
sg                     42024  0 
bcm43xx               140904  0 
snd_seq                63776  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
yenta_socket           30476  2 
xpad                   12040  0 
sd_mod                 33408  2 
ieee80211softmac       34816  1 bcm43xx
rsrc_nonstatic         14336  1 yenta_socket
snd_timer              28040  3 snd_rtctimer,snd_pcm,snd_seq
ieee80211              39112  2 bcm43xx,ieee80211softmac
wacom                  20096  0 
pcmcia_core            47700  3 pcmcia,yenta_socket,rsrc_nonstatic
ieee80211_crypt         8448  1 ieee80211
snd_seq_device         10516  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
sky2                   52740  0 
snd                    70696  14 snd_atiixp,snd_pcm_oss,snd_atiixp_modem,snd_ac97_codec,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               9348  0 
psmouse                46108  0 
pcspkr                  4992  0 
soundcore              11040  1 snd
k8temp                  7936  0 
snd_page_alloc         12688  3 snd_atiixp,snd_atiixp_modem,snd_pcm
i2c_piix4              11788  0 
i2c_core               31488  1 i2c_piix4
shpchp                 38684  0 
pci_hotplug            37876  1 shpchp
evdev                  13184  8 
ext3                  147216  2 
jbd                    68592  1 ext3
mbcache                11784  1 ext3
ide_cd                 35872  1 
cdrom                  42152  1 ide_cd
ide_disk               20352  3 
ata_generic            10372  0 
usb_storage            83264  1 
libata                139312  1 ata_generic
usbhid                 33600  0 
libusual               23208  1 usb_storage
hid                    33664  1 usbhid
scsi_mod              174776  5 sbp2,sg,sd_mod,usb_storage,libata
ohci1394               39752  0 
ieee1394              112856  2 sbp2,ohci1394
atiixp                  8208  0 [permanent]
ehci_hcd               40460  0 
ide_core              146320  4 ide_cd,ide_disk,usb_storage,atiixp
ohci_hcd               25476  0 
usbcore               163760  8 xpad,wacom,usb_storage,usbhid,libusual,ehci_hcd,ohci_hcd
thermal                16784  0 
processor              36232  2 powernow_k8,thermal
fan                     7176  0 
fuse                   53808  1 
apparmor               48288  0 
commoncap               9600  1 apparmor



This would take me forever to fix by myself. I wish I knew how to get the required information from this. Thanks so much for your time, I really appreciate it!

---

### Post by Mikecore on 2008-01-26
this comes from lspci

```


00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)


```

and it tells you that you have a ATI IXP SB400 AC'97 audio sound card.


the reason I asked you for lsmod is that command show you which kernel modules are installed ( a kernel module is a device driver ) and this came from lsmod

```


snd_atiixp 24468 1 


```

this shows that your kernel has the correct module loaded for your sound card. so thats a good start.


I have an older HP laptop that uses the IXP sound driver and back in the day I used to have to remove or ( black list ) ( basicly prevent it from loading the modem module ) the modem driver because it would mess up the IXP sound card driver. I not sure that is your problem but it worth searching these forums about or maybe even google.

next let too at your boot message. try this again in a terminal

```


sudo dmesg


```

please post the resualt

---

### Post by kevindubrow on 2008-01-26
**stephen@ubuntu:~$ sudo dmesg**
[sudo] password for stephen:
[    0.000000] Linux version 2.6.22-14-rt (buildd@king) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP PREEMPT RT Tue Dec 18 06:37:06 UTC 2007 (Unofficial)
[    0.000000] Command line: root=UUID=d63262de-f307-4c1b-b12d-782888aa441c ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001beb0000 (usable)
[    0.000000]  BIOS-e820: 000000001beb0000 - 000000001beb7000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001beb7000 - 000000001bf00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001bf00000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 114352) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F7D20 checksum 0
[    0.000000] ACPI: RSDP 000F7D20, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 1BEB15FC, 0034 (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 1BEB6DDE, 0074 (r1 GATEWA W730-K8x  6040000 ATI     F4240)
[    0.000000] ACPI: DSDT 1BEB1630, 57AE (r1 GATEWA W730-K8x  6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 1BEB7FC0, 0040
[    0.000000] ACPI: SSDT 1BEB6E52, 0118 (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: APIC 1BEB6F6A, 005A (r1 PTLTD       APIC    6040000  LTP        0)
[    0.000000] ACPI: MCFG 1BEB6FC4, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000001beb0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 114352) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000001beb0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   114352
[    0.000000] On node 0 totalpages: 114255
[    0.000000]   DMA zone: 96 pages used for memmap
[    0.000000]   DMA zone: 1192 pages reserved
[    0.000000]   DMA zone: 2711 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 2584 pages used for memmap
[    0.000000]   DMA32 zone: 107672 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34376 bytes of per cpu data
[    0.000000] Real-Time Preemption Support (C) 2004-2007 Ingo Molnar
[    0.000000] Built 1 zonelists.  Total pages: 110383
[    0.000000] Kernel command line: root=UUID=d63262de-f307-4c1b-b12d-782888aa441c ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] WARNING: experimental RCU implementation.
[    0.000000] PID hash table entries: 2048 (order: 11, 16384 bytes)
[    0.000000] TSC calibrated against PM_TIMER
[   10.743243] time.c: Detected 2188.787 MHz processor.
[   10.744131] Console: colour VGA+ 80x25
[   10.744147] Checking aperture...
[   10.744150] CPU 0: aperture @ 2b0c000000 size 32 MB
[   10.744152] Aperture too small (32 MB)
[   10.756857] No AGP bridge found
[   10.767732] Memory: 433848k/457408k available (2343k kernel code, 23172k reserved, 1228k data, 324k init)
[   10.827052] Calibrating delay using timer specific routine.. 4380.40 BogoMIPS (lpj=2190202)
[   10.827099] Security Framework v1.0.0 initialized
[   10.827109] SELinux:  Disabled at boot.
[   10.827182] Dentry cache hash table entries: 65536 (order: 7, 524288 bytes)
[   10.827815] Inode-cache hash table entries: 32768 (order: 6, 262144 bytes)
[   10.828125] Mount-cache hash table entries: 256
[   10.828320] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   10.828323] CPU: L2 Cache: 1024K (64 bytes/line)
[   10.828325] CPU 0/0 -> Node 0
[   10.828345] SMP alternatives: switching to UP code
[   10.828563] Freeing SMP alternatives: 19k freed
[   10.829863] Early unpacking initramfs... done
[   11.111096] ACPI: Core revision 20070126
[   11.111175] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   11.126014] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   11.136051] Using local APIC timer interrupts.
[   11.181662] APIC timer calibration result 12436293
[   11.181663] Detected 12.436 MHz APIC timer.
[   11.182028] Brought up 1 CPUs
[   11.182267] NET: Registered protocol family 16
[   11.182362] ACPI: bus type pci registered
[   11.182372] PCI: Using configuration type 1
[   11.183279] ACPI: EC: Look up EC in DSDT
[   11.183915] ACPI: EC: GPE=0x18, ports=0x66, 0x62
[   11.184783] ACPI: Interpreter enabled
[   11.184786] ACPI: (supports S0 S3 S4 S5)
[   11.184802] ACPI: Using IOAPIC for interrupt routing
[   11.189342] ACPI: EC: GPE=0x18, ports=0x66, 0x62
[   11.189378] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   11.189383] PCI: Probing PCI hardware (bus 00)
[   11.190710] PCI: Transparent bridge - 0000:00:14.4
[   11.190819] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   11.190989] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[   11.191111] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   11.191223] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   11.193642] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[   11.193740] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[   11.193825] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[   11.193908] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[   11.193991] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[   11.194075] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[   11.194159] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[   11.194247] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[   11.194317] Linux Plug and Play Support v0.97 (c) Adam Belay
[   11.194329] pnp: PnP ACPI init
[   11.194339] ACPI: bus type pnp registered
[   11.197042] pnp: PnP ACPI: found 10 devices
[   11.197044] ACPI: ACPI bus type pnp unregistered
[   11.197108] PCI: Using ACPI for IRQ routing
[   11.197110] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   11.197210] NET: Registered protocol family 8
[   11.197212] NET: Registered protocol family 20
[   11.197344] pnp: 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   11.197348] pnp: 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[   11.197352] pnp: 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[   11.197359] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[   11.197362] pnp: 00:08: ioport range 0x200-0x20f has been reserved
[   11.197365] pnp: 00:08: ioport range 0x220-0x22f has been reserved
[   11.197368] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
[   11.197373] pnp: 00:09: iomem range 0xe0000-0xfffff could not be reserved
[   11.197377] pnp: 00:09: iomem range 0xfff80000-0xffffffff could not be reserved
[   11.197380] pnp: 00:09: iomem range 0x0-0xfff could not be reserved
[   11.197747] PCI: Bridge: 0000:00:01.0
[   11.197750]   IO window: 9000-9fff
[   11.197753]   MEM window: d0100000-d01fffff
[   11.197756]   PREFETCH window: d4000000-d7ffffff
[   11.197758] PCI: Bridge: 0000:00:06.0
[   11.197761]   IO window: a000-afff
[   11.197765]   MEM window: d0200000-d02fffff
[   11.197767]   PREFETCH window: disabled.
[   11.197772] PCI: Bus 9, cardbus bridge: 0000:08:05.0
[   11.197774]   IO window: 0000b400-0000b4ff
[   11.197780]   IO window: 0000b800-0000b8ff
[   11.197787]   PREFETCH window: 30000000-33ffffff
[   11.197793]   MEM window: 34000000-37ffffff
[   11.197798] PCI: Bridge: 0000:00:14.4
[   11.197801]   IO window: b000-bfff
[   11.197808]   MEM window: d0300000-d03fffff
[   11.197813]   PREFETCH window: 30000000-33ffffff
[   11.197831] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   11.197856] PCI: Enabling device 0000:08:05.0 (0004 -> 0007)
[   11.197863] ACPI: PCI Interrupt 0000:08:05.0[A] -> GSI 22 (level, low) -> IRQ 22
[   11.197924] NET: Registered protocol family 2
[   11.203763] IP route cache hash table entries: 4096 (order: 3, 32768 bytes)
[   11.203943] TCP established hash table entries: 16384 (order: 8, 1179648 bytes)
[   11.205479] TCP bind hash table entries: 16384 (order: 8, 1048576 bytes)
[   11.206748] TCP: Hash tables configured (established 16384 bind 16384)
[   11.206752] TCP reno registered
[   11.208858] checking if image is initramfs... it is
[   11.747851] Freeing initrd memory: 7554k freed
[   11.757291] audit: initializing netlink socket (disabled)
[   11.757307] audit(1201358760.959:1): initialized
[   11.757488] VFS: Disk quotas dquot_6.5.1
[   11.757496] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   11.757548] io scheduler noop registered
[   11.757551] io scheduler anticipatory registered
[   11.757553] io scheduler deadline registered
[   11.757561] io scheduler cfq registered (default)
[   11.757567] PCI: MSI quirk detected. MSI deactivated.
[   12.420002] Boot video device is 0000:01:05.0
[   12.420179] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   12.420200] assign_interrupt_mode Found MSI capability
[   12.420205] Allocate Port Service[0000:00:06.0:pcie00]
[   12.445099] Real Time Clock Driver v1.12ac
[   12.445206] Linux agpgart interface v0.102 (c) Dave Jones
[   12.445209] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   12.445791] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[   12.445800] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[   12.446410] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   12.446561] input: Macintosh mouse button emulation as /class/input/input0
[   12.446640] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   12.448765] serio: i8042 KBD port at 0x60,0x64 irq 1
[   12.448813] serio: i8042 AUX port at 0x60,0x64 irq 12
[   12.448938] mice: PS/2 mouse device common for all mice
[   12.449060] TCP cubic registered
[   12.449067] NET: Registered protocol family 1
[   12.449298] /build/buildd/linux-source-2.6.22-2.6.22/debian/build/custom-source-rt/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   12.449308] Freeing unused kernel memory: 324k freed
[   12.477350] input: AT Translated Set 2 keyboard as /class/input/input1
[   13.598557] AppArmor: AppArmor initialized<5>audit(1201358762.803:2):  type=1505 info="AppArmor initialized" pid=1164
[   13.603662] fuse init (API version 7.8)
[   13.607629] Failure registering capabilities with primary security module.
[   13.614217] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   13.614224] ACPI: Processor [CPU0] (supports 8 throttling states)
[   14.087061] usbcore: registered new interface driver usbfs
[   14.087088] usbcore: registered new interface driver hub
[   14.087753] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   14.087758] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   14.089915] usbcore: registered new device driver usb
[   14.092226] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[   14.092251] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   14.092264] ATIIXP: chipset revision 0
[   14.092266] ATIIXP: not 100% native mode: will probe irqs later
[   14.092276]     ide0: BM-DMA at 0x8410-0x8417, BIOS settings: hda:DMA, hdb:pio
[   14.092290]     ide1: BM-DMA at 0x8418-0x841f, BIOS settings: hdc:DMA, hdd:pio
[   14.092300] Probing IDE interface ide0...
[   14.096555] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   14.431841] hda: FUJITSU MHV2080AT PL, ATA DISK drive
[   15.042419] hda: selected mode 0x45
[   15.046069] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   15.119335] Probing IDE interface ide1...
[   15.790604] hdc: TSSTcorpCD/DVDW TS-L532U, ATAPI CD/DVD-ROM drive
[   16.401183] hdc: selected mode 0x42
[   16.421535] ide1 at 0x170-0x177,0x376 on irq 15
[   16.436537] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19
[   16.436923] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   16.437378] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   16.437437] ohci_hcd 0000:00:13.0: irq 19, io mem 0xd0000000
[   16.492384] usb usb1: configuration #1 chosen from 1 choice
[   16.492515] hub 1-0:1.0: USB hub found
[   16.492526] hub 1-0:1.0: 4 ports detected
[   16.593257] ACPI: PCI Interrupt 0000:08:0e.0[A] -> GSI 23 (level, low) -> IRQ 23
[   16.595863] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19
[   16.596197] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   16.596514] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[   16.596573] ehci_hcd 0000:00:13.2: irq 19, io mem 0xd0002000
[   16.596585] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   16.596966] usb usb2: configuration #1 chosen from 1 choice
[   16.597112] hub 2-0:1.0: USB hub found
[   16.597117] hub 2-0:1.0: 8 ports detected
[   16.647199] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[23]  MMIO=[d0303000-d03037ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   16.698051] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19
[   16.698464] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   16.698805] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[   16.698825] ohci_hcd 0000:00:13.1: irq 19, io mem 0xd0001000
[   16.753992] usb usb3: configuration #1 chosen from 1 choice
[   16.754148] hub 3-0:1.0: USB hub found
[   16.754159] hub 3-0:1.0: 4 ports detected
[   16.863309] SCSI subsystem initialized
[   16.901079] libata version 2.21 loaded.
[   16.913365] hda: max request size: 128KiB
[   16.913848] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
[   16.917445] hda: cache flushes supported
[   16.917489]  hda:<6>usb 2-2: new high speed USB device using ehci_hcd and address 2
[   16.946991]  hda1 hda2 < hda5 >
[   16.996668] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   16.996678] Uniform CD-ROM driver Revision: 3.20
[   17.042905] usb 2-2: configuration #1 chosen from 1 choice
[   17.043094] hub 2-2:1.0: USB hub found
[   17.043189] hub 2-2:1.0: 4 ports detected
[   17.238321] Attempting manual resume
[   17.238326] swsusp: Resume From Partition 3:5
[   17.238327] PM: Checking swsusp image.
[   17.238523] PM: Resume from disk failed.
[   17.288854] kjournald starting.  Commit interval 5 seconds
[   17.288865] EXT3-fs: mounted filesystem with ordered data mode.
[   17.349621] usb 2-3: new high speed USB device using ehci_hcd and address 3
[   17.468908] usb 2-3: configuration #1 chosen from 1 choice
[   17.907808] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00032521500103c2]
[   17.934649] usb 3-2: new full speed USB device using ohci_hcd and address 2
[   18.117499] usb 3-2: configuration #1 chosen from 1 choice
[   18.297209] usb 2-2.4: new low speed USB device using ehci_hcd and address 5
[   18.392904] usb 2-2.4: configuration #1 chosen from 1 choice
[   27.804855] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   27.836405] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   28.216473] input: PC Speaker as /class/input/input2
[   28.382857] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   28.445587] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   28.445606] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   28.445908] sky2 0000:02:00.0: v1.18 addr 0xd0200000 irq 18 Yukon-FE (0xb7) rev 1
[   28.451385] sky2 eth0: addr 00:03:25:28:b0:06
[   28.527613] ieee80211_crypt: registered algorithm 'NULL'
[   28.585934] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   28.585939] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   28.611400] input: Wacom Intuos3 6x8 as /class/input/input3
[   28.618300] usbcore: registered new interface driver wacom
[   28.618307] /build/buildd/linux-source-2.6.22-2.6.22/debian/build/custom-source-rt/drivers/input/tablet/wacom_sys.c: v1.46:USB Wacom Graphire and Wacom Intuos tablet driver
[   28.619403] Yenta: CardBus bridge found at 0000:08:05.0 [107b:0506]
[   28.619438] Yenta: Using CSCINT to route CSC interrupts to PCI
[   28.619441] Yenta: Routing CardBus interrupts to PCI
[   28.619448] Yenta TI: socket 0000:08:05.0, mfunc 0x01001002, devctl 0x44
[   28.691454] usbcore: registered new interface driver libusual
[   28.760367] usbcore: registered new interface driver xpad
[   28.760372] /build/buildd/linux-source-2.6.22-2.6.22/debian/build/custom-source-rt/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   28.802558] bcm43xx driver
[   28.808619] usbcore: registered new interface driver hiddev
[   28.812295] input: Microsoft Microsoft Wireless Optical Desktop&#65533; 1.00 as /class/input/input4
[   28.812344] input: USB HID v1.11 Keyboard [Microsoft Microsoft Wireless Optical Desktop&#65533; 1.00] on usb-0000:00:13.2-2.4
[   28.840824] input: Microsoft Microsoft Wireless Optical Desktop&#65533; 1.00 as /class/input/input5
[   28.840882] input: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Desktop&#65533; 1.00] on usb-0000:00:13.2-2.4
[   28.840899] usbcore: registered new interface driver usbhid
[   28.840904] /build/buildd/linux-source-2.6.22-2.6.22/debian/build/custom-source-rt/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   28.843597] Yenta: ISA IRQ mask 0x0cf8, PCI irq 22
[   28.843603] Socket status: 30000061
[   28.843608] pcmcia: parent PCI bridge I/O window: 0xb000 - 0xbfff
[   28.843611] pcmcia: parent PCI bridge Memory window: 0xd0300000 - 0xd03fffff
[   28.843613] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[   28.870373] Initializing USB Mass Storage driver...
[   28.871474] ACPI: PCI Interrupt 0000:08:07.0[A] -> GSI 22 (level, low) -> IRQ 22
[   28.891662] scsi0 : SCSI emulation for USB Mass Storage devices
[   28.901013] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x23aeb3, caps: 0xa04713/0x10008
[   28.914642] usb-storage: device found at 3
[   28.914647] usb-storage: waiting for device to settle before scanning
[   28.914682] usbcore: registered new interface driver usb-storage
[   28.914685] USB Mass Storage support registered.
[   28.934812] input: SynPS/2 Synaptics TouchPad as /class/input/input6
[   29.021794] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   29.301275] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   29.311121] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   29.439938] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 17
[   29.493670] pccard: CardBus card inserted into slot 0
[   29.493797] yenta EnE: chaning testregister 0xC9, 04 -> 04
[   29.499332] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[   29.530008] ath_hal: module license 'Proprietary' taints kernel.
[   29.532658] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   29.602514] MC'97 0 converters and GPIO not ready (0x1)
[   29.748385] wlan: 0.8.4.2 (0.9.3.2)
[   29.811214] ath_pci: 0.9.4.5 (0.9.3.2)
[   29.811722] PCI: Enabling device 0000:09:00.0 (0000 -> 0002)
[   29.811729] ACPI: PCI Interrupt 0000:09:00.0[A] -> GSI 22 (level, low) -> IRQ 22
[   30.396121] NET: Registered protocol family 17
[   30.433407] ath_rate_sample: 1.2 (0.9.3.2)
[   30.433821] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   30.433826] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   30.433833] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   30.433836] wifi0: mac 7.8 phy 4.5 radio 5.6
[   30.433840] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   30.433842] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   30.433843] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   30.433845] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   30.433847] wifi0: Use hw queue 8 for CAB traffic
[   30.433848] wifi0: Use hw queue 9 for beacons
[   30.463250] wifi0: Atheros 5212: mem=0x34000000, irq=22
[   30.988215] loop: module loaded
[   31.056859] lp: driver loaded but no devices found
[   31.203805] Adding 1301224k swap on /dev/hda5.  Priority:-1 extents:1 across:1301224k
[   31.660581] EXT3 FS on hda1, internal journal
[   32.869178] No dock devices found.
[   32.997375] ACPI: Battery Slot [BAT0] (battery present)
[   33.019379] ACPI: AC Adapter [AC] (on-line)
[   33.184330] input: Power Button (FF) as /class/input/input7
[   33.184360] ACPI: Power Button (FF) [PWRF]
[   33.184401] input: Power Button (CM) as /class/input/input8
[   33.184418] ACPI: Power Button (CM) [PWRB]
[   33.184452] input: Sleep Button (CM) as /class/input/input9
[   33.184473] ACPI: Sleep Button (CM) [SLPB]
[   33.184508] input: Lid Switch as /class/input/input10
[   33.184535] ACPI: Lid Switch [LID]
[   33.439207] NET: Registered protocol family 10
[   33.439281] lo: Disabled Privacy Extensions
[   33.533040] powernow-k8: Found 1 Mobile AMD Athlon(tm) 64 Processor 3400+ processors (version 2.00.00)
[   33.533093] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x8
[   33.533095] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xa
[   33.533097] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xc
[   33.533099] powernow-k8:    3 : fid 0x8 (1600 MHz), vid 0xe
[   33.533101] powernow-k8:    4 : fid 0x0 (800 MHz), vid 0x18
[   33.906694] usb-storage: device scan complete
[   33.941997] scsi 0:0:0:0: Direct-Access     WD       1600JB External  0108 PQ: 0 ANSI: 0
[   34.155415] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   34.156333] sd 0:0:0:0: [sda] Write Protect is off
[   34.156337] sd 0:0:0:0: [sda] Mode Sense: 03 00 00 00
[   34.156339] sd 0:0:0:0: [sda] Assuming drive cache: write through
[   34.157279] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   34.158289] sd 0:0:0:0: [sda] Write Protect is off
[   34.158292] sd 0:0:0:0: [sda] Mode Sense: 03 00 00 00
[   34.158294] sd 0:0:0:0: [sda] Assuming drive cache: write through
[   34.158297]  sda: sda1
[   34.172692] sd 0:0:0:0: [sda] Attached SCSI disk
[   34.242112] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   34.739472] ppdev: user-space parallel port driver
[   34.973903] audit(1201358785.090:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4869 profile="/usr/sbin/cupsd"
[   35.309190] Failure registering capabilities with primary security module.
[   36.348686] Marking TSC unstable due to cpufreq changes
[   36.876979] [drm] Initialized drm 1.1.0 20060810
[   36.881712] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[   36.882228] [drm] Initialized radeon 1.27.0 20060524 on minor 0
[   37.948602] [drm] Setting GART location based on new memory map
[   37.949260] [drm] Loading R300 Microcode
[   37.949271] [drm] writeback test succeeded in 1 usecs
[   39.241105] ath0: no IPv6 routers present
[   44.864188] kjournald starting.  Commit interval 5 seconds
[   44.864641] EXT3 FS on sda1, internal journal
[   44.864646] EXT3-fs: mounted filesystem with ordered data mode.
[   46.366478] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.


I see that it says that my wireless card isn't working...that thing is such a pain that I am just using another card I found lying around for the time being. Thanks again for your help!

---

### Post by Mikecore on 2008-01-26
Ok maybe I jumped in too beep. when you say your sound is not working. Do you mean you actually do not have any sound for just no desktop sounds.? And just to be safe you have already checked your volume control and made sure its not muted. or that your PC speakers are plugged in. ( there are two sound controls just like windows Master and PCM both need to be on to here anything. ) also you say no sound in Gusty does that mean you
have run others version of Ubuntu and you had sound?

---

### Post by Mikecore on 2008-01-26
also try removing the kernel module and reinstalling it. like this

```


sudo rmmod snd_atiixp


```

then to re-load it 

```


sudo modprobe snd_atiixp


```

then try your sound.


if that doesn't work you could try removing your modem driver then removing and reloading the sound driver. as I stated before I do have an HP with that uses the snd-atiixp sound driver and a while ago thats what I had to do to get it working.

to remove the modem driver

```


sudo rmmod snd_atiixp_modem


```

this that doesn't work don't forget to reload it with

[code]

sudo modprobe snd+atiixp+modem


also you might want to try getting your wireless card working correctly I would remove the other one and use the restricted driver manager to install the wireless driver and the correct micro code ( firmware ) for your card. sometimes when you get errors with one device it can cause other issues ( not saying thats the case with your no sound but lets get everything working correctly. ( note it will ask you where to get the firmware from choose the internet let it download the firmware don't use one that you removed from the windows driver file. ) I have had great luck with this restricted driver manager on both my HP laptops and both have broadcom cards in them.

---

### Post by Mikecore on 2008-01-26
one last thing I would also be searching on google and these forums for other posts regarding this problem most like other have run into this and know how to fix it.

---

### Post by kevindubrow on 2008-01-26
Hey, yeah, no sound at all. The volume is up and everything. I tried those codes but they wont work because "Module snd_atiixp is in use." So I'll try to start Ubuntu in text mode or something and see what happens.

---

### Post by shadyedsan on 2008-01-26
i know it's a long shot, but can you please post the output of this command from a terminal:

less /proc/asound/modules


i need to see what soundcards or devices you actually have

---

### Post by kevindubrow on 2008-01-26
0 snd_atiixp
 1 snd_atiixp_modem
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
(END)

Thanks for the help!

---

### Post by shadyedsan on 2008-01-26
ok, i'm guessing that the first entry is the default sound device.

give this a try:

sudo gedit /etc/modprobe.d/alsa-base

Find the place where it says something like
# Prevent abnormal drivers from grabbing index 0
and in the list below add
options snd_whateveryourcardnameswere index=-2

in your case it would be options snd_atiixp_modem index =-2

save the file and reboot ubuntu and see if the sound works.

the reason why i mentioned the above is because for some reason, ubuntu selects random sound devices at boot and doesn't load apparent default devices. the instructions above are to blacklist the devices you know you don't use and to force ubuntu to grab slot 0 (which is the device you want to use) everytime you start up.

hopefully this will work, and if not there may be other problems

---

### Post by kevindubrow on 2008-01-26
Well, that text you told me to add in was already there....well something very similar: **options snd-atiixp-modem index=-2**

Should I still add what you told me to add? Also, I don't know if this helps, but at Sound Preferences under Audio Conferencing, I tested Sound Capture and got this error message: **Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'**

---

### Post by shadyedsan on 2008-01-26
i wouldn't say adding it would help any if it is already there. does the sound device you want to use appear in the option menus in the sound preferences? if so, do any of the tests work?

also try it with the other options such as alsa.

it may also be possible that some sound drivers are missing or don't work such as alsa-base

---

### Post by kevindubrow on 2008-01-26
Yeah, my device is there and I have tested each option with both the lap top speakers and some computer speakers.

---

### Post by shadyedsan on 2008-01-26
you may want to try installing esound (if you don't already have it), sometimes this may help

in a terminal window type

sudo apt-get update
sudo apt-get install esound

---

### Post by shadyedsan on 2008-01-26
i have been doing a little digging around for you and have come up with this elsewhere in the ubuntu forums which are related to your problem:

[http://ubuntuforums.org/showthread.php?t=365342](http://ubuntuforums.org/showthread.php?t=365342)

hope this helps in some way.

please post back your results

---

### Post by kevindubrow on 2008-01-26
No luck with that.

---

### Post by shadyedsan on 2008-01-26
i'm afraid i can't help you any further. i hope you find a solution to your problem.

if it were me, and it was a desktop machine, i would be inclined to just install a soundcard.

sorry i couldn't help any further.

good luck!

---

### Post by kevindubrow on 2008-01-26
Thanks a lot, I appreciate your time.

---

### Post by shadyedsan on 2008-01-26
no problemo! :KS

---

### Post by kevindubrow on 2008-01-26
Ok, I found a guide that explained how to enable sound on my specific laptop. It didn't work, but I assumed it wasn't working because of all the things I had done to try to get sound working already. I reinstalled, had no sound, but followed the guide and had sound. I think I will be making a how to on installing Gusty on this laptop. Thanks a lot for all of the help here.

---

### Post by cdtech on 2008-01-27
Could you post a link please?

Thanks

---

### Post by kevindubrow on 2008-01-27
I don't exactly know where I found it...tuxmachines or something like that. But its really simple, so I'll just type it here.

Get an audio file and play it.
Double click on the sound icon at the top right (do this step and all the rest while the file is playing).
Go to edit than preferences.
Check external amplifier.
Now you will have a "switches" tab on the mixer, click on it.
You should only see one check box, "External Amplifier"
Un-check it.
The audio from that file should begin to play immediately.

A couple of notes:
It didn't work for me the first time because I had done so many things previously to fix the audio issue, once I reinstalled Gusty, I used this method again and audio worked.

Where I found this guide didn't mention playing an audio file...but it only worked for me once I did. I'm sure its an isolated occasion...so if you don't have an audio file to play, just do without. 

I hope it works, please ask me any questions if you have any. This method should work for a lot of the MX Series Gateway laptops.

---

### Post by Mikecore on 2008-01-27
you should edit the titled thread and add "Solved" to it.

---

