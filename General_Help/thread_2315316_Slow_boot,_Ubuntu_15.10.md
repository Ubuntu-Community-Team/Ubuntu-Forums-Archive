---
title: "Slow boot, Ubuntu 15.10"
date: 2016-02-27
forum: General Help
---

### Post by brianmacdiarmuide on 2016-02-27
This is my first post, apologies if I'm posting in the wrong place or something like that.

I am using Ubuntu 15.10 on a laptop with 6gigs of ram and intel i3 dual 2.4ghz.

I see that my boot time in all, is ~71 secs, which seems like a long time. 
I would love to take that down as much as possible. The dmesg output is below,
 I cut out the first 8 secs as there doesn't appear to be any bottlenecks.

Bottlenecks are easy to see due to the timestamps, but I just don't know whether those 
bottlenecks are simply to be expected with my system specs, or whether I have some problems,
 and I'm not sure how to go about fixing them if I do. I have tried bootchart before, and found that 
It just never produced an output file for me. I will try again, but for now, there is the below output. 
Anything else I should provide, please let me know, help much appreciated.

```

[    8.396940] psmouse serio1: elantech: retrying ps2 command 0xf8 (1).
[    9.022344] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input7
[   14.183027] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   15.326946] systemd[1]: RTC configured in localtime, applying delta of 0 minutes to system time.
[   15.894326] systemd[1]: Failed to insert module 'kdbus': Function not implemented
[   16.056315] systemd[1]: systemd 225 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID -ELFUTILS +KMOD -IDN)
[   16.056485] systemd[1]: Detected architecture x86-64.
[   16.089975] systemd[1]: Set hostname to <DeepThought>.
[   20.150173] systemd[1]: Reached target Remote File Systems (Pre).
[   20.150268] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[   20.150301] systemd[1]: Created slice Root Slice.
[   20.150354] systemd[1]: Listening on Journal Socket.
[   20.150394] systemd[1]: Listening on udev Kernel Socket.
[   20.150490] systemd[1]: Created slice User and Session Slice.
[   20.150502] systemd[1]: Reached target User and Group Name Lookups.
[   20.150584] systemd[1]: Created slice System Slice.
[   20.151176] systemd[1]: Started Read required files in advance.
[   20.152031] systemd[1]: Mounting Huge Pages File System...
[   20.152695] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[   20.152856] systemd[1]: Created slice system-systemd\x2dfsck.slice.
[   20.153638] systemd[1]: Mounting Debug File System...
[   20.154288] systemd[1]: Started Braille Device Support.
[   20.154706] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[   20.154845] systemd[1]: Listening on Journal Audit Socket.
[   20.154873] systemd[1]: Reached target Encrypted Volumes.
[   20.154947] systemd[1]: Listening on udev Control Socket.
[   20.155003] systemd[1]: Listening on Journal Socket (/dev/log).
[   20.155593] systemd[1]: Starting udev Coldplug all Devices...
[   20.156186] systemd[1]: Starting Setup Virtual Console...
[   20.156733] systemd[1]: Starting Uncomplicated firewall...
[   20.156793] systemd[1]: Reached target Slices.
[   20.412713] systemd[1]: Starting Load Kernel Modules...
[   20.412823] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[   20.413383] systemd[1]: Mounting POSIX Message Queue File System...
[   20.414056] systemd[1]: Starting Increase datagram queue length...
[   20.684142] systemd[1]: Created slice system-getty.slice.
[   20.684208] systemd[1]: Listening on fsck to fsckd communication Socket.
[   20.685057] systemd[1]: Mounted Debug File System.
[   20.685138] systemd[1]: Mounted POSIX Message Queue File System.
[   20.685197] systemd[1]: Mounted Huge Pages File System.
[   20.685547] systemd[1]: Started Create list of required static device nodes for the current kernel.
[   20.686364] systemd[1]: Started Setup Virtual Console.
[   20.686778] systemd[1]: Started Increase datagram queue length.
[   20.695921] systemd[1]: Listening on Syslog Socket.
[   20.696717] systemd[1]: Starting Journal Service...
[   20.697672] systemd[1]: Starting Create Static Device Nodes in /dev...
[   20.975238] lp: driver loaded but no devices found
[   20.979099] ppdev: user-space parallel port driver
[   21.114462] systemd[1]: Started Load Kernel Modules.
[   21.115352] systemd[1]: Starting Apply Kernel Variables...
[   21.116031] systemd[1]: Mounting FUSE Control File System...
[   21.118595] systemd[1]: Mounted FUSE Control File System.
[   21.439958] systemd[1]: Started Apply Kernel Variables.
[   21.516060] ip_tables: (C) 2000-2006 Netfilter Core Team
[   21.658270] systemd[1]: Started Journal Service.
[   21.670578] nf_conntrack version 0.5.0 (65536 buckets, 262144 max)
[   21.985307] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   24.799083] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   25.062796] systemd-journald[318]: Received request to flush runtime journal from PID 1
[   25.331151] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
[   25.331171] intel ips 0000:00:1f.6: found PCI INT A -> IRQ 11
[   25.331408] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
[   25.391694] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x0000000000000400-0x000000000000047F (\PMIO) (20150619/utaddress-254)
[   25.391703] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   25.391707] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20150619/utaddress-254)
[   25.391711] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   25.391712] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20150619/utaddress-254)
[   25.391715] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x000000000000053F (\_SB_.PCI0.GPIO) (20150619/utaddress-254)
[   25.391719] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   25.391720] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20150619/utaddress-254)
[   25.391723] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x000000000000053F (\_SB_.PCI0.GPIO) (20150619/utaddress-254)
[   25.391726] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   25.391727] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   25.452177] mei_me 0000:00:16.0: found PCI INT A -> IRQ 10
[   25.452191] mei_me 0000:00:16.0: sharing IRQ 10 with 0000:00:1a.0
[   25.452202] mei_me 0000:00:16.0: sharing IRQ 10 with 0000:00:1c.1
[   25.452250] mei_me 0000:00:16.0: sharing IRQ 10 with 0000:01:00.0
[   25.572954] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   26.304414] acer_wmi: Acer Laptop ACPI-WMI Extras
[   26.304433] acer_wmi: Function bitmap for Communication Button: 0x1
[   26.305223] input: Acer WMI hotkeys as /devices/virtual/input/input9
[   26.305495] input: Acer BMA150 accelerometer as /devices/virtual/input/input10
[   26.330101] kvm: VM_EXIT_LOAD_IA32_PERF_GLOBAL_CTRL does not work properly. Using workaround
[   26.692539] snd_hda_intel 0000:00:1b.0: found PCI INT A -> IRQ 10
[   26.918379] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC272X: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   26.918386] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   26.918390] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[   26.918392] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[   26.918394] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[   26.918397] snd_hda_codec_realtek hdaudioC0D0:      Internal Mic=0x19
[   26.918399] snd_hda_codec_realtek hdaudioC0D0:      Mic=0x18
[   26.927417] input: HDA Intel MID Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   26.927550] input: HDA Intel MID Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   26.996599] ath9k 0000:02:00.0: found PCI INT A -> IRQ 11
[   26.996614] ath9k 0000:02:00.0: sharing IRQ 11 with 0000:00:1c.0
[   27.003806] ath: phy0: Enable LNA combining
[   27.005001] ath: phy0: ASPM enabled: 0x43
[   27.005003] ath: EEPROM regdomain: 0x65
[   27.005004] ath: EEPROM indicates we should expect a direct regpair map
[   27.005006] ath: Country alpha2 being used: 00
[   27.005007] ath: Regpair used: 0x65
[   27.223029] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   27.223413] ieee80211 phy0: Atheros AR9485 Rev:1 mem=0xffffc90001100000, irq=11
[   27.629150] media: Linux media interface: v0.10
[   27.755710] Linux video capture interface: v2.00
[   28.219934] uvcvideo: Found UVC 1.00 device WebCam (04f2:b209)
[   28.222743] input: WebCam as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input13
[   28.222877] usbcore: registered new interface driver uvcvideo
[   28.222879] USB Video Class driver (1.1.1)
[   28.659489] cfg80211: World regulatory domain updated:
[   28.659496] cfg80211:  DFS Master region: unset
[   28.659497] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   28.659500] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   28.659502] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   28.659504] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[   28.659506] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[   28.659508] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[   28.659510] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[   28.659511] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[   28.659513] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[   28.839130] Adding 6143996k swap on /dev/sda6.  Priority:-1 extents:1 across:6143996k FS
[   32.062985] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[   33.986043] audit: type=1400 audit(1456603152.463:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=700 comm="apparmor_parser"
[   33.986053] audit: type=1400 audit(1456603152.463:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=700 comm="apparmor_parser"
[   34.096829] audit: type=1400 audit(1456603152.575:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=700 comm="apparmor_parser"
[   34.096837] audit: type=1400 audit(1456603152.575:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=700 comm="apparmor_parser"
[   34.096842] audit: type=1400 audit(1456603152.575:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=700 comm="apparmor_parser"
[   34.096847] audit: type=1400 audit(1456603152.575:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=700 comm="apparmor_parser"
[   34.212709] audit: type=1400 audit(1456603152.691:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="system_tor" pid=700 comm="apparmor_parser"
[   34.566830] audit: type=1400 audit(1456603153.043:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=700 comm="apparmor_parser"
[   34.566842] audit: type=1400 audit(1456603153.043:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=700 comm="apparmor_parser"
[   34.566847] audit: type=1400 audit(1456603153.043:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=700 comm="apparmor_parser"
[   48.581622] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   48.606000] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   48.610678] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   48.625370] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   48.853570] tg3 0000:01:00.0 eth0: Link is down
[   49.512687] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   51.236325] wlan0: authenticate with 5c:0a:5b:79:3c:52
[   51.256429] wlan0: send auth to 5c:0a:5b:79:3c:52 (try 1/3)
[   51.260219] wlan0: authenticated
[   51.260404] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[   51.262734] wlan0: associate with 5c:0a:5b:79:3c:52 (try 1/3)
[   51.265571] wlan0: RX AssocResp from 5c:0a:5b:79:3c:52 (capab=0x411 status=0 aid=1)
[   51.265679] wlan0: associated
[   51.265693] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   61.022739] Ebtables v2.0 registered
[   61.269894] Bluetooth: Core ver 2.20
[   61.269957] NET: Registered protocol family 31
[   61.269959] Bluetooth: HCI device and connection manager initialized
[   61.269965] Bluetooth: HCI socket layer initialized
[   61.269968] Bluetooth: L2CAP socket layer initialized
[   61.269974] Bluetooth: SCO socket layer initialized
[   61.273546] Netfilter messages via NETLINK v0.30.
[   61.295983] Guest personality initialized and is inactive
[   61.296072] VMCI host device registered (name=vmci, major=10, minor=56)
[   61.296073] Initialized host personality
[   61.323110] NET: Registered protocol family 40
[   61.379737] bridge: automatic filtering via arp/ip/ip6tables has been deprecated. Update your scripts to load br_netfilter if you need this.
[   61.431020] device virbr0-nic entered promiscuous mode
[   61.562629] virbr0: port 1(virbr0-nic) entered listening state
[   61.562654] virbr0: port 1(virbr0-nic) entered listening state
[   61.604723] virbr0: port 1(virbr0-nic) entered disabled state
[   64.853362] device eth0 entered promiscuous mode
[   65.742052] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   65.742057] Bluetooth: BNEP filters: protocol multicast
[   65.742064] Bluetooth: BNEP socket layer initialized
[   71.204795] [UFW BLOCK] IN=wlan0 OUT= MAC= SRC=fe80:0000:0000:0000:76de:2bff:fea5:05a8 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
[   71.204825] [UFW BLOCK] IN=wlan0 OUT= MAC= SRC=fe80:0000:0000:0000:76de:2bff:fea5:05a8 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
[   71.215098] [UFW BLOCK] IN=wlan0 OUT= MAC= SRC=fe80:0000:0000:0000:76de:2bff:fea5:05a8 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
[   71.215126] [UFW BLOCK] IN=wlan0 OUT= MAC= SRC=fe80:0000:0000:0000:76de:2bff:fea5:05a8 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=UDP SPT=8612 DPT=8610 LEN=24 

```

---

### Post by no-spam-to-me on 2016-02-27
I have just the same problem with different hardware!
```

heiko@heiko-TravelMate-5740ZG:~$ LC_ALL=C sudo systemd-analyze
Startup finished in 12.836s (kernel) + 40.260s (userspace) = 53.097s

```
Should I open another thread?

[HR][/HR]lshw:
[ATTACH]267559[/ATTACH]
```

heiko-travelmate-5740zg
    description: Computer
    width: 64 bits
    capabilities: smbios-2.6 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3816MiB
     *-cpu
          product: Intel(R) Pentium(R) CPU        P6000  @ 1.87GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 1199MHz
          capacity: 1866MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm popcnt lahf_lm arat dtherm cpufreq
     *-pci:0
          description: Host bridge
          product: Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Core Processor PCI Express x16 Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:3000(size=4096) memory:b4000000-b40fffff ioport:a0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Madison [Mobility Radeon HD 5650/5750 / 6530M/6550M]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:26 memory:a0000000-afffffff memory:b4000000-b401ffff ioport:3000(size=256) memory:b4040000-b405ffff
           *-multimedia
                description: Audio device
                product: Redwood HDMI Audio [Radeon HD 5000 Series]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:29 memory:b4020000-b4023fff
        *-communication
             description: Communication controller
             product: 5 Series/3400 Series Chipset HECI Controller
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:27 memory:b4106100-b410610f
        *-usb:0
             description: USB controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:b4105c00-b4105fff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.2.0-30-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.02
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: Integrated Rate Matching Hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=6 speed=480Mbit/s
                 *-usb
                      description: Video
                      product: 1.3M WebCam
                      vendor: XPA321C86
                      physical id: 1
                      bus info: usb@1:1.1
                      version: 0.09
                      capabilities: usb-2.00
                      configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
        *-multimedia
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:28 memory:b4100000-b4103fff
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:2000(size=4096) memory:b3000000-b3ffffff ioport:b0000000(size=16777216)
           *-network
                description: Ethernet interface
                product: NetLink BCM57780 Gigabit Ethernet PCIe
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: enp2s0
                version: 01
                serial: xx:xx:xx:xx:xx:xx
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 duplex=half firmware=sb latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:30 memory:b3000000-b300ffff
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:1000(size=4096) memory:b2000000-b2ffffff ioport:b1000000(size=16777216)
           *-network
                description: Network controller
                product: BCM43225 802.11b/g/n
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=bcma-pci-bridge latency=0
                resources: irq:17 memory:b2000000-b2003fff
        *-usb:1
             description: USB controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:b4105800-b4105bff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.2.0-30-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.02
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: Integrated Rate Matching Hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@2:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=8 speed=480Mbit/s
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a5
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: Mobile 5 Series Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 5 Series/3400 Series Chipset 4 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:25 ioport:4048(size=8) ioport:4054(size=4) ioport:4040(size=8) ioport:4050(size=4) ioport:4020(size=32) memory:b4105000-b41057ff
        *-serial UNCLAIMED
             description: SMBus
             product: 5 Series/3400 Series Chipset SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:b4106000-b41060ff ioport:4000(size=32)
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:ff:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:ff:00.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:ff:02.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: 1st Generation Core i3/5/7 Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:ff:02.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: 1st Generation Core i3/5/7 Processor Reserved
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:ff:02.2
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: 1st Generation Core i3/5/7 Processor Reserved
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:ff:02.3
          version: 02
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Hitachi HTS54505
             vendor: Hitachi
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: C60F
             serial: 100217PBN406B7C9GTVL
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=12429d0f
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 80fe3643-1069-4acc-ad39-293bdda9749c
                size: 461GiB
                capacity: 461GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2016-02-21 00:02:32 filesystem=ext4 lastmountpoint=/ modified=2016-02-27 12:34:02 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2016-02-27 10:20:21 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 3957MiB
                capacity: 3957MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 3957MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 3
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD-RAM UJ890AS
             vendor: MATSHITA
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: 1.00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlp3s0b1
       serial: xx:xx:xx:xx:xx:xx
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=4.2.0-30-generic firmware=666.2 ip=192.168.1.102 link=yes multicast=yes wireless=IEEE 802.11bg

```
[HR][/HR] [HR][/HR]dmesg:
```

[    0.000000] microcode: CPU0 microcode updated early to revision 0xe, date = 2013-06-26
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 4.2.0-30-generic (buildd@lgw01-60) (gcc version 5.2.1 20151010 (Ubuntu 5.2.1-22ubuntu2) ) #36-Ubuntu SMP Fri Feb 26 00:58:07 UTC 2016 (Ubuntu 4.2.0-30.36-generic 4.2.8-ckt3)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-30-generic root=UUID=80fe3643-1069-4acc-ad39-293bdda9749c ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] x86/fpu: Legacy x87 FPU detected.
[    0.000000] x86/fpu: Using 'lazy' FPU context switches.
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009cfff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000009f681fff] usable
[    0.000000] BIOS-e820: [mem 0x000000009f682000-0x000000009f6befff] reserved
[    0.000000] BIOS-e820: [mem 0x000000009f6bf000-0x000000009f735fff] usable
[    0.000000] BIOS-e820: [mem 0x000000009f736000-0x000000009f7befff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000009f7bf000-0x000000009f7defff] usable
[    0.000000] BIOS-e820: [mem 0x000000009f7df000-0x000000009f7fefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000009f7ff000-0x000000009f7fffff] usable
[    0.000000] BIOS-e820: [mem 0x000000009f800000-0x000000009fffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000feb00000-0x00000000feb03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed13fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed18000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1b000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffe80000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x0000000157ffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.6 present.
[    0.000000] DMI: Acer             TravelMate 5740ZG/TravelMate 5740ZG, BIOS V1.21 02/24/2011
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x158000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   2 base 080000000 mask FE0000000 write-back
[    0.000000]   3 base 09F800000 mask FFF800000 uncachable
[    0.000000]   4 base 100000000 mask FC0000000 write-back
[    0.000000]   5 base 140000000 mask FF0000000 write-back
[    0.000000]   6 base 150000000 mask FF8000000 write-back
[    0.000000]   7 disabled
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
[    0.000000] e820: last_pfn = 0x9f800 max_arch_pfn = 0x400000000
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01ff1000, 0x01ff1fff] PGTABLE
[    0.000000] BRK [0x01ff2000, 0x01ff2fff] PGTABLE
[    0.000000] BRK [0x01ff3000, 0x01ff3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x157e00000-0x157ffffff]
[    0.000000]  [mem 0x157e00000-0x157ffffff] page 2M
[    0.000000] BRK [0x01ff4000, 0x01ff4fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x140000000-0x157dfffff]
[    0.000000]  [mem 0x140000000-0x157dfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x120000000-0x13fffffff]
[    0.000000]  [mem 0x120000000-0x13fffffff] page 2M
[    0.000000] BRK [0x01ff5000, 0x01ff5fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x00100000-0x9f681fff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x9f5fffff] page 2M
[    0.000000]  [mem 0x9f600000-0x9f681fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x9f6bf000-0x9f735fff]
[    0.000000]  [mem 0x9f6bf000-0x9f735fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x9f7bf000-0x9f7defff]
[    0.000000]  [mem 0x9f7bf000-0x9f7defff] page 4k
[    0.000000] init_memory_mapping: [mem 0x9f7ff000-0x9f7fffff]
[    0.000000]  [mem 0x9f7ff000-0x9f7fffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x11fffffff]
[    0.000000]  [mem 0x100000000-0x11fffffff] page 2M
[    0.000000] RAMDISK: [mem 0x33f8c000-0x35fbdfff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000FE020 000024 (v02 ACRSYS)
[    0.000000] ACPI: XSDT 0x000000009F7FE120 00007C (v01 ACRSYS ACRPRDCT 00000001      01000013)
[    0.000000] ACPI: FACP 0x000000009F7FC000 0000F4 (v04 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: DSDT 0x000000009F7EA000 00E975 (v02 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: FACS 0x000000009F75A000 000040
[    0.000000] ACPI: FACS 0x000000009F75A000 000040
[    0.000000] ACPI: ASF! 0x000000009F7FD000 0000A5 (v32 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: HPET 0x000000009F7FB000 000038 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: APIC 0x000000009F7FA000 00008C (v02 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: MCFG 0x000000009F7F9000 00003C (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: SLIC 0x000000009F7E9000 000176 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: BOOT 0x000000009F7E6000 000028 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: ASPT 0x000000009F7E2000 000034 (v04 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: SSDT 0x000000009F7E1000 0009F1 (v01 PmRef  CpuPm    00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 0x000000009F7E0000 000259 (v01 PmRef  Cpu0Tst  00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 0x000000009F7DF000 00049F (v01 PmRef  ApTst    00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x0000000157ffffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x157ff8000-0x157ffcfff]
[    0.000000]  [ffffea0000000000-ffffea00055fffff] PMD -> [ffff880153800000-ffff8801575fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.000000]   Normal   [mem 0x0000000100000000-0x0000000157ffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x000000000009cfff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x000000009f681fff]
[    0.000000]   node   0: [mem 0x000000009f6bf000-0x000000009f735fff]
[    0.000000]   node   0: [mem 0x000000009f7bf000-0x000000009f7defff]
[    0.000000]   node   0: [mem 0x000000009f7ff000-0x000000009f7fffff]
[    0.000000]   node   0: [mem 0x0000000100000000-0x0000000157ffffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x0000000157ffffff]
[    0.000000] On node 0 totalpages: 1013430
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 10141 pages used for memmap
[    0.000000]   DMA32 zone: 648986 pages, LIFO batch:31
[    0.000000]   Normal zone: 5632 pages used for memmap
[    0.000000]   Normal zone: 360448 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 6 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x9f682000-0x9f6befff]
[    0.000000] PM: Registered nosave memory: [mem 0x9f736000-0x9f7befff]
[    0.000000] PM: Registered nosave memory: [mem 0x9f7df000-0x9f7fefff]
[    0.000000] PM: Registered nosave memory: [mem 0x9f800000-0x9fffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xa0000000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfeafffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfeb00000-0xfeb03fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfeb04000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed13fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed14000-0xfed17fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed18000-0xfed19fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1afff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1b000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffe7ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffe80000-0xffffffff]
[    0.000000] e820: [mem 0xa0000000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 33 pages/cpu @ffff880157c00000 s96728 r8192 d30248 u262144
[    0.000000] pcpu-alloc: s96728 r8192 d30248 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 997572
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-30-generic root=UUID=80fe3643-1069-4acc-ad39-293bdda9749c ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3873440K/4053720K available (8158K kernel code, 1238K rwdata, 3804K rodata, 1464K init, 1292K bss, 180280K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     Build-time adjustment of leaf fanout to 64.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=8
[    0.000000] NR_IRQS:16640 nr_irqs:488 16
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 1862.315 MHz processor
[    0.000044] Calibrating delay loop (skipped), value calculated using timer frequency.. 3724.63 BogoMIPS (lpj=7449260)
[    0.000048] pid_max: default: 32768 minimum: 301
[    0.000056] ACPI: Core revision 20150619
[    0.020320] ACPI: All ACPI Tables successfully acquired
[    0.020349] Security Framework initialized
[    0.020366] AppArmor: AppArmor initialized
[    0.020367] Yama: becoming mindful.
[    0.020759] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.021833] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.022419] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.022426] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.022702] Initializing cgroup subsys blkio
[    0.022707] Initializing cgroup subsys memory
[    0.022717] Initializing cgroup subsys devices
[    0.022720] Initializing cgroup subsys freezer
[    0.022723] Initializing cgroup subsys net_cls
[    0.022726] Initializing cgroup subsys perf_event
[    0.022729] Initializing cgroup subsys net_prio
[    0.022732] Initializing cgroup subsys hugetlb
[    0.022758] CPU: Physical Processor ID: 0
[    0.022759] CPU: Processor Core ID: 0
[    0.022766] mce: CPU supports 9 MCE banks
[    0.022778] CPU0: Thermal monitoring enabled (TM1)
[    0.022787] process: using mwait in idle threads
[    0.022791] Last level iTLB entries: 4KB 512, 2MB 7, 4MB 7
[    0.022793] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32, 1GB 0
[    0.023209] Freeing SMP alternatives memory: 28K (ffffffff81ea5000 - ffffffff81eac000)
[    0.189351] ftrace: allocating 30940 entries in 121 pages
[    0.210799] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.355444] smpboot: CPU0: Intel(R) Pentium(R) CPU        P6000  @ 1.87GHz (fam: 06, model: 25, stepping: 02)
[    0.355482] Performance Events: PEBS fmt1+, 16-deep LBR, Westmere events, Intel PMU driver.
[    0.355506] perf_event_intel: CPUID marked event: 'bus cycles' unavailable
[    0.355509] ... version:                3
[    0.355511] ... bit width:              48
[    0.355512] ... generic registers:      4
[    0.355513] ... value mask:             0000ffffffffffff
[    0.355514] ... max period:             000000007fffffff
[    0.355516] ... fixed-purpose events:   3
[    0.355517] ... event mask:             000000070000000f
[    0.356635] x86: Booting SMP configuration:
[    0.356638] .... node  #0, CPUs:      #1
[    0.358115] microcode: CPU1 microcode updated early to revision 0xe, date = 2013-06-26
[    0.360312] x86: Booted up 1 node, 2 CPUs
[    0.360317] smpboot: Total of 2 processors activated (7449.26 BogoMIPS)
[    0.360493] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.362001] devtmpfs: initialized
[    0.365162] evm: security.selinux
[    0.365165] evm: security.SMACK64
[    0.365166] evm: security.SMACK64EXEC
[    0.365167] evm: security.SMACK64TRANSMUTE
[    0.365168] evm: security.SMACK64MMAP
[    0.365169] evm: security.ima
[    0.365171] evm: security.capability
[    0.365256] PM: Registering ACPI NVS region [mem 0x9f736000-0x9f7befff] (561152 bytes)
[    0.365360] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.365454] pinctrl core: initialized pinctrl subsystem
[    0.365610] RTC time: 11:33:51, date: 02/27/16
[    0.365754] NET: Registered protocol family 16
[    0.371472] cpuidle: using governor ladder
[    0.376294] cpuidle: using governor menu
[    0.376384] Simple Boot Flag at 0x44 set to 0x1
[    0.376438] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.376440] ACPI: bus type PCI registered
[    0.376442] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.376546] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.376549] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.376566] PCI: Using configuration type 1 for base access
[    0.376760] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.376762] mtrr: probably your BIOS does not setup all CPUs.
[    0.376763] mtrr: corrected configuration.
[    0.379957] ACPI: Added _OSI(Module Device)
[    0.379960] ACPI: Added _OSI(Processor Device)
[    0.379961] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.379963] ACPI: Added _OSI(Processor Aggregator Device)
[    0.384746] ACPI: Executed 1 blocks of module-level executable AML code
[    0.389588] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.390149] ACPI: Dynamic OEM Table Load:
[    0.390160] ACPI: SSDT 0xFFFF880153496800 00032A (v01 PmRef  Cpu0Ist  00003000 INTL 20051117)
[    0.390961] ACPI: Dynamic OEM Table Load:
[    0.390970] ACPI: SSDT 0xFFFF880152B20000 000891 (v01 PmRef  Cpu0Cst  00003001 INTL 20051117)
[    0.392149] ACPI: Dynamic OEM Table Load:
[    0.392157] ACPI: SSDT 0xFFFF880153497000 000303 (v01 PmRef  ApIst    00003000 INTL 20051117)
[    0.392945] ACPI: Dynamic OEM Table Load:
[    0.392952] ACPI: SSDT 0xFFFF880152AC1400 000119 (v01 PmRef  ApCst    00003000 INTL 20051117)
[    0.393793] ACPI : EC: EC started
[    0.400392] ACPI: Interpreter enabled
[    0.400407] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20150619/hwxface-580)
[    0.400415] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150619/hwxface-580)
[    0.400444] ACPI: (supports S0 S3 S4 S5)
[    0.400446] ACPI: Using IOAPIC for interrupt routing
[    0.400490] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.813975] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.813984] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.814027] \_SB_.PCI0:_OSC invalid UUID
[    0.814028] _OSC request data:1 1f 0 
[    0.814033] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
[    0.814727] PCI host bridge to bus 0000:00
[    0.814732] pci_bus 0000:00: root bus resource [bus 00-fe]
[    0.814735] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.814737] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.814740] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.814742] pci_bus 0000:00: root bus resource [mem 0xa0000000-0xfebfffff window]
[    0.814752] pci 0000:00:00.0: [8086:0044] type 00 class 0x060000
[    0.814778] DMAR: BIOS has allocated no shadow GTT; disabling IOMMU for graphics
[    0.814930] pci 0000:00:01.0: [8086:0045] type 01 class 0x060400
[    0.814970] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.815156] pci 0000:00:16.0: [8086:3b64] type 00 class 0x078000
[    0.815186] pci 0000:00:16.0: reg 0x10: [mem 0xb4106100-0xb410610f 64bit]
[    0.815281] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.815451] pci 0000:00:1a.0: [8086:3b3c] type 00 class 0x0c0320
[    0.815820] pci 0000:00:1a.0: reg 0x10: [mem 0xb4105c00-0xb4105fff]
[    0.817941] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.818110] pci 0000:00:1b.0: [8086:3b56] type 00 class 0x040300
[    0.818136] pci 0000:00:1b.0: reg 0x10: [mem 0xb4100000-0xb4103fff 64bit]
[    0.818240] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.818354] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.818410] pci 0000:00:1c.0: [8086:3b42] type 01 class 0x060400
[    0.818507] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.818620] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.818678] pci 0000:00:1c.1: [8086:3b44] type 01 class 0x060400
[    0.818776] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.818947] pci 0000:00:1d.0: [8086:3b34] type 00 class 0x0c0320
[    0.819309] pci 0000:00:1d.0: reg 0x10: [mem 0xb4105800-0xb4105bff]
[    0.821431] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.821559] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.821613] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
[    0.821787] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.821841] pci 0000:00:1f.0: [8086:3b09] type 00 class 0x060100
[    0.822097] pci 0000:00:1f.2: [8086:3b29] type 00 class 0x010601
[    0.822122] pci 0000:00:1f.2: reg 0x10: [io  0x4048-0x404f]
[    0.822134] pci 0000:00:1f.2: reg 0x14: [io  0x4054-0x4057]
[    0.822146] pci 0000:00:1f.2: reg 0x18: [io  0x4040-0x4047]
[    0.822158] pci 0000:00:1f.2: reg 0x1c: [io  0x4050-0x4053]
[    0.822170] pci 0000:00:1f.2: reg 0x20: [io  0x4020-0x403f]
[    0.822182] pci 0000:00:1f.2: reg 0x24: [mem 0xb4105000-0xb41057ff]
[    0.822239] pci 0000:00:1f.2: PME# supported from D3hot
[    0.822391] pci 0000:00:1f.3: [8086:3b30] type 00 class 0x0c0500
[    0.822415] pci 0000:00:1f.3: reg 0x10: [mem 0xb4106000-0xb41060ff 64bit]
[    0.822446] pci 0000:00:1f.3: reg 0x20: [io  0x4000-0x401f]
[    0.822691] pci 0000:01:00.0: [1002:68c1] type 00 class 0x030000
[    0.822714] pci 0000:01:00.0: reg 0x10: [mem 0xa0000000-0xafffffff 64bit pref]
[    0.822729] pci 0000:01:00.0: reg 0x18: [mem 0xb4000000-0xb401ffff 64bit]
[    0.822740] pci 0000:01:00.0: reg 0x20: [io  0x3000-0x30ff]
[    0.822760] pci 0000:01:00.0: reg 0x30: [mem 0xfffe0000-0xffffffff pref]
[    0.822805] pci 0000:01:00.0: supports D1 D2
[    0.822911] pci 0000:01:00.1: [1002:aa60] type 00 class 0x040300
[    0.822933] pci 0000:01:00.1: reg 0x10: [mem 0xb4020000-0xb4023fff 64bit]
[    0.823019] pci 0000:01:00.1: supports D1 D2
[    0.823100] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.823104] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    0.823107] pci 0000:00:01.0:   bridge window [mem 0xb4000000-0xb40fffff]
[    0.823111] pci 0000:00:01.0:   bridge window [mem 0xa0000000-0xafffffff 64bit pref]
[    0.823231] pci 0000:02:00.0: [14e4:1692] type 00 class 0x020000
[    0.823281] pci 0000:02:00.0: reg 0x10: [mem 0xb3000000-0xb300ffff 64bit]
[    0.823518] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.832453] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.832463] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.832471] pci 0000:00:1c.0:   bridge window [mem 0xb3000000-0xb3ffffff]
[    0.832484] pci 0000:00:1c.0:   bridge window [mem 0xb0000000-0xb0ffffff 64bit pref]
[    0.832615] pci 0000:03:00.0: [14e4:4357] type 00 class 0x028000
[    0.832668] pci 0000:03:00.0: reg 0x10: [mem 0xb2000000-0xb2003fff 64bit]
[    0.832927] pci 0000:03:00.0: supports D1 D2
[    0.832929] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.833046] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.833051] pci 0000:00:1c.1:   bridge window [io  0x1000-0x1fff]
[    0.833057] pci 0000:00:1c.1:   bridge window [mem 0xb2000000-0xb2ffffff]
[    0.833064] pci 0000:00:1c.1:   bridge window [mem 0xb1000000-0xb1ffffff 64bit pref]
[    0.833156] pci 0000:00:1e.0: PCI bridge to [bus 04] (subtractive decode)
[    0.833170] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7 window] (subtractive decode)
[    0.833172] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff window] (subtractive decode)
[    0.833175] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff window] (subtractive decode)
[    0.833177] pci 0000:00:1e.0:   bridge window [mem 0xa0000000-0xfebfffff window] (subtractive decode)
[    1.036435] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    1.036500] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    1.036562] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    1.036624] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    1.036686] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    1.036748] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    1.036810] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    1.036872] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    1.036898] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus ff])
[    1.036903] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    1.036909] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    1.036973] PCI host bridge to bus 0000:ff
[    1.036976] pci_bus 0000:ff: root bus resource [bus ff]
[    1.036983] pci 0000:ff:00.0: [8086:2c62] type 00 class 0x060000
[    1.037046] pci 0000:ff:00.1: [8086:2d01] type 00 class 0x060000
[    1.037116] pci 0000:ff:02.0: [8086:2d10] type 00 class 0x060000
[    1.037175] pci 0000:ff:02.1: [8086:2d11] type 00 class 0x060000
[    1.037233] pci 0000:ff:02.2: [8086:2d12] type 00 class 0x060000
[    1.037290] pci 0000:ff:02.3: [8086:2d13] type 00 class 0x060000
[    1.037418] ACPI: Enabled 5 GPEs in block 00 to 3F
[    1.037477] ACPI : EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    1.037625] vgaarb: setting as boot device: PCI:0000:01:00.0
[    1.037628] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    1.037631] vgaarb: loaded
[    1.037632] vgaarb: bridge control possible 0000:01:00.0
[    1.037945] SCSI subsystem initialized
[    1.038013] libata version 3.00 loaded.
[    1.038044] ACPI: bus type USB registered
[    1.038066] usbcore: registered new interface driver usbfs
[    1.038078] usbcore: registered new interface driver hub
[    1.038095] usbcore: registered new device driver usb
[    1.038277] PCI: Using ACPI for IRQ routing
[    1.048323] PCI: pci_cache_line_size set to 64 bytes
[    1.048475] e820: reserve RAM buffer [mem 0x0009d000-0x0009ffff]
[    1.048477] e820: reserve RAM buffer [mem 0x9f682000-0x9fffffff]
[    1.048479] e820: reserve RAM buffer [mem 0x9f736000-0x9fffffff]
[    1.048481] e820: reserve RAM buffer [mem 0x9f7df000-0x9fffffff]
[    1.048482] e820: reserve RAM buffer [mem 0x9f800000-0x9fffffff]
[    1.048634] NetLabel: Initializing
[    1.048636] NetLabel:  domain hash size = 128
[    1.048637] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.048655] NetLabel:  unlabeled traffic allowed by default
[    1.048762] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    1.048768] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    1.050802] clocksource: Switched to clocksource hpet
[    1.058861] AppArmor: AppArmor Filesystem Enabled
[    1.058967] pnp: PnP ACPI init
[    1.263010] pnp 00:00: disabling [io  0x164e-0x164f] because it overlaps 0000:00:1c.1 BAR 13 [io  0x1000-0x1fff]
[    1.263077] system 00:00: [io  0x0680-0x069f] has been reserved
[    1.263080] system 00:00: [io  0xff2c-0xff2f] has been reserved
[    1.263083] system 00:00: [io  0x0800-0x080f] has been reserved
[    1.263085] system 00:00: [io  0xffff] has been reserved
[    1.263089] system 00:00: [io  0xffff] has been reserved
[    1.263093] system 00:00: [io  0x0400-0x047f] could not be reserved
[    1.263095] system 00:00: [io  0x0500-0x057f] has been reserved
[    1.263101] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.263140] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.263189] pnp 00:02: Plug and Play ACPI device, IDs PNP0303 (active)
[    1.263265] pnp 00:03: Plug and Play ACPI device, IDs SYN1b16 SYN1b00 SYN0002 PNP0f13 (active)
[    1.263599] pnp 00:04: disabling [mem 0xfffff000-0xffffffff] because it overlaps 0000:01:00.0 BAR 6 [mem 0xfffe0000-0xffffffff pref]
[    1.263634] system 00:04: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    1.263637] system 00:04: [mem 0xfed10000-0xfed13fff] has been reserved
[    1.263639] system 00:04: [mem 0xfed18000-0xfed18fff] has been reserved
[    1.263642] system 00:04: [mem 0xfed19000-0xfed19fff] has been reserved
[    1.263645] system 00:04: [mem 0xe0000000-0xefffffff] has been reserved
[    1.263647] system 00:04: [mem 0xfed20000-0xfed3ffff] has been reserved
[    1.263650] system 00:04: [mem 0xfed45000-0xfed8ffff] has been reserved
[    1.263653] system 00:04: [mem 0xff000000-0xffffffff] could not be reserved
[    1.263656] system 00:04: [mem 0xfee00000-0xfeefffff] could not be reserved
[    1.263659] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.263791] pnp: PnP ACPI: found 5 devices
[    1.270976] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    1.270986] pci 0000:01:00.0: can't claim BAR 6 [mem 0xfffe0000-0xffffffff pref]: no compatible bridge window
[    1.271031] pci 0000:01:00.0: BAR 6: assigned [mem 0xb4040000-0xb405ffff pref]
[    1.271034] pci 0000:00:01.0: PCI bridge to [bus 01]
[    1.271037] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    1.271042] pci 0000:00:01.0:   bridge window [mem 0xb4000000-0xb40fffff]
[    1.271045] pci 0000:00:01.0:   bridge window [mem 0xa0000000-0xafffffff 64bit pref]
[    1.271050] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    1.271054] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    1.271059] pci 0000:00:1c.0:   bridge window [mem 0xb3000000-0xb3ffffff]
[    1.271065] pci 0000:00:1c.0:   bridge window [mem 0xb0000000-0xb0ffffff 64bit pref]
[    1.271073] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    1.271077] pci 0000:00:1c.1:   bridge window [io  0x1000-0x1fff]
[    1.271084] pci 0000:00:1c.1:   bridge window [mem 0xb2000000-0xb2ffffff]
[    1.271089] pci 0000:00:1c.1:   bridge window [mem 0xb1000000-0xb1ffffff 64bit pref]
[    1.271098] pci 0000:00:1e.0: PCI bridge to [bus 04]
[    1.271115] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    1.271117] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    1.271120] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    1.271122] pci_bus 0000:00: resource 7 [mem 0xa0000000-0xfebfffff window]
[    1.271125] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
[    1.271127] pci_bus 0000:01: resource 1 [mem 0xb4000000-0xb40fffff]
[    1.271129] pci_bus 0000:01: resource 2 [mem 0xa0000000-0xafffffff 64bit pref]
[    1.271132] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    1.271134] pci_bus 0000:02: resource 1 [mem 0xb3000000-0xb3ffffff]
[    1.271136] pci_bus 0000:02: resource 2 [mem 0xb0000000-0xb0ffffff 64bit pref]
[    1.271139] pci_bus 0000:03: resource 0 [io  0x1000-0x1fff]
[    1.271141] pci_bus 0000:03: resource 1 [mem 0xb2000000-0xb2ffffff]
[    1.271143] pci_bus 0000:03: resource 2 [mem 0xb1000000-0xb1ffffff 64bit pref]
[    1.271146] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7 window]
[    1.271148] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff window]
[    1.271151] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff window]
[    1.271153] pci_bus 0000:04: resource 7 [mem 0xa0000000-0xfebfffff window]
[    1.271196] NET: Registered protocol family 2
[    1.271411] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[    1.271558] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    1.271760] TCP: Hash tables configured (established 32768 bind 32768)
[    1.271800] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    1.271844] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    1.271938] NET: Registered protocol family 1
[    1.303047] pci 0000:01:00.0: Video device with shadowed ROM
[    1.303130] PCI: CLS 64 bytes, default 64
[    1.303211] Trying to unpack rootfs image as initramfs...
[    2.054027] Freeing initrd memory: 32968K (ffff880033f8c000 - ffff880035fbe000)
[    2.054084] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    2.054087] software IO TLB [mem 0x9b682000-0x9f682000] (64MB) mapped at [ffff88009b682000-ffff88009f681fff]
[    2.054292] microcode: CPU0 sig=0x20652, pf=0x10, revision=0xe
[    2.054299] microcode: CPU1 sig=0x20652, pf=0x10, revision=0xe
[    2.054383] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    2.054492] Scanning for low memory corruption every 60 seconds
[    2.054956] futex hash table entries: 2048 (order: 5, 131072 bytes)
[    2.054995] Initialise system trusted keyring
[    2.055026] audit: initializing netlink subsys (disabled)
[    2.055050] audit: type=2000 audit(1456572832.780:1): initialized
[    2.055551] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    2.057612] zpool: loaded
[    2.057615] zbud: loaded
[    2.057861] VFS: Disk quotas dquot_6.6.0
[    2.057911] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    2.058552] fuse init (API version 7.23)
[    2.058745] Key type big_key registered
[    2.059244] Key type asymmetric registered
[    2.059248] Asymmetric key parser 'x509' registered
[    2.059268] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    2.059308] io scheduler noop registered
[    2.059312] io scheduler deadline registered (default)
[    2.059355] io scheduler cfq registered
[    2.060005] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.060015] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.060057] vesafb: mode is 1366x768x32, linelength=5504, pages=0
[    2.060059] vesafb: scrolling: redraw
[    2.060062] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    2.060080] vesafb: framebuffer at 0xa0000000, mapped to 0xffffc90000800000, using 4160k, total 4160k
[    2.060210] Console: switching to colour frame buffer device 170x48
[    2.060250] fb0: VESA VGA frame buffer device
[    2.060272] intel_idle: MWAIT substates: 0x120
[    2.060274] intel_idle: v0.4 model 0x25
[    2.060276] intel_idle: lapic_timer_reliable_states 0xffffffff
[    2.563380] ACPI: AC Adapter [AC] (on-line)
[    2.563473] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:10/PNP0C0C:00/input/input0
[    2.563477] ACPI: Power Button [PWRB]
[    2.563527] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:10/PNP0C0D:00/input/input1
[    2.563557] ACPI: Lid Switch [LID0]
[    2.563607] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:10/PNP0C0E:00/input/input2
[    2.563610] ACPI: Sleep Button [SLPB]
[    2.563664] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    2.563667] ACPI: Power Button [PWRF]
[    2.565350] GHES: HEST is not enabled!
[    2.565590] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    3.051539] tsc: Refined TSC clocksource calibration: 1862.322 MHz
[    3.051546] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x35b0465207b, max_idle_ns: 881590764823 ns
[    4.051811] clocksource: Switched to clocksource tsc
[    4.119762] ACPI: Battery Slot [BAT0] (battery present)
[    4.120012] Linux agpgart interface v0.103
[    4.123765] brd: module loaded
[    4.125205] loop: module loaded
[    4.125464] libphy: Fixed MDIO Bus: probed
[    4.125468] tun: Universal TUN/TAP device driver, 1.6
[    4.125469] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    4.125551] PPP generic driver version 2.4.2
[    4.125668] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.125675] ehci-pci: EHCI PCI platform driver
[    4.125847] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    4.125856] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    4.125872] ehci-pci 0000:00:1a.0: debug port 2
[    4.129798] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    4.129824] ehci-pci 0000:00:1a.0: irq 16, io mem 0xb4105c00
[    4.139658] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    4.139742] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    4.139748] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.139752] usb usb1: Product: EHCI Host Controller
[    4.139757] usb usb1: Manufacturer: Linux 4.2.0-30-generic ehci_hcd
[    4.139761] usb usb1: SerialNumber: 0000:00:1a.0
[    4.139957] hub 1-0:1.0: USB hub found
[    4.139966] hub 1-0:1.0: 2 ports detected
[    4.140212] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    4.140222] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    4.140236] ehci-pci 0000:00:1d.0: debug port 2
[    4.144164] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    4.144176] ehci-pci 0000:00:1d.0: irq 23, io mem 0xb4105800
[    4.155698] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    4.155832] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    4.155840] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.155842] usb usb2: Product: EHCI Host Controller
[    4.155844] usb usb2: Manufacturer: Linux 4.2.0-30-generic ehci_hcd
[    4.155846] usb usb2: SerialNumber: 0000:00:1d.0
[    4.156097] hub 2-0:1.0: USB hub found
[    4.156119] hub 2-0:1.0: 2 ports detected
[    4.156238] ehci-platform: EHCI generic platform driver
[    4.156251] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.156257] ohci-pci: OHCI PCI platform driver
[    4.156270] ohci-platform: OHCI generic platform driver
[    4.156281] uhci_hcd: USB Universal Host Controller Interface driver
[    4.156352] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSS0] at 0x60,0x64 irq 1,12
[    4.174384] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.174390] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.174666] mousedev: PS/2 mouse device common for all mice
[    4.175607] rtc_cmos 00:01: RTC can wake from S4
[    4.175849] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    4.175891] rtc_cmos 00:01: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    4.175914] i2c /dev entries driver
[    4.176056] device-mapper: uevent: version 1.0.3
[    4.176246] device-mapper: ioctl: 4.33.0-ioctl (2015-8-18) initialised: dm-devel@redhat.com
[    4.176301] ledtrig-cpu: registered to indicate activity on CPUs
[    4.176626] PCCT header not found.
[    4.176924] NET: Registered protocol family 10
[    4.177174] NET: Registered protocol family 17
[    4.177189] Key type dns_resolver registered
[    4.177666] Loading compiled-in X.509 certificates
[    4.179030] Loaded X.509 cert 'Build time autogenerated kernel key: aa46912a20e4e17b1e4a6ccc08bd3c70d4d8f464'
[    4.179049] registered taskstats version 1
[    4.179075] zswap: loading zswap
[    4.179078] zswap: using zbud pool
[    4.179083] zswap: using lzo compressor
[    4.181922] Key type trusted registered
[    4.186611] Key type encrypted registered
[    4.186620] AppArmor: AppArmor sha1 policy hashing enabled
[    4.186625] ima: No TPM chip found, activating TPM-bypass!
[    4.186656] evm: HMAC attrs: 0x1
[    4.187195]   Magic number: 4:200:581
[    4.187252] pci_bus 0000:02: hash matches
[    4.187359] rtc_cmos 00:01: setting system clock to 2016-02-27 11:33:55 UTC (1456572835)
[    4.187801] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.187803] EDD information not available.
[    4.187936] PM: Hibernation image not present or could not be loaded.
[    4.188446] Freeing unused kernel memory: 1464K (ffffffff81d37000 - ffffffff81ea5000)
[    4.188449] Write protecting the kernel read-only data: 12288k
[    4.188673] Freeing unused kernel memory: 20K (ffff8800017fb000 - ffff880001800000)
[    4.188775] Freeing unused kernel memory: 292K (ffff880001bb7000 - ffff880001c00000)
[    4.194103] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    4.208188] random: systemd-udevd urandom read with 8 bits of entropy available
[    4.451778] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    4.467777] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    4.584168] usb 1-1: New USB device found, idVendor=8087, idProduct=0020
[    4.584174] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    4.584592] hub 1-1:1.0: USB hub found
[    4.584767] hub 1-1:1.0: 6 ports detected
[    4.600172] usb 2-1: New USB device found, idVendor=8087, idProduct=0020
[    4.600180] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    4.600620] hub 2-1:1.0: USB hub found
[    4.600747] hub 2-1:1.0: 8 ports detected
[    4.751544] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
[    4.751973] wmi: Mapper loaded
[    5.064020] acpi device:0d: registered as cooling_device2
[    5.064155] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:09/LNXVIDEO:01/input/input6
[    5.888086] pps_core: LinuxPPS API ver. 1 registered
[    5.888090] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    5.889928] PTP clock support registered
[    5.892805] [drm] Initialized drm 1.1.0 20060810
[    5.904872] ahci 0000:00:1f.2: version 3.0
[    5.905124] ahci 0000:00:1f.2: SSS flag set, parallel bus scan disabled
[    5.905163] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0x3 impl SATA mode
[    5.905167] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems apst 
[    5.917453] tg3.c:v3.137 (May 11, 2014)
[    5.931849] scsi host0: ahci
[    5.933613] [drm] radeon kernel modesetting enabled.
[    5.933698] scsi host1: ahci
[    5.933798] scsi host2: ahci
[    5.933887] scsi host3: ahci
[    5.933952] ata1: SATA max UDMA/133 abar m2048@0xb4105000 port 0xb4105100 irq 25
[    5.933956] ata2: SATA max UDMA/133 abar m2048@0xb4105000 port 0xb4105180 irq 25
[    5.933958] ata3: DUMMY
[    5.933959] ata4: DUMMY
[    5.938808] AMD IOMMUv2 driver by Joerg Roedel <jroedel@suse.de>
[    5.938812] AMD IOMMUv2 functionality not available on this system
[    5.943807] CRAT table not found
[    5.943811] Finished initializing topology ret=0
[    5.943861] kfd kfd: Initialized module
[    5.944115] checking generic (a0000000 410000) vs hw (a0000000 10000000)
[    5.944118] fb: switching to radeondrmfb from VESA VGA
[    5.944165] Console: switching to colour dummy device 80x25
[    5.944540] [drm] initializing kernel modesetting (REDWOOD 0x1002:0x68C1 0x1025:0x036D).
[    5.944556] [drm] register mmio base: 0xB4000000
[    5.944557] [drm] register mmio size: 131072
[    5.944671] ATOM BIOS: Acer
[    5.944757] radeon 0000:01:00.0: VRAM: 1024M 0x0000000000000000 - 0x000000003FFFFFFF (1024M used)
[    5.944760] radeon 0000:01:00.0: GTT: 1024M 0x0000000040000000 - 0x000000007FFFFFFF
[    5.944762] [drm] Detected VRAM RAM=1024M, BAR=256M
[    5.944764] [drm] RAM width 128bits DDR
[    5.948503] [TTM] Zone  kernel: Available graphics memory: 1954106 kiB
[    5.948506] [TTM] Initializing pool allocator
[    5.948516] [TTM] Initializing DMA pool allocator
[    5.948542] [drm] radeon: 1024M of VRAM memory ready
[    5.948543] [drm] radeon: 1024M of GTT memory ready.
[    5.948557] [drm] Loading REDWOOD Microcode
[    5.948634] [drm] Internal thermal controller with fan control
[    5.962970] libphy: tg3 mdio bus: probed
[    5.984310] [drm] radeon: dpm initialized
[    5.984433] [drm] GART: num cpu pages 262144, num gpu pages 262144
[    5.999100] [drm] PCIE GART of 1024M enabled (table at 0x000000000025E000).
[    5.999262] radeon 0000:01:00.0: WB enabled
[    5.999267] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000040000c00 and cpu addr 0xffff880035b4ec00
[    5.999270] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000040000c0c and cpu addr 0xffff880035b4ec0c
[    6.000016] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x000000000005c418 and cpu addr 0xffffc9000081c418
[    6.000019] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    6.000021] [drm] Driver supports precise vblank timestamp query.
[    6.000023] radeon 0000:01:00.0: radeon: MSI limited to 32-bit
[    6.000065] radeon 0000:01:00.0: radeon: using MSI.
[    6.000104] [drm] radeon: irq initialized.
[    6.017073] [drm] ring test on 0 succeeded in 1 usecs
[    6.017084] [drm] ring test on 3 succeeded in 3 usecs
[    6.039035] tg3 0000:02:00.0 eth0: Tigon3 [partno(BCM57780) rev 57780001] (PCI Express) MAC address xx:xx:xx:xx:xx:xx
[    6.039040] tg3 0000:02:00.0 eth0: attached PHY driver [Broadcom BCM57780] (mii_bus:phy_addr=200:01)
[    6.039043] tg3 0000:02:00.0 eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    6.039046] tg3 0000:02:00.0 eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    6.040440] tg3 0000:02:00.0 enp2s0: renamed from eth0
[    6.193404] [drm] ring test on 5 succeeded in 1 usecs
[    6.193412] [drm] UVD initialized successfully.
[    6.193812] [drm] ib test on ring 0 succeeded in 0 usecs
[    6.193853] [drm] ib test on ring 3 succeeded in 0 usecs
[    6.252268] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    6.253333] ata1.00: ATA-8: Hitachi HTS545050B9A300, PB4OC60F, max UDMA/133
[    6.253337] ata1.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    6.254568] ata1.00: configured for UDMA/133
[    6.254706] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54505 C60F PQ: 0 ANSI: 5
[    6.254978] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    6.255024] sd 0:0:0:0: [sda] Write Protect is off
[    6.255027] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.255047] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.255624] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    6.303840]  sda: sda1 sda2 < sda5 >
[    6.304178] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.572355] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.574174] ata2.00: ATAPI: MATSHITADVD-RAM UJ890AS, 1.00, max UDMA/100
[    6.577024] ata2.00: configured for UDMA/100
[    6.581119] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ890AS  1.00 PQ: 0 ANSI: 5
[    6.599793] sr 1:0:0:0: [sr0] scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.599799] cdrom: Uniform CD-ROM driver Revision: 3.20
[    6.599993] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    6.600069] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    6.840621] [drm] ib test on ring 5 succeeded
[    6.900514] [drm] radeon atom DIG backlight initialized
[    6.900524] [drm] Radeon Display Connectors
[    6.900527] [drm] Connector 0:
[    6.900530] [drm]   LVDS-1
[    6.900534] [drm]   DDC: 0x6560 0x6560 0x6564 0x6564 0x6568 0x6568 0x656c 0x656c
[    6.900537] [drm]   Encoders:
[    6.900539] [drm]     LCD1: INTERNAL_UNIPHY
[    6.900542] [drm] Connector 1:
[    6.900544] [drm]   HDMI-A-1
[    6.900546] [drm]   HPD1
[    6.900550] [drm]   DDC: 0x6430 0x6430 0x6434 0x6434 0x6438 0x6438 0x643c 0x643c
[    6.900552] [drm]   Encoders:
[    6.900555] [drm]     DFP1: INTERNAL_UNIPHY1
[    6.900557] [drm] Connector 2:
[    6.900559] [drm]   VGA-1
[    6.900563] [drm]   DDC: 0x6470 0x6470 0x6474 0x6474 0x6478 0x6478 0x647c 0x647c
[    6.900565] [drm]   Encoders:
[    6.900568] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    6.981810] psmouse serio1: synaptics: queried max coordinates: x [..5772], y [..5086]
[    7.097048] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000/0x0, board id: 0, fw id: 570026
[    7.169701] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   10.460564] [drm] fb mappable at 0xA045F000
[   10.460567] [drm] vram apper at 0xA0000000
[   10.460568] [drm] size 4325376
[   10.460569] [drm] fb depth is 24
[   10.460571] [drm]    pitch is 5632
[   10.460824] fbcon: radeondrmfb (fb0) is primary device
[   10.460971] Console: switching to colour frame buffer device 170x48
[   10.461014] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[   10.461016] radeon 0000:01:00.0: registered panic notifier
[   11.477847] [drm] Initialized radeon 2.43.0 20080528 for 0000:01:00.0 on minor 0
[   12.200876] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   12.486219] random: nonblocking pool is initialized
[   13.513047] systemd[1]: Failed to insert module 'kdbus': Function not implemented
[   13.725956] systemd[1]: systemd 225 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID -ELFUTILS +KMOD -IDN)
[   13.726123] systemd[1]: Detected architecture x86-64.
[   13.757209] systemd[1]: Set hostname to <heiko-TravelMate-5740ZG>.
[   14.650518] systemd[1]: rc-local.service: Cannot add dependency job, ignoring: Unit rc-local.service is masked.
[   14.651293] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[   14.651336] systemd[1]: Reached target Remote File Systems (Pre).
[   14.651349] systemd[1]: Reached target User and Group Name Lookups.
[   14.651386] systemd[1]: Created slice Root Slice.
[   14.651492] systemd[1]: Listening on Journal Audit Socket.
[   14.651609] systemd[1]: Created slice User and Session Slice.
[   14.651643] systemd[1]: Listening on udev Kernel Socket.
[   14.651688] systemd[1]: Listening on Journal Socket (/dev/log).
[   14.651724] systemd[1]: Listening on fsck to fsckd communication Socket.
[   14.651737] systemd[1]: Reached target Encrypted Volumes.
[   14.651784] systemd[1]: Listening on Journal Socket.
[   14.651842] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[   14.652010] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[   14.652119] systemd[1]: Created slice System Slice.
[   14.652245] systemd[1]: Created slice system-getty.slice.
[   14.652884] systemd[1]: Mounting POSIX Message Queue File System...
[   14.653617] systemd[1]: Started Braille Device Support.
[   14.654569] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[   14.655287] systemd[1]: Mounting Huge Pages File System...
[   14.655313] systemd[1]: Reached target Slices.
[   14.656036] systemd[1]: Started Read required files in advance.
[   14.656805] systemd[1]: Mounting Debug File System...
[   14.932928] systemd[1]: Starting Load Kernel Modules...
[   14.933621] systemd[1]: Starting Uncomplicated firewall...
[   14.934332] systemd[1]: Starting Setup Virtual Console...
[   14.934422] systemd[1]: Listening on udev Control Socket.
[   14.935193] systemd[1]: Starting udev Coldplug all Devices...
[   14.935966] systemd[1]: Starting Increase datagram queue length...
[   15.251010] systemd[1]: Started Create list of required static device nodes for the current kernel.
[   15.251305] systemd[1]: Started Uncomplicated firewall.
[   15.251559] systemd[1]: Started Setup Virtual Console.
[   15.257122] systemd[1]: Starting Create Static Device Nodes in /dev...
[   15.568612] systemd[1]: Mounted Huge Pages File System.
[   15.568656] systemd[1]: Mounted POSIX Message Queue File System.
[   15.568677] systemd[1]: Mounted Debug File System.
[   15.569240] systemd[1]: Started Increase datagram queue length.
[   15.575593] systemd[1]: Listening on Syslog Socket.
[   15.576345] systemd[1]: Starting Journal Service...
[   15.820133] lp: driver loaded but no devices found
[   15.890644] ppdev: user-space parallel port driver
[   16.038592] systemd[1]: Started Load Kernel Modules.
[   16.039610] systemd[1]: Mounting FUSE Control File System...
[   16.040325] systemd[1]: Starting Apply Kernel Variables...
[   16.042929] systemd[1]: Mounted FUSE Control File System.
[   16.531341] systemd[1]: Started Journal Service.
[   19.074287] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   19.488176] systemd-journald[253]: Received request to flush runtime journal from PID 1
[   20.220350] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   20.668519] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x0000000000000400-0x000000000000047F (\PMIO) (20150619/utaddress-254)
[   20.668529] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   20.668534] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20150619/utaddress-254)
[   20.668539] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   20.668540] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20150619/utaddress-254)
[   20.668545] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x000000000000053F (\_SB_.PCI0.GPIO) (20150619/utaddress-254)
[   20.668549] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   20.668550] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20150619/utaddress-254)
[   20.668554] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x000000000000053F (\_SB_.PCI0.GPIO) (20150619/utaddress-254)
[   20.668558] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   20.668560] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   21.106857] bcma: bus0: Found chip with id 43225, rev 0x01 and package 0x08
[   21.106905] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x22, class 0x0)
[   21.106949] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x17, class 0x0)
[   21.107030] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x0F, class 0x0)
[   21.121657] bcma: bus0: Bus registered
[   22.330583] snd_hda_intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   22.499734] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input8
[   22.540053] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC272X: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   22.540059] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   22.540062] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[   22.540065] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[   22.540067] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[   22.540070] snd_hda_codec_realtek hdaudioC0D0:      Internal Mic=0x19
[   22.540072] snd_hda_codec_realtek hdaudioC0D0:      Mic=0x18
[   22.547770] input: HDA Intel MID Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   22.547862] input: HDA Intel MID Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   22.567930] b43-phy0: Broadcom 43225 WLAN found (core revision 23)
[   22.568351] b43-phy0: Found PHY: Analog 8, Type 4 (N), Revision 6
[   22.568365] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2056, Revision 11, Version 0
[   22.568916] Broadcom 43xx driver loaded [ Features: PNL ]
[   23.973311] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   23.974935] b43 bcma0:1 wlp3s0b1: renamed from wlan0
[   24.861092] cfg80211: World regulatory domain updated:
[   24.861098] cfg80211:  DFS Master region: unset
[   24.861100] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   24.861103] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   24.861105] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   24.861108] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[   24.861110] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[   24.861113] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[   24.861115] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[   24.861117] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[   24.861120] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[   26.576966] Adding 4051964k swap on /dev/sda5.  Priority:-1 extents:1 across:4051964k FS
[   27.020326] audit: type=1400 audit(1456572858.323:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=482 comm="apparmor_parser"
[   27.020338] audit: type=1400 audit(1456572858.323:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=482 comm="apparmor_parser"
[   27.108312] audit: type=1400 audit(1456572858.411:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=482 comm="apparmor_parser"
[   27.108323] audit: type=1400 audit(1456572858.411:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=482 comm="apparmor_parser"
[   27.108330] audit: type=1400 audit(1456572858.411:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=482 comm="apparmor_parser"
[   27.108336] audit: type=1400 audit(1456572858.411:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=482 comm="apparmor_parser"
[   27.315603] audit: type=1400 audit(1456572858.619:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=482 comm="apparmor_parser"
[   27.315616] audit: type=1400 audit(1456572858.619:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=482 comm="apparmor_parser"
[   27.315624] audit: type=1400 audit(1456572858.619:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=482 comm="apparmor_parser"
[   27.315630] audit: type=1400 audit(1456572858.619:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=482 comm="apparmor_parser"
[   38.058360] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   38.079345] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   38.082942] IPv6: ADDRCONF(NETDEV_UP): wlp3s0b1: link is not ready
[   38.236967] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   38.377615] IPv6: ADDRCONF(NETDEV_UP): wlp3s0b1: link is not ready
[   38.439744] IPv6: ADDRCONF(NETDEV_UP): wlp3s0b1: link is not ready
[   39.042209] tg3 0000:02:00.0 enp2s0: Link is down
[   39.701935] wlp3s0b1: authenticate with xx:xx:xx:xx:xx:xx
[   39.713690] wlp3s0b1: send auth to xx:xx:xx:xx:xx:xx (try 1/3)
[   39.737383] wlp3s0b1: authenticated
[   39.741451] wlp3s0b1: associate with xx:xx:xx:xx:xx:xx (try 1/3)
[   39.744271] wlp3s0b1: RX AssocResp from xx:xx:xx:xx:xx:xx (capab=0x31 status=0 aid=4)
[   39.744817] wlp3s0b1: associated
[   39.744849] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0b1: link becomes ready

```
[HR][/HR]critical-chain:
[ATTACH]267556[/ATTACH]
```

The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.

graphical.target @40.252s
`-multi-user.target @40.252s
  `-getty.target @40.252s
    `-getty@tty1.service @40.252s
      `-systemd-user-sessions.service @17.094s +742ms
        `-basic.target @14.868s
          `-paths.target @14.868s
            `-cups.path @14.868s
              `-sysinit.target @14.866s
                `-networking.service @14.553s +312ms
                  `-apparmor.service @5.965s +8.586s
                    `-local-fs.target @5.965s
                      `-local-fs-pre.target @5.964s
                        `-systemd-remount-fs.service @5.888s +74ms
                          `-system.slice @1.541s
                            `--.slice @1.540s

```
[HR][/HR]systemd-analyze blame:
[ATTACH]267557[/ATTACH]
```

         22.402s plymouth-quit-wait.service
         10.555s dev-sda1.device
          8.586s apparmor.service
          8.544s gpu-manager.service
          7.479s accounts-daemon.service
          6.963s thermald.service
          6.715s ModemManager.service
          6.451s NetworkManager.service
          5.913s grub-common.service
          5.708s irqbalance.service
          3.607s rsyslog.service
          3.026s apport.service
          2.968s alsa-restore.service
          2.967s pppd-dns.service
          2.809s plymouth-start.service
          2.653s binfmt-support.service
          2.538s systemd-logind.service
          2.466s console-setup.service
          2.178s systemd-udevd.service
          2.138s systemd-udev-trigger.service
          1.860s proc-sys-fs-binfmt_misc.mount
          1.561s systemd-tmpfiles-setup-dev.service
          1.201s systemd-tmpfiles-setup.service
          1.178s ifup-wait-all-auto.service
          1.105s systemd-modules-load.service
           981ms dns-clean.service
           954ms systemd-journald.service
           941ms avahi-daemon.service
           915ms dev-mqueue.mount
           913ms dev-hugepages.mount
           911ms sys-kernel-debug.mount
           885ms systemd-update-utmp.service
           849ms upower.service
           742ms systemd-user-sessions.service
           741ms speech-dispatcher.service
           737ms ondemand.service
           707ms systemd-journal-flush.service
           637ms dev-disk-by\x2duuid-ef8cca3b\x2d26b8\x2d455e\x2d9ba9\x2d294395348c36.swap
           633ms systemd-setup-dgram-qlen.service
           616ms systemd-sysctl.service
           596ms kmod-static-nodes.service
           552ms systemd-timesyncd.service
           483ms lm-sensors.service
           476ms systemd-rfkill@rfkill0.service
           475ms systemd-random-seed.service
           463ms resolvconf.service
           322ms systemd-backlight@backlight:acpi_video0.service
           317ms ufw.service
           317ms systemd-vconsole-setup.service
           312ms networking.service
           311ms udisks2.service
           214ms systemd-backlight@backlight:radeon_bl0.service
           204ms plymouth-read-write.service
           193ms polkitd.service
           117ms systemd-tmpfiles-clean.service
            97ms lightdm.service
            92ms kerneloops.service
            74ms systemd-remount-fs.service
            35ms user@1000.service
            21ms wpa_supplicant.service
             8ms ureadahead-stop.service
             6ms systemd-update-utmp-runlevel.service
             6ms rtkit-daemon.service
             5ms hddtemp.service
             3ms sys-fs-fuse-connections.mount

```

[ATTACH]267558[/ATTACH]

---

### Post by no-spam-to-me on 2016-02-29
I have forgotten something:
I can see the plymouth splash screen only a few seconds (maybe three) in the entire 53s boot process.:-k

---

