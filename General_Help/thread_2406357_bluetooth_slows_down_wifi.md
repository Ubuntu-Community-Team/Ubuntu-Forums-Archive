---
title: "bluetooth slows down wifi"
date: 2018-11-19
forum: General Help
---

### Post by vichoko on 2018-11-19
i've recently bought an ASUS VivoBook and immediately installed Ubuntu.
As soon i started using my bluetooth speaker, i noticed that the bluetooth's signal range was very poor, also the wireless internet were affected being slowed down.

For example, i had a download speed of 20 KBps downloading a file with bluetooth enabled, also the bluetooth music sound intermittent.
When i turned the bluetooth off, the download speed increases to 1000 KBps.

I inspected kernel messages (dmesg) and saw these:
```
[    2.300948] [drm] Finished loading DMC firmware i915/kbl_dmc_ver1_01.bin (v1.1)
[    2.311385] [drm] Initialized i915 1.6.0 20171023 for 0000:00:02.0 on minor 0
[    2.314436] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    2.314923] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5
[    2.416617] usb 1-8: New USB device found, idVendor=13d3, idProduct=3500
[    2.416619] usb 1-8: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.534788] ata3: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.536082] ata3.00: ATA-9: SanDisk SD8SN8U256G1002, X4131002, max UDMA/133
[    2.536084] ata3.00: 500118192 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    2.537952] ata3.00: configured for UDMA/133
[    2.538231] scsi 2:0:0:0: Direct-Access     ATA      SanDisk SD8SN8U2 1002 PQ: 0 ANSI: 5
[    2.538500] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    2.538661] sd 2:0:0:0: [sda] 500118192 512-byte logical blocks: (256 GB/238 GiB)
[    2.538686] sd 2:0:0:0: [sda] Write Protect is off
[    2.538688] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.538740] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.541125]  sda: sda1 sda2 sda3 sda4
[    2.541816] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.556144] clocksource: Switched to clocksource tsc
[    2.693261] random: fast init done
[    2.904448] fbcon: inteldrmfb (fb0) is primary device
[    2.904489] Console: switching to colour frame buffer device 240x67
[    2.904509] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    2.904542] random: systemd-udevd: uninitialized urandom read (16 bytes read)
[    2.904570] random: systemd-udevd: uninitialized urandom read (16 bytes read)
[    2.904572] random: systemd-udevd: uninitialized urandom read (16 bytes read)
[    3.804723] [drm] RC6 on
[   35.756051] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[   35.902226] ip_tables: (C) 2000-2006 Netfilter Core Team
[   35.988674] systemd[1]: systemd 237 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ +LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD -IDN2 +IDN -PCRE2 default-hierarchy=hybrid)
[   36.008781] systemd[1]: Detected architecture x86-64.
[   36.011921] systemd[1]: Set hostname to <flaco>.
[   36.012686] Lockdown: /dev/mem,kmem,port is restricted; see man kernel_lockdown.7
[   36.141846] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[   36.141879] systemd[1]: Reached target User and Group Name Lookups.
[   36.141907] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[   36.141913] systemd[1]: Reached target Remote File Systems.
[   36.142021] systemd[1]: Created slice User and Session Slice.
[   36.142098] systemd[1]: Created slice System Slice.
[   36.142156] systemd[1]: Listening on fsck to fsckd communication Socket.
[   36.162979] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
[   36.171862] lp: driver loaded but no devices found
[   36.174795] ppdev: user-space parallel port driver
[   36.208748] systemd-journald[403]: Received request to flush runtime journal from PID 1
[   36.367195] input: Asus Wireless Radio Control as /devices/LNXSYSTM:00/LNXSYBUS:00/ATK4002:00/input/input6
[   36.415308] random: crng init done
[   36.415310] random: 7 urandom warning(s) missed due to ratelimiting
[   36.464749] (NULL device *): hwmon_device_register() is deprecated. Please convert the driver to use hwmon_device_register_with_info().
[   36.464906] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   36.467956] proc_thermal 0000:00:04.0: enabling device (0000 -> 0002)
[   36.474963] intel-lpss 0000:00:15.0: enabling device (0000 -> 0002)
[   36.486373] idma64 idma64.0: Found Intel integrated DMA 64-bit
[   36.500617] intel-lpss 0000:00:15.1: enabling device (0000 -> 0002)
[   36.500970] idma64 idma64.1: Found Intel integrated DMA 64-bit
[   36.509852] i2c_hid i2c-ELAN1300:00: i2c-ELAN1300:00 supply vdd not found, using dummy regulator
[   36.519861] cfg80211: Loading compiled-in X.509 certificates for regulatory database
[   36.520106] RAPL PMU: API unit is 2^-32 Joules, 5 fixed counters, 655360 ms ovfl timer
[   36.520107] RAPL PMU: hw unit of domain pp0-core 2^-14 Joules
[   36.520108] RAPL PMU: hw unit of domain package 2^-14 Joules
[   36.520109] RAPL PMU: hw unit of domain dram 2^-14 Joules
[   36.520110] RAPL PMU: hw unit of domain pp1-gpu 2^-14 Joules
[   36.520111] RAPL PMU: hw unit of domain psys 2^-14 Joules
[   36.520314] cfg80211: Loaded X.509 cert 'sforshee: 00b28ddf47aef9cea7'
[   36.521134] asus_wmi: ASUS WMI generic driver loaded
[   36.523465] asus_wmi: Initialization: 0x1
[   36.523599] asus_wmi: BIOS WMI version: 9.0
[   36.523690] asus_wmi: SFUN value: 0x21
[   36.527136] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input7
[   36.527388] asus_wmi: Number of fans: 0
[   36.538787] mei_me 0000:00:16.0: enabling device (0000 -> 0002)
[   36.556765] AVX2 version of gcm_enc/dec engaged.
[   36.556766] AES CTR mode by8 optimization enabled
[   36.560643] intel-lpss 0000:00:1e.0: enabling device (0000 -> 0002)
[   36.561122] idma64 idma64.2: Found Intel integrated DMA 64-bit
[   36.561763] intel-lpss 0000:00:1e.2: enabling device (0000 -> 0002)
[   36.562205] idma64 idma64.3: Found Intel integrated DMA 64-bit
[   36.595893] ath10k_pci 0000:01:00.0: enabling device (0000 -> 0002)
[   36.597019] ath10k_pci 0000:01:00.0: pci irq msi oper_irq_mode 2 irq_mode 0 reset_mode 0
[   36.657651] intel_rapl: Found RAPL domain package
[   36.657653] intel_rapl: Found RAPL domain core
[   36.657654] intel_rapl: Found RAPL domain uncore
[   36.657656] intel_rapl: Found RAPL domain dram
[   36.666807] snd_hda_intel 0000:00:1f.3: enabling device (0000 -> 0002)
[   36.670574] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[   36.673217] hid-multitouch 0018:04F3:3057.0001: Ignoring the extra HID_DG_INPUTMODE
[   36.673792] input: ELAN1300:00 04F3:3057 Touchpad as /devices/pci0000:00/0000:00:15.1/i2c_designware.1/i2c-7/i2c-ELAN1300:00/0018:04F3:3057.0001/input/input9
[   36.673893] hid-multitouch 0018:04F3:3057.0001: input,hidraw0: I2C HID v1.00 Mouse [ELAN1300:00 04F3:3057] on i2c-ELAN1300:00
[   36.713288] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC295: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   36.713291] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   36.713293] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[   36.713294] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[   36.713295] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[   36.713297] snd_hda_codec_realtek hdaudioC0D0:      Mic=0x12
[   36.764602] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1f.3/sound/card0/input10
[   36.765973] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input11
[   36.766041] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input12
[   36.766093] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input13
[   36.766138] input: HDA Intel PCH HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input14
[   36.766212] input: HDA Intel PCH HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input15
[   36.784308] dw-apb-uart.2: ttyS4 at MMIO 0xef234000 (irq = 20, base_baud = 115200) is a 16550A
[   36.920918] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/pre-cal-pci-0000:01:00.0.bin failed with error -2
[   36.920929] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/cal-pci-0000:01:00.0.bin failed with error -2
[   36.926765] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware-6.bin failed with error -2
[   36.934222] ath10k_pci 0000:01:00.0: qca9377 hw1.1 target 0x05020001 chip_id 0x003821ff sub 1a3b:2251
[   36.934224] ath10k_pci 0000:01:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[   36.934696] ath10k_pci 0000:01:00.0: firmware ver WLAN.TF.1.0-00002-QCATFSWPZ-5 api 5 features ignore-otp crc32 c3e0d04f
[   37.021207] ath10k_pci 0000:01:00.0: board_file api 2 bmi_id N/A crc32 8aedfa4a
[   37.371631] EXT4-fs (sda4): mounted filesystem with ordered data mode. Opts: (null)
[   37.432341] audit: type=1400 audit(1542665986.159:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-oopslash" pid=877 comm="apparmor_parser"
[   37.432504] audit: type=1400 audit(1542665986.159:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/man" pid=876 comm="apparmor_parser"
[   37.432508] audit: type=1400 audit(1542665986.159:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_filter" pid=876 comm="apparmor_parser"
[   37.432511] audit: type=1400 audit(1542665986.159:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_groff" pid=876 comm="apparmor_parser"
[   37.433357] audit: type=1400 audit(1542665986.159:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-senddoc" pid=878 comm="apparmor_parser"
[   37.433675] audit: type=1400 audit(1542665986.159:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-xpdfimport" pid=880 comm="apparmor_parser"
[   37.434367] audit: type=1400 audit(1542665986.159:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=873 comm="apparmor_parser"
[   37.434371] audit: type=1400 audit(1542665986.159:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=873 comm="apparmor_parser"
[   37.434374] audit: type=1400 audit(1542665986.159:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=873 comm="apparmor_parser"
[   37.434377] audit: type=1400 audit(1542665986.159:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=873 comm="apparmor_parser"
[   37.454324] Adding 9765372k swap on /dev/mapper/cryptswap1.  Priority:-2 extents:1 across:9765372k SSFS
[   37.507381] Bluetooth: Core ver 2.22
[   37.507397] NET: Registered protocol family 31
[   37.507398] Bluetooth: HCI device and connection manager initialized
[   37.507400] Bluetooth: HCI socket layer initialized
[   37.507402] Bluetooth: L2CAP socket layer initialized
[   37.507407] Bluetooth: SCO socket layer initialized
[   37.551441] media: Linux media interface: v0.10
[   37.558574] Linux video capture interface: v2.00
[   37.636415] usbcore: registered new interface driver btusb
[   37.654305] ath10k_pci 0000:01:00.0: htt-ver 3.44 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[   37.662861] ath: EEPROM regdomain: 0x6a
[   37.662862] ath: EEPROM indicates we should expect a direct regpair map
[   37.662864] ath: Country alpha2 being used: 00
[   37.662865] ath: Regpair used: 0x6a
[   37.672575] ath10k_pci 0000:01:00.0 wlp1s0: renamed from wlan0
[   37.709569] uvcvideo: Found UVC 1.00 device USB2.0 HD UVC WebCam (13d3:56a2)
[   37.711041] uvcvideo 1-6:1.0: Entity type for entity Realtek Extended Controls Unit was not initialized!
[   37.711051] uvcvideo 1-6:1.0: Entity type for entity Extension 4 was not initialized!
[   37.711052] uvcvideo 1-6:1.0: Entity type for entity Processing 2 was not initialized!
[   37.711054] uvcvideo 1-6:1.0: Entity type for entity Camera 1 was not initialized!
[   37.711128] input: USB2.0 HD UVC WebCam: USB2.0 HD as /devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/input/input16
[   37.711202] usbcore: registered new interface driver uvcvideo
[   37.711203] USB Video Class driver (1.1.1)
[   37.737478] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   37.737479] Bluetooth: BNEP filters: protocol multicast
[   37.737483] Bluetooth: BNEP socket layer initialized
[   38.112878] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[   38.933886] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[   39.027268] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[   43.917218] wlp1s0: authenticate with 90:94:e4:ae:57:04
[   43.953754] wlp1s0: send auth to 90:94:e4:ae:57:04 (try 1/3)
[   43.958983] wlp1s0: authenticated
[   43.960049] wlp1s0: associate with 90:94:e4:ae:57:04 (try 1/3)
[   43.964031] wlp1s0: RX AssocResp from 90:94:e4:ae:57:04 (capab=0x431 status=0 aid=5)
[   43.967807] wlp1s0: associated
[   44.005230] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready
[   57.199219] Could not find key with description: [bb4b4a20210cb4eb]
[   57.199224] process_request_key_err: No key
[   57.199225] Could not find valid key in user session keyring for sig specified in mount option: [bb4b4a20210cb4eb]
[   57.199228] One or more global auth toks could not properly register; rc = [-2]
[   57.199229] Error parsing options; rc = [-2]
[   61.824952] Bluetooth: RFCOMM TTY layer initialized
[   61.824961] Bluetooth: RFCOMM socket layer initialized
[   61.824970] Bluetooth: RFCOMM ver 1.11
[   63.254454] rfkill: input handler disabled
[   84.562098] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  100.318105] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  105.565922] input: 04:52:C7:41:14:56 as /devices/virtual/input/input17
[  145.846590] wlp1s0: Connection to AP 90:94:e4:ae:57:04 lost
[  152.117417] wlp1s0: authenticate with 90:94:e4:ae:57:04
[  152.152979] wlp1s0: send auth to 90:94:e4:ae:57:04 (try 1/3)
[  152.158854] wlp1s0: authenticated
[  152.161995] wlp1s0: associate with 90:94:e4:ae:57:04 (try 1/3)
[  152.179967] wlp1s0: RX AssocResp from 90:94:e4:ae:57:04 (capab=0x431 status=0 aid=5)
[  152.183861] wlp1s0: associated
[  167.522097] wlp1s0: Connection to AP 90:94:e4:ae:57:04 lost
[  173.744571] wlp1s0: authenticate with 90:94:e4:ae:57:04
[  173.780006] wlp1s0: send auth to 90:94:e4:ae:57:04 (try 1/3)
[  173.782402] wlp1s0: authenticated
[  173.790078] wlp1s0: associate with 90:94:e4:ae:57:04 (try 1/3)
[  173.801829] wlp1s0: RX AssocResp from 90:94:e4:ae:57:04 (capab=0x431 status=0 aid=5)
[  173.805407] wlp1s0: associated
[  186.185598] wlp1s0: Connection to AP 90:94:e4:ae:57:04 lost
[  192.993793] wlp1s0: authenticate with 90:94:e4:ae:57:04
[  193.029267] wlp1s0: send auth to 90:94:e4:ae:57:04 (try 1/3)
[  193.034328] wlp1s0: send auth to 90:94:e4:ae:57:04 (try 2/3)
[  193.038084] wlp1s0: authenticated
[  193.039815] wlp1s0: associate with 90:94:e4:ae:57:04 (try 1/3)
[  193.050382] wlp1s0: associate with 90:94:e4:ae:57:04 (try 2/3)
[  193.065247] wlp1s0: RX AssocResp from 90:94:e4:ae:57:04 (capab=0x431 status=0 aid=5)
[  193.069496] wlp1s0: associated
[  206.121696] wlp1s0: Connection to AP 90:94:e4:ae:57:04 lost
[  213.032492] wlp1s0: authenticate with 90:94:e4:ae:57:04
[  213.067741] wlp1s0: send auth to 90:94:e4:ae:57:04 (try 1/3)
[  213.069438] wlp1s0: authenticated
[  213.072693] wlp1s0: associate with 90:94:e4:ae:57:04 (try 1/3)
[  213.090820] wlp1s0: RX AssocResp from 90:94:e4:ae:57:04 (capab=0x431 status=0 aid=5)
[  213.094540] wlp1s0: associated
[  248.083064] wlp1s0: Connection to AP 90:94:e4:ae:57:04 lost
[  255.088136] wlp1s0: authenticate with 90:94:e4:ae:57:04
[  255.124082] wlp1s0: send auth to 90:94:e4:ae:57:04 (try 1/3)
[  255.126962] wlp1s0: authenticated
[  255.131067] wlp1s0: associate with 90:94:e4:ae:57:04 (try 1/3)
[  255.243097] wlp1s0: associate with 90:94:e4:ae:57:04 (try 2/3)
[  255.256354] wlp1s0: RX AssocResp from 90:94:e4:ae:57:04 (capab=0x431 status=0 aid=5)
[  255.260593] wlp1s0: associated
[  294.139600] wlp1s0: Connection to AP 90:94:e4:ae:57:04 lost
[  301.386857] wlp1s0: authenticate with 90:94:e4:ae:57:04
[  301.422259] wlp1s0: send auth to 90:94:e4:ae:57:04 (try 1/3)
[  301.424558] wlp1s0: authenticated
[  301.427933] wlp1s0: associate with 90:94:e4:ae:57:04 (try 1/3)
[  301.443719] wlp1s0: RX AssocResp from 90:94:e4:ae:57:04 (capab=0x431 status=0 aid=5)
[  301.447683] wlp1s0: associated
[  312.307028] wlp1s0: Connection to AP 90:94:e4:ae:57:04 lost
[  319.305644] wlp1s0: authenticate with 90:94:e4:ae:57:04
[  319.340939] wlp1s0: send auth to 90:94:e4:ae:57:04 (try 1/3)
[  319.342706] wlp1s0: authenticated
[  319.346983] wlp1s0: associate with 90:94:e4:ae:57:04 (try 1/3)
[  319.367234] wlp1s0: RX AssocResp from 90:94:e4:ae:57:04 (capab=0x431 status=0 aid=5)
[  319.371495] wlp1s0: associated
[  337.638290] wlp1s0: Connection to AP 90:94:e4:ae:57:04 lost
[  343.712803] Lockdown: debugfs is restricted; see man kernel_lockdown.7
[  343.831409] wlp1s0: authenticate with 90:94:e4:ae:57:04
[  343.867098] wlp1s0: send auth to 90:94:e4:ae:57:04 (try 1/3)
[  343.872105] wlp1s0: send auth to 90:94:e4:ae:57:04 (try 2/3)
[  343.880680] wlp1s0: authenticated
[  343.882956] wlp1s0: associate with 90:94:e4:ae:57:04 (try 1/3)
[  343.891256] wlp1s0: RX AssocResp from 90:94:e4:ae:57:04 (capab=0x431 status=0 aid=5)
[  343.894918] wlp1s0: associated
[  356.576387] wlp1s0: Connection to AP 90:94:e4:ae:57:04 lost
[  362.368519] wlp1s0: authenticate with 90:94:e4:ae:57:04
[  362.403810] wlp1s0: send auth to 90:94:e4:ae:57:04 (try 1/3)
[  362.405801] wlp1s0: authenticated
[  362.409421] wlp1s0: associate with 90:94:e4:ae:57:04 (try 1/3)
[  362.431602] wlp1s0: RX AssocResp from 90:94:e4:ae:57:04 (capab=0x431 status=0 aid=5)
[  362.435736] wlp1s0: associated
[  376.786243] wlp1s0: Connection to AP 90:94:e4:ae:57:04 lost
[  382.215028] wlp1s0: authenticate with 90:94:e4:ae:57:04
[  382.250736] wlp1s0: send auth to 90:94:e4:ae:57:04 (try 1/3)
[  382.252409] wlp1s0: authenticated
[  382.255543] wlp1s0: associate with 90:94:e4:ae:57:04 (try 1/3)
[  382.266023] wlp1s0: associate with 90:94:e4:ae:57:04 (try 2/3)
[  382.294487] wlp1s0: RX AssocResp from 90:94:e4:ae:57:04 (capab=0x431 status=0 aid=5)
[  382.298518] wlp1s0: associated
[  392.906245] wlp1s0: Connection to AP 90:94:e4:ae:57:04 lost
[  400.720352] wlp1s0: authenticate with 90:94:e4:ae:57:04
[  400.755916] wlp1s0: send auth to 90:94:e4:ae:57:04 (try 1/3)
[  400.766091] wlp1s0: authenticated
[  400.770265] wlp1s0: associate with 90:94:e4:ae:57:04 (try 1/3)
[  400.774523] wlp1s0: RX AssocResp from 90:94:e4:ae:57:04 (capab=0x431 status=0 aid=5)
[  400.778606] wlp1s0: associated
[  414.143611] wlp1s0: Connection to AP 90:94:e4:ae:57:04 lost
[  421.315300] wlp1s0: authenticate with 90:94:e4:ae:57:04
[  421.351521] wlp1s0: send auth to 90:94:e4:ae:57:04 (try 1/3)
[  421.369337] wlp1s0: authenticated
[  421.371962] wlp1s0: associate with 90:94:e4:ae:57:04 (try 1/3)
[  421.389850] wlp1s0: RX AssocResp from 90:94:e4:ae:57:04 (capab=0x431 status=0 aid=5)
[  421.393778] wlp1s0: associated
[  432.310540] wlp1s0: Connection to AP 90:94:e4:ae:57:04 lost
[  438.221250] wlp1s0: authenticate with 90:94:e4:ae:57:04
[  438.256604] wlp1s0: send auth to 90:94:e4:ae:57:04 (try 1/3)
[  438.261445] wlp1s0: send auth to 90:94:e4:ae:57:04 (try 2/3)
[  438.265413] wlp1s0: authenticated
[  438.267498] wlp1s0: associate with 90:94:e4:ae:57:04 (try 1/3)
[  438.278179] wlp1s0: associate with 90:94:e4:ae:57:04 (try 2/3)
[  438.295168] wlp1s0: RX AssocResp from 90:94:e4:ae:57:04 (capab=0x431 status=0 aid=5)
[  438.299375] wlp1s0: associated
[  455.850688] wlp1s0: Connection to AP 90:94:e4:ae:57:04 lost
[  461.627017] wlp1s0: authenticate with 90:94:e4:ae:57:04
[  461.663000] wlp1s0: send auth to 90:94:e4:ae:57:04 (try 1/3)
[  461.666133] wlp1s0: authenticated
[  461.667987] wlp1s0: associate with 90:94:e4:ae:57:04 (try 1/3)
[  461.684550] wlp1s0: RX AssocResp from 90:94:e4:ae:57:04 (capab=0x431 status=0 aid=5)
[  461.688268] wlp1s0: associated
[  474.745211] wlp1s0: Connection to AP 90:94:e4:ae:57:04 lost
[  480.246361] wlp1s0: authenticate with 90:94:e4:ae:57:04
[  480.281827] wlp1s0: send auth to 90:94:e4:ae:57:04 (try 1/3)
[  480.283503] wlp1s0: authenticated
[  480.285910] wlp1s0: associate with 90:94:e4:ae:57:04 (try 1/3)
[  480.294071] wlp1s0: RX AssocResp from 90:94:e4:ae:57:04 (capab=0x431 status=0 aid=5)
[  480.298770] wlp1s0: associated
[  499.534452] wlp1s0: Connection to AP 90:94:e4:ae:57:04 lost
[  504.789308] wlp1s0: authenticate with 90:94:e4:ae:57:04
[  504.824984] wlp1s0: send auth to 90:94:e4:ae:57:04 (try 1/3)
[  504.828484] wlp1s0: authenticated
[  504.831227] wlp1s0: associate with 90:94:e4:ae:57:04 (try 1/3)
[  504.846399] wlp1s0: RX AssocResp from 90:94:e4:ae:57:04 (capab=0x431 status=0 aid=5)
[  504.849904] wlp1s0: associated
[  532.284937] wlp1s0: Connection to AP 90:94:e4:ae:57:04 lost
[  537.425003] wlp1s0: authenticate with 90:94:e4:ae:57:04
[  537.459903] wlp1s0: send auth to 90:94:e4:ae:57:04 (try 1/3)
[  537.481395] wlp1s0: authenticated
[  537.482551] wlp1s0: associate with 90:94:e4:ae:57:04 (try 1/3)
[  537.489675] wlp1s0: RX AssocResp from 90:94:e4:ae:57:04 (capab=0x431 status=0 aid=5)
[  537.493567] wlp1s0: associated
[  645.124503] wlp1s0: Connection to AP 90:94:e4:ae:57:04 lost
[  651.456514] wlp1s0: authenticate with 90:94:e4:ae:57:04
[  651.491807] wlp1s0: send auth to 90:94:e4:ae:57:04 (try 1/3)
[  651.494041] wlp1s0: authenticated
[  651.497358] wlp1s0: associate with 90:94:e4:ae:57:04 (try 1/3)
[  651.508514] wlp1s0: RX AssocResp from 90:94:e4:ae:57:04 (capab=0x431 status=0 aid=5)
[  651.512393] wlp1s0: associated
[  677.093230] wlp1s0: Connection to AP 90:94:e4:ae:57:04 lost
[  683.284508] wlp1s0: authenticate with 90:94:e4:ae:57:04
[  683.319613] wlp1s0: send auth to 90:94:e4:ae:57:04 (try 1/3)
[  683.323001] wlp1s0: authenticated
[  683.326514] wlp1s0: associate with 90:94:e4:ae:57:04 (try 1/3)
[  683.338655] wlp1s0: RX AssocResp from 90:94:e4:ae:57:04 (capab=0x431 status=0 aid=5)
[  683.342908] wlp1s0: associated
[  699.090031] wlp1s0: Connection to AP 90:94:e4:ae:57:04 lost
[  704.454808] wlp1s0: authenticate with 90:94:e4:ae:57:04
[  704.490133] wlp1s0: send auth to 90:94:e4:ae:57:04 (try 1/3)
[  704.496386] wlp1s0: authenticated
[  704.498631] wlp1s0: associate with 90:94:e4:ae:57:04 (try 1/3)
[  704.502557] wlp1s0: RX AssocResp from 90:94:e4:ae:57:04 (capab=0x431 status=0 aid=5)
[  704.506924] wlp1s0: associated
[  725.698599] wlp1s0: Connection to AP 90:94:e4:ae:57:04 lost
[  731.137257] wlp1s0: authenticate with 90:94:e4:ae:57:04
[  731.172475] wlp1s0: send auth to 90:94:e4:ae:57:04 (try 1/3)
[  731.176388] wlp1s0: authenticated
[  731.179769] wlp1s0: associate with 90:94:e4:ae:57:04 (try 1/3)
[  731.196291] wlp1s0: RX AssocResp from 90:94:e4:ae:57:04 (capab=0x431 status=0 aid=5)
[  731.199840] wlp1s0: associated
[  742.585846] wlp1s0: Connection to AP 90:94:e4:ae:57:04 lost
[  748.066657] wlp1s0: authenticate with 90:94:e4:ae:57:04
[  748.102338] wlp1s0: send auth to 90:94:e4:ae:57:04 (try 1/3)
[  748.111011] wlp1s0: authenticated
[  748.115090] wlp1s0: associate with 90:94:e4:ae:57:04 (try 1/3)
[  748.120331] wlp1s0: RX AssocResp from 90:94:e4:ae:57:04 (capab=0x431 status=0 aid=5)
[  748.123798] wlp1s0: associated
[  863.498046] wlp1s0: Connection to AP 90:94:e4:ae:57:04 lost
[  869.321529] wlp1s0: authenticate with 90:94:e4:ae:57:04
[  869.357230] wlp1s0: send auth to 90:94:e4:ae:57:04 (try 1/3)
[  869.358924] wlp1s0: authenticated
[  869.360853] wlp1s0: associate with 90:94:e4:ae:57:04 (try 1/3)
[  869.371414] wlp1s0: associate with 90:94:e4:ae:57:04 (try 2/3)
[  869.404156] wlp1s0: RX AssocResp from 90:94:e4:ae:57:04 (capab=0x431 status=0 aid=5)
[  869.407747] wlp1s0: associated
[  880.075638] wlp1s0: Connection to AP 90:94:e4:ae:57:04 lost
[  885.371778] wlp1s0: authenticate with 90:94:e4:ae:57:04
[  885.407110] wlp1s0: send auth to 90:94:e4:ae:57:04 (try 1/3)
[  885.412415] wlp1s0: send auth to 90:94:e4:ae:57:04 (try 2/3)
[  885.418087] wlp1s0: authenticated
[  885.420678] wlp1s0: associate with 90:94:e4:ae:57:04 (try 1/3)
[  885.438099] wlp1s0: RX AssocResp from 90:94:e4:ae:57:04 (capab=0x431 status=0 aid=5)
[  885.442981] wlp1s0: associated
[  920.222107] wlp1s0: Connection to AP 90:94:e4:ae:57:04 lost
[  925.606409] wlp1s0: authenticate with 90:94:e4:ae:57:04
[  925.641549] wlp1s0: send auth to 90:94:e4:ae:57:04 (try 1/3)
[  925.651449] wlp1s0: authenticated
[  925.654278] wlp1s0: associate with 90:94:e4:ae:57:04 (try 1/3)
[  925.665542] wlp1s0: associate with 90:94:e4:ae:57:04 (try 2/3)
[  925.682630] wlp1s0: RX AssocResp from 90:94:e4:ae:57:04 (capab=0x431 status=0 aid=5)
[  925.686458] wlp1s0: associated
[  957.309681] wlp1s0: Connection to AP 90:94:e4:ae:57:04 lost
[  962.672870] wlp1s0: authenticate with 90:94:e4:ae:57:04
[  962.708470] wlp1s0: send auth to 90:94:e4:ae:57:04 (try 1/3)
[  962.713608] wlp1s0: authenticated
[  962.715780] wlp1s0: associate with 90:94:e4:ae:57:04 (try 1/3)
[  962.721851] wlp1s0: RX AssocResp from 90:94:e4:ae:57:04 (capab=0x431 status=0 aid=5)
[  962.725770] wlp1s0: associated
[  979.011280] wlp1s0: Connection to AP 90:94:e4:ae:57:04 lost
[  984.546979] wlp1s0: authenticate with 90:94:e4:ae:57:04
[  984.582953] wlp1s0: send auth to 90:94:e4:ae:57:04 (try 1/3)
[  984.588618] wlp1s0: authenticated
[  984.591289] wlp1s0: associate with 90:94:e4:ae:57:04 (try 1/3)
[  984.605012] wlp1s0: RX AssocResp from 90:94:e4:ae:57:04 (capab=0x431 status=0 aid=5)
[  984.609005] wlp1s0: associated
[ 1018.404914] wlp1s0: Connection to AP 90:94:e4:ae:57:04 lost
[ 1024.451208] wlp1s0: authenticate with 90:94:e4:ae:57:04
[ 1024.486609] wlp1s0: send auth to 90:94:e4:ae:57:04 (try 1/3)
[ 1024.488267] wlp1s0: authenticated
[ 1024.489342] wlp1s0: associate with 90:94:e4:ae:57:04 (try 1/3)
[ 1024.498591] wlp1s0: RX AssocResp from 90:94:e4:ae:57:04 (capab=0x431 status=0 aid=5)
[ 1024.505469] wlp1s0: associated
[ 1050.639659] wlp1s0: Connection to AP 90:94:e4:ae:57:04 lost
[ 1055.881744] wlp1s0: authenticate with 90:94:e4:ae:57:04
[ 1055.917073] wlp1s0: send auth to 90:94:e4:ae:57:04 (try 1/3)
[ 1055.929066] wlp1s0: authenticated
[ 1055.932929] wlp1s0: associate with 90:94:e4:ae:57:04 (try 1/3)
[ 1055.943680] wlp1s0: RX AssocResp from 90:94:e4:ae:57:04 (capab=0x431 status=0 aid=5)
[ 1055.947822] wlp1s0: associated
[ 1066.503649] wlp1s0: Connection to AP 90:94:e4:ae:57:04 lost
[ 1072.042959] wlp1s0: authenticate with 90:94:e4:ae:57:04
[ 1072.078245] wlp1s0: send auth to 90:94:e4:ae:57:04 (try 1/3)
[ 1072.083983] wlp1s0: authenticated
[ 1072.089416] wlp1s0: associate with 90:94:e4:ae:57:04 (try 1/3)
[ 1072.103901] wlp1s0: RX AssocResp from 90:94:e4:ae:57:04 (capab=0x431 status=0 aid=5)
[ 1072.108836] wlp1s0: associated
[ 1090.299706] wlp1s0: Connection to AP 90:94:e4:ae:57:04 lost
[ 1096.079461] wlp1s0: authenticate with 90:94:e4:ae:57:04
[ 1096.114731] wlp1s0: send auth to 90:94:e4:ae:57:04 (try 1/3)
[ 1096.117885] wlp1s0: authenticated
[ 1096.120743] wlp1s0: associate with 90:94:e4:ae:57:04 (try 1/3)
[ 1096.127340] wlp1s0: RX AssocResp from 90:94:e4:ae:57:04 (capab=0x431 status=0 aid=5)
[ 1096.131759] wlp1s0: associated
[ 1595.536244] pcieport 0000:00:1c.0: AER: Corrected error received: id=00e0
[ 1595.536250] pcieport 0000:00:1c.0: PCIe Bus Error: severity=Corrected, type=Data Link Layer, id=00e0(Transmitter ID)
[ 1595.536254] pcieport 0000:00:1c.0:   device [8086:9d15] error status/mask=00001000/00002000
[ 1595.536257] pcieport 0000:00:1c.0:    [12] Replay Timer Timeout  

```

Suprisingly, at the startup there is this messages, that i think, indicate an error with the firmware:
> 
[   36.595893] ath10k_pci 0000:01:00.0: enabling device (0000 -> 0002)
[   36.597019] ath10k_pci 0000:01:00.0: pci irq msi oper_irq_mode 2 irq_mode 0 reset_mode 0
[B][   36.920918] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/pre-cal-pci-0000:01:00.0.bin failed with error -2
[   36.920929] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/cal-pci-0000:01:00.0.bin failed with error -2
[   36.926765] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware-6.bin failed with error -2
[   36.934222] ath10k_pci 0000:01:00.0: qca9377 hw1.1 target 0x05020001 chip_id 0x003821ff sub 1a3b:2251[/B]
[   36.934224] ath10k_pci 0000:01:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[   36.934696] ath10k_pci 0000:01:00.0: firmware ver WLAN.TF.1.0-00002-QCATFSWPZ-5 api 5 features ignore-otp crc32 c3e0d04f
[   37.021207] ath10k_pci 0000:01:00.0: board_file api 2 bmi_id N/A crc32 8aedfa4a
[   37.654305] ath10k_pci 0000:01:00.0: htt-ver 3.44 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[   37.672575] ath10k_pci 0000:01:00.0 wlp1s0: renamed from wlan0


The wlp1s0 related messages just show the effect of the bluetooth and that kinda explain the low-speed, when i turned off the bluetooth, this messages stopped showing.
Also, i think the Bluetooth labeled messages doesn't show anything useful.

This is the information of my card (lspci -vvv):
```

01:00.0 Network controller: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter (rev 31)
    Subsystem: AzureWave QCA9377 802.11ac Wireless Network Adapter
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 127
    Region 0: Memory at ef000000 (64-bit, non-prefetchable) [size=2M]
    Capabilities: [40] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [50] MSI: Enable+ Count=1/8 Maskable+ 64bit-
        Address: fee00338  Data: 0000
        Masking: 000000fe  Pending: 00000000
    Capabilities: [70] Express (v2) Endpoint, MSI 00
        DevCap:    MaxPayload 256 bytes, PhantFunc 0, Latency L0s unlimited, L1 <64us
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset- SlotPowerLimit 10.000W
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 256 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr+ UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Exit Latency L0s <4us, L1 <64us
            ClockPM+ Surprise- LLActRep- BwNot- ASPMOptComp+
        LnkCtl:    ASPM L0s L1 Enabled; RCB 64 bytes Disabled- CommClk+
            ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        DevCap2: Completion Timeout: Not Supported, TimeoutDis+, LTR+, OBFF Via message
        DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-, LTR+, OBFF Disabled
        LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-
             Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
             Compliance De-emphasis: -6dB
        LnkSta2: Current De-emphasis Level: -6dB, EqualizationComplete-, EqualizationPhase1-
             EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
    Capabilities: [100 v2] Advanced Error Reporting
        UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UESvrt:    DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
        CESta:    RxErr- BadTLP+ BadDLLP+ Rollover- Timeout+ NonFatalErr-
        CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
        AERCap:    First Error Pointer: 00, GenCap- CGenEn- ChkCap- ChkEn-
    Capabilities: [148 v1] Virtual Channel
        Caps:    LPEVC=0 RefClk=100ns PATEntryBits=1
        Arb:    Fixed- WRR32- WRR64- WRR128-
        Ctrl:    ArbSelect=Fixed
        Status:    InProgress-
        VC0:    Caps:    PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
            Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
            Ctrl:    Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
            Status:    NegoPending- InProgress-
    Capabilities: [168 v1] Device Serial Number 00-00-00-00-00-00-00-00
    Capabilities: [178 v1] Latency Tolerance Reporting
        Max snoop latency: 3145728ns
        Max no snoop latency: 3145728ns
    Capabilities: [180 v1] L1 PM Substates
        L1SubCap: PCI-PM_L1.2+ PCI-PM_L1.1+ ASPM_L1.2+ ASPM_L1.1+ L1_PM_Substates+
              PortCommonModeRestoreTime=50us PortTPowerOnTime=10us
        L1SubCtl1: PCI-PM_L1.2+ PCI-PM_L1.1+ ASPM_L1.2+ ASPM_L1.1+
               T_CommonMode=0us LTR1.2_Threshold=163840ns
        L1SubCtl2: T_PwrOn=44us
    Kernel driver in use: ath10k_pci
    Kernel modules: ath10k_pci

```

Any idea?
I have not modified the driver as it came with the Ubuntu installation. 
I have Ubuntu 18 upgraded from 16 and kernel 4.15.0-39-generic

Thanks for reading.
I have been looking up for this problem for a long time now and i couldn't find anything useful;
 so i'd really aprecciate a hand with this trouble.

---

### Post by vichoko on 2018-12-02
So i managed to fix this issue downloading the missing firmware shown in the dmesg error from here: [https://github.com/kvalo/ath10k-firmware](https://github.com/kvalo/ath10k-firmware)
Inspired by some of the answers here: [https://askubuntu.com/questions/607707/ath10k-installation](https://askubuntu.com/questions/607707/ath10k-installation)

As the errors stated:
```

[B][   36.920918] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/pre-cal-pci-0000:01:00.0.bin failed with error -2
[   36.920929] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/cal-pci-0000:01:00.0.bin failed with error -2
[   36.926765] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware-6.bin failed with error -2[/B]

```
I found the missing firmware bin here: [https://github.com/kvalo/ath10k-firmware/blob/master/QCA9377/hw1.0/WLAN.TF.2.1/firmware-6.bin_WLAN.TF.2.1-00021-QCARMSWP-1](https://github.com/kvalo/ath10k-firmware/blob/master/QCA9377/hw1.0/WLAN.TF.2.1/firmware-6.bin_WLAN.TF.2.1-00021-QCARMSWP-1)

I put the firmware file in the path shown in dmesg error, renamed it and rebooted, and it worked.
Sadly i couldn't find replacement for the **pre-cal-pci-0000:01:00.0.bin and [B]cal-pci-0000:01:00.0.bin,**[/B] but as now the synthoms dissipated and everything works fine to the date, it seems that those are not extremely necessary.

My new dmesg log show some errors but the bluetooth + wifi issue was corrected. This is the first time since i bought the computer that i can listen to music with my bluetooth speaker without interruptions.

For comparison this is my new dmesg versus the former:

NEW:
```

...
[   38.198724] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input11
[   38.198783] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input12
[   38.198838] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input13
[   38.198896] input: HDA Intel PCH HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input14
[   38.200148] input: HDA Intel PCH HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input15
[   38.236248] dw-apb-uart.2: ttyS4 at MMIO 0xef234000 (irq = 20, base_baud = 115200) is a 16550A
[B][   38.294159] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/pre-cal-pci-0000:01:00.0.bin failed with error -2
[   38.294170] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/cal-pci-0000:01:00.0.bin failed with error -2
[   38.298356] ath10k_pci 0000:01:00.0: qca9377 hw1.1 target 0x05020001 chip_id 0x003821ff sub 1a3b:2251
[   38.298358] ath10k_pci 0000:01:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[    38.298771] ath10k_pci 0000:01:00.0: firmware ver  WLAN.TF.2.1-00021-QCARMSWP-1 api 6 features wowlan,ignore-otp crc32  42e41877
[   38.364652] ath10k_pci 0000:01:00.0: board_file api 2 bmi_id N/A crc32 8aedfa4a
[   38.693223] Adding 9765372k swap on /dev/mapper/cryptswap1.  Priority:-2 extents:1 across:9765372k SSFS
[   38.956083] ath10k_pci 0000:01:00.0: Unknown eventid: 3
[   38.970788] ath10k_pci 0000:01:00.0: Unknown eventid: 118809
[   38.973686] ath10k_pci 0000:01:00.0: Unknown eventid: 90118
[   38.974550] ath10k_pci 0000:01:00.0: htt-ver 3.56 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1[/B]
[B][   38.981246] ath: EEPROM regdomain: 0x6a
[   38.981247] ath: EEPROM indicates we should expect a direct regpair map
[   38.981248] ath: Country alpha2 being used: 00
[   38.981248] ath: Regpair used: 0x6a
[   38.984847] ath10k_pci 0000:01:00.0 wlp1s0: renamed from wlan0[/B]
[B][   39.035597] Bluetooth: Core ver 2.22
[   39.035610] NET: Registered protocol family 31
[   39.035610] Bluetooth: HCI device and connection manager initialized
[   39.035612] Bluetooth: HCI socket layer initialized
[   39.035614] Bluetooth: L2CAP socket layer initialized
[   39.035617] Bluetooth: SCO socket layer initialized[/B]
[   39.059804] media: Linux media interface: v0.10
[   39.065080] Linux video capture interface: v2.00
[   39.188297] usbcore: registered new interface driver btusb
[   39.217783] uvcvideo: Found UVC 1.00 device USB2.0 HD UVC WebCam (13d3:56a2)
[   39.219670] uvcvideo 1-6:1.0: Entity type for entity Realtek Extended Controls Unit was not initialized!
[   39.219672] uvcvideo 1-6:1.0: Entity type for entity Extension 4 was not initialized!
[   39.219673] uvcvideo 1-6:1.0: Entity type for entity Processing 2 was not initialized!
[   39.219674] uvcvideo 1-6:1.0: Entity type for entity Camera 1 was not initialized!
[   39.219753] input: USB2.0 HD UVC WebCam: USB2.0 HD as /devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/input/input16
[   39.219826] usbcore: registered new interface driver uvcvideo
[   39.219827] USB Video Class driver (1.1.1)
[   44.627352] EXT4-fs (sda4): mounted filesystem with ordered data mode. Opts: (null)
[    44.685726] audit: type=1400 audit(1517155104.232:2): apparmor="STATUS"  operation="profile_load" profile="unconfined" name="libreoffice-senddoc"  pid=1002 comm="apparmor_parser"
[   44.685730] audit: type=1400  audit(1517155104.232:3): apparmor="STATUS" operation="profile_load"  profile="unconfined" name="libreoffice-xpdfimport" pid=1004  comm="apparmor_parser"
[   44.685756] audit: type=1400  audit(1517155104.232:4): apparmor="STATUS" operation="profile_load"  profile="unconfined" name="libreoffice-oopslash" pid=1001  comm="apparmor_parser"
[   44.685896] audit: type=1400  audit(1517155104.232:5): apparmor="STATUS" operation="profile_load"  profile="unconfined" name="/usr/bin/man" pid=1000 comm="apparmor_parser"
[    44.685899] audit: type=1400 audit(1517155104.232:6): apparmor="STATUS"  operation="profile_load" profile="unconfined" name="man_filter" pid=1000  comm="apparmor_parser"
[   44.685901] audit: type=1400  audit(1517155104.232:7): apparmor="STATUS" operation="profile_load"  profile="unconfined" name="man_groff" pid=1000 comm="apparmor_parser"
[    44.687191] audit: type=1400 audit(1517155104.232:8): apparmor="STATUS"  operation="profile_load" profile="unconfined" name="/sbin/dhclient"  pid=997 comm="apparmor_parser"
[   44.687194] audit: type=1400  audit(1517155104.232:9): apparmor="STATUS" operation="profile_load"  profile="unconfined"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=997  comm="apparmor_parser"
[   44.687196] audit: type=1400  audit(1517155104.232:10): apparmor="STATUS" operation="profile_load"  profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper"  pid=997 comm="apparmor_parser"
[   44.687199] audit: type=1400  audit(1517155104.232:11): apparmor="STATUS" operation="profile_load"  profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script"  pid=997 comm="apparmor_parser"
[   44.909221] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   44.909222] Bluetooth: BNEP filters: protocol multicast
[   44.909225] Bluetooth: BNEP socket layer initialized
[   45.204105] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[   45.206577] pcieport 0000:00:1c.0: AER: Multiple Corrected error received: id=00e0
[   45.206586] pcieport 0000:00:1c.0: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e0(Receiver ID)
[   45.206590] pcieport 0000:00:1c.0:   device [8086:9d15] error status/mask=00000081/00002000
[   45.206593] pcieport 0000:00:1c.0:    [ 0] Receiver Error         (First)
[   45.206595] pcieport 0000:00:1c.0:    [ 7] Bad DLLP              
[   45.206599] pcieport 0000:00:1c.0: AER: Multiple Corrected error received: id=00e0
[   45.206605] pcieport 0000:00:1c.0: can't find device of ID00e0
[   45.206606] pcieport 0000:00:1c.0: AER: Multiple Corrected error received: id=00e0
[   45.206612] pcieport 0000:00:1c.0: can't find device of ID00e0
[   45.206613] pcieport 0000:00:1c.0: AER: Multiple Corrected error received: id=00e0
[   45.206619] pcieport 0000:00:1c.0: can't find device of ID00e0
[   45.241957] pcieport 0000:00:1c.0: AER: Multiple Corrected error received: id=00e0
[   45.241966] pcieport 0000:00:1c.0: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e0(Receiver ID)
[   45.241969] pcieport 0000:00:1c.0:   device [8086:9d15] error status/mask=00000001/00002000
[   45.241972] pcieport 0000:00:1c.0:    [ 0] Receiver Error         (First)
[   45.241976] pcieport 0000:00:1c.0: AER: Multiple Corrected error received: id=00e0
[   45.241982] pcieport 0000:00:1c.0: can't find device of ID00e0
[   45.241983] pcieport 0000:00:1c.0: AER: Multiple Corrected error received: id=00e0
[   45.241989] pcieport 0000:00:1c.0: can't find device of ID00e0
[   45.241990] pcieport 0000:00:1c.0: AER: Multiple Corrected error received: id=00e0
[   45.241996] pcieport 0000:00:1c.0: can't find device of ID00e0
[   45.241997] pcieport 0000:00:1c.0: AER: Multiple Corrected error received: id=00e0
[   45.242003] pcieport 0000:00:1c.0: can't find device of ID00e0
[   45.962670] ath10k_pci 0000:01:00.0: Unknown eventid: 3
[   45.977334] ath10k_pci 0000:01:00.0: Unknown eventid: 118809
[   45.980223] ath10k_pci 0000:01:00.0: Unknown eventid: 90118
[   45.992804] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[   46.077400] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[   50.965405] wlp1s0: authenticate with 90:94:e4:ae:57:04
[   51.001178] wlp1s0: send auth to 90:94:e4:ae:57:04 (try 1/3)
[   51.003073] wlp1s0: authenticated
[   51.004174] wlp1s0: associate with 90:94:e4:ae:57:04 (try 1/3)
[   51.008442] wlp1s0: RX AssocResp from 90:94:e4:ae:57:04 (capab=0x431 status=0 aid=8)
[   51.010989] wlp1s0: associated
[   51.040950] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready
[   54.805025] Could not find key with description: [bb4b4a20210cb4eb]
[   54.805029] process_request_key_err: No key
[   54.805030] Could not find valid key in user session keyring for sig specified in mount option: [bb4b4a20210cb4eb]
[   54.805031] One or more global auth toks could not properly register; rc = [-2]
[   54.805032] Error parsing options; rc = [-2]
[   58.497802] Bluetooth: RFCOMM TTY layer initialized
[   58.497820] Bluetooth: RFCOMM socket layer initialized
[   58.497833] Bluetooth: RFCOMM ver 1.11
[   59.514335] rfkill: input handler disabled

```

Former:
```

[   36.520110] RAPL PMU: hw unit of domain pp1-gpu 2^-14 Joules
[   36.520111] RAPL PMU: hw unit of domain psys 2^-14 Joules
[   36.520314] cfg80211: Loaded X.509 cert 'sforshee: 00b28ddf47aef9cea7'
[   36.521134] asus_wmi: ASUS WMI generic driver loaded
[   36.523465] asus_wmi: Initialization: 0x1
[   36.523599] asus_wmi: BIOS WMI version: 9.0
[   36.523690] asus_wmi: SFUN value: 0x21
[   36.527136] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input7
[   36.527388] asus_wmi: Number of fans: 0
[   36.538787] mei_me 0000:00:16.0: enabling device (0000 -> 0002)
[   36.556765] AVX2 version of gcm_enc/dec engaged.
[   36.556766] AES CTR mode by8 optimization enabled
[   36.560643] intel-lpss 0000:00:1e.0: enabling device (0000 -> 0002)
[   36.561122] idma64 idma64.2: Found Intel integrated DMA 64-bit
[   36.561763] intel-lpss 0000:00:1e.2: enabling device (0000 -> 0002)
[   36.562205] idma64 idma64.3: Found Intel integrated DMA 64-bit[B]
[   36.595893] ath10k_pci 0000:01:00.0: enabling device (0000 -> 0002)
[   36.597019] ath10k_pci 0000:01:00.0: pci irq msi oper_irq_mode 2 irq_mode 0 reset_mode 0[/B]
[   36.657651] intel_rapl: Found RAPL domain package
[   36.657653] intel_rapl: Found RAPL domain core
[   36.657654] intel_rapl: Found RAPL domain uncore
[   36.657656] intel_rapl: Found RAPL domain dram
[   36.666807] snd_hda_intel 0000:00:1f.3: enabling device (0000 -> 0002)
[   36.670574] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[   36.673217] hid-multitouch 0018:04F3:3057.0001: Ignoring the extra HID_DG_INPUTMODE
[   36.673792] input: ELAN1300:00 04F3:3057 Touchpad as /devices/pci0000:00/0000:00:15.1/i2c_designware.1/i2c-7/i2c-ELAN1300:00/0018:04F3:3057.0001/input/input9
[   36.673893] hid-multitouch 0018:04F3:3057.0001: input,hidraw0: I2C HID v1.00 Mouse [ELAN1300:00 04F3:3057] on i2c-ELAN1300:00
[   36.713288] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC295: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   36.713291] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   36.713293] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[   36.713294] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[   36.713295] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[   36.713297] snd_hda_codec_realtek hdaudioC0D0:      Mic=0x12
[   36.764602] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1f.3/sound/card0/input10
[   36.765973] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input11
[   36.766041] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input12
[   36.766093] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input13
[   36.766138] input: HDA Intel PCH HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input14
[   36.766212] input: HDA Intel PCH HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input15
[   36.784308] dw-apb-uart.2: ttyS4 at MMIO 0xef234000 (irq = 20, base_baud = 115200) is a 16550A
[B][   36.920918] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/pre-cal-pci-0000:01:00.0.bin failed with error -2
[   36.920929] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/cal-pci-0000:01:00.0.bin failed with error -2
[   36.926765] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware-6.bin failed with error -2
[   36.934222] ath10k_pci 0000:01:00.0: qca9377 hw1.1 target 0x05020001 chip_id 0x003821ff sub 1a3b:2251
[   36.934224] ath10k_pci 0000:01:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[   36.934696] ath10k_pci 0000:01:00.0: firmware ver WLAN.TF.1.0-00002-QCATFSWPZ-5 api 5 features ignore-otp crc32 c3e0d04f
[   37.021207] ath10k_pci 0000:01:00.0: board_file api 2 bmi_id N/A crc32 8aedfa4a
[/B][   37.371631] EXT4-fs (sda4): mounted filesystem with ordered data mode. Opts: (null)
[   37.432341] audit: type=1400 audit(1542665986.159:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-oopslash" pid=877 comm="apparmor_parser"
[   37.432504] audit: type=1400 audit(1542665986.159:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/man" pid=876 comm="apparmor_parser"
[   37.432508] audit: type=1400 audit(1542665986.159:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_filter" pid=876 comm="apparmor_parser"
[   37.432511] audit: type=1400 audit(1542665986.159:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_groff" pid=876 comm="apparmor_parser"
[   37.433357] audit: type=1400 audit(1542665986.159:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-senddoc" pid=878 comm="apparmor_parser"
[   37.433675] audit: type=1400 audit(1542665986.159:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-xpdfimport" pid=880 comm="apparmor_parser"
[   37.434367] audit: type=1400 audit(1542665986.159:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=873 comm="apparmor_parser"
[   37.434371] audit: type=1400 audit(1542665986.159:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=873 comm="apparmor_parser"
[   37.434374] audit: type=1400 audit(1542665986.159:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=873 comm="apparmor_parser"
[   37.434377] audit: type=1400 audit(1542665986.159:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=873 comm="apparmor_parser"
[   37.454324] Adding 9765372k swap on /dev/mapper/cryptswap1.  Priority:-2 extents:1 across:9765372k SSFS
[B][   37.507381] Bluetooth: Core ver 2.22
[   37.507397] NET: Registered protocol family 31
[   37.507398] Bluetooth: HCI device and connection manager initialized
[   37.507400] Bluetooth: HCI socket layer initialized
[   37.507402] Bluetooth: L2CAP socket layer initialized
[   37.507407] Bluetooth: SCO socket layer initialized
[/B][   37.551441] media: Linux media interface: v0.10
[   37.558574] Linux video capture interface: v2.00
[   37.636415] usbcore: registered new interface driver btusb
[B][   37.654305] ath10k_pci 0000:01:00.0: htt-ver 3.44 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[   37.662861] ath: EEPROM regdomain: 0x6a
[   37.662862] ath: EEPROM indicates we should expect a direct regpair map
[   37.662864] ath: Country alpha2 being used: 00
[   37.662865] ath: Regpair used: 0x6a
[   37.672575] ath10k_pci 0000:01:00.0 wlp1s0: renamed from wlan0[/B]

```

Seen this, i conclude that now the device is loading the newer firmware instead of the version-5 that had before, and it seems that this did the trick for fixing the problems.

---

