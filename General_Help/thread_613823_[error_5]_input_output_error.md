---
title: "[error 5] input output error"
date: 2007-11-15
forum: General Help
---

### Post by talibsyed on 2007-11-15
I am trying to install ubuntu 7.10 by using Wubi 7.10 but at the progress of 55% it gives me an error of input output error plz help:confused:

---

### Post by ago on 2007-11-15
> **talibsyed said:**
> I am trying to install ubuntu 7.10 by using Wubi 7.10 but at the progress of 55% it gives me an error of input output error plz help:confused:

Can you post here /var/log/syslog

Also the output of

lspci -vv
lsmod
sudo hdparm -I /dev/sda

---

### Post by talibsyed on 2007-11-16
currently i am running 7.04
can i get you thiose information from that also


root@zulfi25:~# lspci -vv
00:00.0 Host bridge: Intel Corporation 82820 820 (Camino) Chipset Host Bridge (MCH) (rev 04)
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
        Latency: 0
        Region 0: Memory at e0000000 (32-bit, prefetchable) [size=256M]
        Capabilities: [a0] AGP version 2.0
                Status: RQ=32 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW- AGP3- Rate=x1,x2,x4
                Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP- GART64- 64bit- FW- Rate=<none>

00:01.0 PCI bridge: Intel Corporation 82820 820 (Camino) Chipset AGP Bridge (rev 04) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        Memory behind bridge: fc900000-fe9fffff
        Prefetchable memory behind bridge: cc600000-dc6fffff
        Secondary status: 66MHz+ FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-

00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fea00000-feafffff
        Prefetchable memory behind bridge: dc700000-dc7fffff
        Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-

00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
        Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02) (prog-if 80 [Master])
        Subsystem: Intel Corporation 82801AA IDE
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        Region 4: I/O ports at ffa0 [size=16]

00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation 82801AA USB
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin D routed to IRQ 10
        Region 4: I/O ports at ef80 [size=32]

00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
        Subsystem: Intel Corporation 82801AA SMBus
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin B routed to IRQ 9
        Region 4: I/O ports at efa0 [size=16]

01:00.0 VGA compatible controller: nVidia Corporation NV15 [GeForce2 GTS/Pro] (rev a4) (prog-if 00 [VGA])
        Subsystem: nVidia Corporation GeForce2 GTS
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (1250ns min, 250ns max)
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: Memory at d0000000 (32-bit, prefetchable) [size=128M]
        Expansion ROM at fe9f0000 [disabled] [size=64K]
        Capabilities: [60] Power Management version 1
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [44] AGP version 2.0
                Status: RQ=32 Iso- ArqSz=0 Cal=0 SBA- ITACoh- GART64- HTrans- 64bit- FW+ AGP3- Rate=x1,x2,x4
                Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP- GART64- 64bit- FW- Rate=<none>

02:08.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
        Subsystem: Hewlett-Packard Company Unknown device 9207
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (8000ns min, 16000ns max)
        Interrupt: pin A routed to IRQ 11
        Region 0: I/O ports at d800 [size=256]
        Region 1: Memory at feaffc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

02:0a.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
        Subsystem: C-Media Electronics Inc CMI8738/C3DX PCI Audio Device
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (500ns min, 6000ns max)
        Interrupt: pin A routed to IRQ 3
        Region 0: I/O ports at d400 [size=256]
        Capabilities: [c0] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-









root@zulfi25:~# lsmod
Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
speedstep_lib           6148  0 
cpufreq_ondemand        9228  0 
cpufreq_stats           7360  0 
cpufreq_powersave       2688  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5408  0 
cpufreq_conservative     8200  0 
sony_acpi               6284  0 
pcc_acpi               13184  0 
tc1100_wmi              8068  0 
dev_acpi               12292  0 
dock                   10268  0 
ac                      6020  0 
asus_acpi              17308  0 
video                  16388  0 
container               5248  0 
backlight               7040  1 asus_acpi
button                  8720  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
battery                10756  0 
ipv6                  268704  8 
lp                     12452  0 
snd_cmipci             37024  1 
gameport               16520  1 snd_cmipci
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  2 snd_cmipci,snd_pcm_oss
snd_page_alloc         10888  1 snd_pcm
snd_opl3_lib           11520  1 snd_cmipci
snd_hwdep               9988  1 snd_opl3_lib
snd_mpu401_uart         9472  1 snd_cmipci
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  3 snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device          9100  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
snd                    54020  14 snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
i2c_core               22784  1 i2c_ec
serio_raw               7940  0 
psmouse                38920  0 
pcspkr                  4224  0 
intel_agp              25116  1 
agpgart                35400  1 intel_agp
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
af_packet              23816  2 
tsdev                   8768  0 
evdev                  11008  3 
floppy                 59524  0 
usbhid                 26592  0 
hid                    27392  1 usbhid
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
sg                     36252  0 
8139too                27648  0 
mii                     6528  1 8139too
generic                 5124  0 [permanent]
ata_generic             9092  0 
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability
nls_iso8859_1           5120  2 
nls_cp437               6784  2 
nls_utf8                3072  0 
squashfs               49028  0 
unionfs                74020  0 
loop                   17800  4 
fuse                   46612  1 
ntfs                  107764  0 
hfs                    49924  0 
hfsplus                78212  0 
isofs                  36284  0 
xfs                   562008  0 
jfs                   188900  0 
vfat                   14208  2 
fat                    53916  1 vfat
reiserfs              247680  0 
ext3                  133128  2 
jbd                    59816  1 ext3
ext2                   66824  0 
mbcache                 9604  2 ext3,ext2
sata_vsc               10116  0 
sata_via               12548  0 
sata_uli                8836  0 
sata_sx4               14596  0 
sata_svw                9220  0 
sata_sis               10500  0 
sata_sil               12808  0 
sata_sil24             15492  0 
sata_qstor             10500  0 
sata_promise           13316  0 
sata_nv                20868  0 
sata_mv                20232  0 
sata_inic162x          13060  0 
pdc_adma               10372  0 
pata_sis               14220  1 sata_sis
ata_piix               15492  2 
usb_storage            72256  0 
libusual               17936  1 usb_storage
ohci_hcd               22532  0 
uhci_hcd               25360  0 
ehci_hcd               34188  0 
usbcore               134280  7 usbhid,usb_storage,libusual,ohci_hcd,uhci_hcd,ehci_hcd
sd_mod                 23428  3 
libata                125720  17 ata_generic,sata_vsc,sata_via,sata_uli,sata_sx4,sata_svw,sata_sis,sata_sil,sata_sil24,sata_qstor,sata_promise,sata_nv,sata_mv,sata_inic162x,pdc_adma,pata_sis,ata_piix
scsi_mod              142348  5 sr_mod,sg,usb_storage,sd_mod,libata
dm_mirror              23188  0 
dm_mod                 59084  1 dm_mirror
raid0                   9600  0 
raid1                  25600  0 
md_mod                 79764  2 raid0,raid1







root@zulfi25:~# sudo hdparm -I /dev/sda

/dev/sda:

ATA device, with non-removable media
        Model Number:       ST380215A                               
        Serial Number:      5QZ0GGX2
        Firmware Revision:  3.AAC   
Standards:
        Supported: 7 6 5 4 
        Likely used: 7
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:  156301488
        LBA48  user addressable sectors:  156301488
        device size with M = 1024*1024:       76319 MBytes
        device size with M = 1000*1000:       80026 MBytes (80 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 16
        Recommended acoustic management value: 208, current value: 0
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 *udma4 udma5 
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4 
             Cycle time: no flow control=240ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    SMART feature set
                Security Mode feature set
           *    Power Management feature set
           *    Write cache
           *    Look-ahead
           *    Host Protected Area feature set
           *    WRITE_BUFFER command
           *    READ_BUFFER command
           *    DOWNLOAD_MICROCODE
                SET_MAX security extension
           *    48-bit Address feature set
           *    Device Configuration Overlay feature set
           *    Mandatory FLUSH_CACHE
           *    FLUSH_CACHE_EXT
           *    SMART error logging
           *    SMART self-test
           *    General Purpose Logging feature set
Security: 
        Master password revision code = 65534
                supported
        not     enabled
        not     locked
        not     frozen
        not     expired: security count
        not     supported: enhanced erase
HW reset results:
        CBLID- above Vih
        Device num = 0 determined by the jumper
Checksum: correct







and the first command you said is not getting me any results permission denied error appears

---

