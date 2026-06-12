---
title: "Ubuntu works without nvidia but stuck at login screen with nvidia"
date: 2019-02-22
forum: General Help
---

### Post by ravi_joshi on 2019-02-22
I have Nvidia GeForce GTX 1080 card installed and the Ubuntu  14.04 LTS used to work without any issue till yesterday. Unfortunately, after restarting from many days, it is now got stuck at the login screen. I switched to terminal mode (Ctrl+Alt+F1) and removed Nvidia drivers using the following command:


```
sudo apt-get purge nvidia-*

```

However, I want to use Nvidia drivers so this time after removing (purging) Nvidia, I logged in using Ubuntu's default graphics and I installed Nvidia drives from "additional drivers" under "software and updates". After rebooting, it again stuck at login screen.


Below is the permission info. for .Xauthority file:


```
ravi@lab:~$ ls -la .X*
-rw------- 1 ravi ravi 48 Feb 22 11:43 .Xauthority

```

I also tried upgrading Nvidia drivers to nvidia-410 using ppa:graphics-drivers/ppa -y but the problem persists. I am not able to figure out the cause of the problem. Below is the tail of dmesg:
```
[    1.180256] usb 1-10: New USB device found, idVendor=1a81, idProduct=2004
[    1.180258] usb 1-10: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.180260] usb 1-10: Product: USB KEYBOARD
[    1.180262] usb 1-10: Manufacturer: USB KEYBOARD
[    1.180438] usb 1-10: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    1.180447] usb 1-10: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
[    1.184841] input: USB KEYBOARD USB KEYBOARD as /devices/pci0000:00/0000:00:14.0/usb1/1-10/1-10:1.0/input/input7
[    1.185063] hid-generic 0003:1A81:2004.0002: input,hidraw1: USB HID v1.10 Keyboard [USB KEYBOARD USB KEYBOARD] on usb-0000:00:14.0-10/input0
[    1.193158] input: USB KEYBOARD USB KEYBOARD as /devices/pci0000:00/0000:00:14.0/usb1/1-10/1-10:1.1/input/input8
[    1.193545] hid-generic 0003:1A81:2004.0003: input,hiddev0,hidraw2: USB HID v1.10 Device [USB KEYBOARD USB KEYBOARD] on usb-0000:00:14.0-10/input1
[    1.225281] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[    1.307191] random: init urandom read with 29 bits of entropy available
[    1.339571] init: plymouth-upstart-bridge main process (229) terminated with status 1
[    1.339580] init: plymouth-upstart-bridge main process ended, respawning
[    1.341226] init: plymouth-upstart-bridge main process (239) terminated with status 1
[    1.341235] init: plymouth-upstart-bridge main process ended, respawning
[    1.342420] init: plymouth-upstart-bridge main process (241) terminated with status 1
[    1.342433] init: plymouth-upstart-bridge main process ended, respawning
[    1.344228] init: plymouth-upstart-bridge main process (243) terminated with status 1
[    1.344236] init: plymouth-upstart-bridge main process ended, respawning
[    1.345567] init: plymouth-upstart-bridge main process (245) terminated with status 1
[    1.345574] init: plymouth-upstart-bridge main process ended, respawning
[    1.347373] init: plymouth-upstart-bridge main process (246) terminated with status 1
[    1.347385] init: plymouth-upstart-bridge main process ended, respawning
[    1.349379] init: plymouth-upstart-bridge main process (248) terminated with status 1
[    1.349387] init: plymouth-upstart-bridge main process ended, respawning
[    1.350681] init: plymouth-upstart-bridge main process (250) terminated with status 1
[    1.350711] init: plymouth-upstart-bridge main process ended, respawning
[    1.469157] Adding 16734204k swap on /dev/sda3.  Priority:-1 extents:1 across:16734204k SSFS
[    1.542168] systemd-udevd[366]: starting version 204
[    1.555642] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[    1.595939] tsc: Refined TSC clocksource calibration: 3599.985 MHz
[    1.603335] lp: driver loaded but no devices found
[    1.611459] ppdev: user-space parallel port driver
[    1.690668] wmi: Mapper loaded
[    1.696308] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    1.729736] [drm] Initialized drm 1.1.0 20060810
[    1.801546] type=1400 audit(1550892856.530:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=563 comm="apparmor_parser"
[    1.801551] type=1400 audit(1550892856.530:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=563 comm="apparmor_parser"
[    1.801554] type=1400 audit(1550892856.530:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=563 comm="apparmor_parser"
[    1.801966] type=1400 audit(1550892856.530:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=559 comm="apparmor_parser"
[    1.801969] type=1400 audit(1550892856.530:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=559 comm="apparmor_parser"
[    1.801972] type=1400 audit(1550892856.530:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=559 comm="apparmor_parser"
[    1.814570] snd_hda_intel 0000:00:1f.3: irq 182 for MSI/MSI-X
[    1.833616] SKU: Nid=0x1d sku_cfg=0x4024c601
[    1.833628] SKU: port_connectivity=0x1
[    1.833628] SKU: enable_pcbeep=0x0
[    1.833629] SKU: check_sum=0x00000004
[    1.833630] SKU: customization=0x000000c6
[    1.833630] SKU: external_amp=0x0
[    1.833631] SKU: platform_type=0x0
[    1.833632] SKU: swap=0x0
[    1.833633] SKU: override=0x1
[    1.833991] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:line
[    1.833992]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    1.833993]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[    1.833994]    mono: mono_out=0x0
[    1.833999]    inputs:
[    1.834000]      Front Mic=0x19
[    1.834001]      Rear Mic=0x18
[    1.834002]      Line=0x1a
[    1.834003] realtek: No valid SSID, checking pincfg 0x4024c601 for NID 0x1d
[    1.834009] realtek: Enabling init ASM_ID=0xc601 CODEC_ID=10ec0892
[    1.889961] Bluetooth: Core ver 2.17
[    1.889977] NET: Registered protocol family 31
[    1.889978] Bluetooth: HCI device and connection manager initialized
[    1.889983] Bluetooth: HCI socket layer initialized
[    1.889991] Bluetooth: L2CAP socket layer initialized
[    1.889994] Bluetooth: SCO socket layer initialized
[    1.898882] type=1400 audit(1550892856.626:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=726 comm="apparmor_parser"
[    1.898887] type=1400 audit(1550892856.626:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=726 comm="apparmor_parser"
[    1.900182] Bluetooth: RFCOMM TTY layer initialized
[    1.900194] Bluetooth: RFCOMM socket layer initialized
[    1.900337] Bluetooth: RFCOMM ver 1.11
[    1.904964] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    1.904967] Bluetooth: BNEP filters: protocol multicast
[    1.904972] Bluetooth: BNEP socket layer initialized
[    1.951414] init: cups main process (764) killed by HUP signal
[    1.951428] init: cups main process ended, respawning
[    1.971310] init: failsafe main process (721) killed by TERM signal
[    2.069576] type=1400 audit(1550892856.798:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=912 comm="apparmor_parser"
[    2.220123] init: nvidia-prime main process (1028) terminated with status 127
[    2.234127] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    2.262080] init: alsa-restore main process (1082) terminated with status 19
[    2.314042] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[    2.360725] init: plymouth-upstart-bridge main process ended, respawning
[    2.530774] vboxdrv: module verification failed: signature and/or  required key missing - tainting kernel
[    2.534467] vboxdrv: Found 8 processor cores
[    2.558419] vboxdrv: TSC mode is Invariant, tentative frequency 3598561236 Hz
[    2.558421] vboxdrv: Successfully loaded version 6.0.4 (interface 0x00290008)
[    2.598214] Switched to clocksource tsc
[    2.762104] VBoxNetFlt: Successfully started.
[    2.763450] VBoxNetAdp: Successfully started.
[    2.764904] VBoxPciLinuxInit
[    2.766636] vboxpci: IOMMU not found (not registered)
[    2.805767] random: nonblocking pool is initialized
[    2.825697] init: plymouth-stop pre-start process (1365) terminated with status 1
[    2.848274] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1f.3/sound/card0/input13
[    2.848389] input: HDA Intel Line Out as /devices/pci0000:00/0000:00:1f.3/sound/card0/input12
[    2.848498] input: HDA Intel Line as /devices/pci0000:00/0000:00:1f.3/sound/card0/input11
[    2.848586] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1f.3/sound/card0/input10
[    2.848674] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1f.3/sound/card0/input9
[    2.849027] hda_intel: Disabling MSI
[    2.849031] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[    2.849059] hda-intel 0000:01:00.1: Disabling 64bit DMA
[    2.852436] hda-intel 0000:01:00.1: Enable delay in RIRB handling
[    3.162941] autoconfig: line_outs=0 (0x0/0x0/0x0/0x0/0x0) type:line
[    3.162944]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    3.162945]    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    3.162946]    mono: mono_out=0x0
[    3.162947]    dig-out=0x4/0x5
[    3.162948]    inputs:
[    3.251205] input: HDA NVidia HDMI as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input15
[    3.251307] input: HDA NVidia HDMI as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input14
[    3.274485] ahci 0000:00:17.0: port does not support device sleep
[    3.297415] init: plymouth-splash main process (1668) terminated with status 1
[    5.059584] e1000e: eth1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[    5.059882] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[    5.083734] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[    5.084032] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   32.013438] audit_printk_skb: 60 callbacks suppressed
[   32.013440] type=1400 audit(1550892886.682:31): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=3031 comm="apparmor_parser"
[   32.013444] type=1400 audit(1550892886.682:32): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=3031 comm="apparmor_parser"

```

The complete [dmesg]("https://pastebin.com/A7qCJ2d5") is uploaded to PasteBin to keep this post shorter and cleaner.

PS: I know the similar type of questions is asked many times but I am not able to figure out the cause of this problem.

---

### Post by ravi_joshi on 2019-02-23
Any workaround, please?

---

### Post by CatKiller on 2019-02-24
The place to look for error messages when you're getting an X crash at login is (probably) /var/log/Xorg.0.log rather than dmesg.

We've had a few reports here now of people having an issue with new nvidia drivers on 14.04. 

Support for 14.04 ends in April.

My advice would be to stick with an older driver for now and upgrade to 16.04 or 18.04 ASAP.

---

### Post by Bashing-om on 2019-02-24
ravi_joshi; Hello

I too had issues with a new(er) Nvidia card on 14.04. Booting in text mode showed that the card had no support. However, booting with the 'nomodeset' kernel boot parameter gives a usable system.

The card is supported on 16.04 and up releases.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by ravi_joshi on 2019-02-26
Hello CatKiller and Bashing-om,

Thank you very much for your help. I am following your advice and I tried once again installing NVIDIA driver version 384.130 (proprietary) from "additional drivers" under "software and updates". Although, I have added "ppa:graphics-drivers/ppa -y" and I can see recent new versions of NVIDIA driver under the same window but I chose version 384.130 (proprietary) since Ubuntu 14.04 is too old to support new versions (maybe!).

After installing NVIDIA driver version 384.130 (proprietary), I restarted the PC and I wasn't able to log in using GUI mode hence switched to the terminal mode using CTRL+ALT+F1 and copied the logs such as Xorg.0.log and kern.log. Each of these files is too long to completely copy and paste here since It will make this thread too long to read. Hence I am pasting initial 100 lines of each file and I am uploading the complete files into PasteBin. (Do let me know if this is not a best practice. I am sorry if I made a mistake here)

Below are the first 100 lines of Xorg.0.log
```

[    22.707] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    22.707] X Protocol Version 11, Revision 0
[    22.707] Build Operating System: Linux 4.4.0-97-generic x86_64 Ubuntu
[    22.707] Current Operating System: Linux lab 3.13.0-165-generic #215-Ubuntu SMP Wed Jan 16 11:46:47 UTC 2019 x86_64
[    22.707] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-165-generic.efi.signed root=UUID=c0eee90f-7184-4ed5-a6a8-8c87a33425e0 ro quiet splash usbcore.usbfs_memory_mb=256 vt.handoff=7
[    22.707] Build Date: 13 October 2017  01:59:06PM
[    22.707] xorg-server 2:1.15.1-0ubuntu2.11 (For technical support please see http://www.ubuntu.com/support) 
[    22.707] Current version of pixman: 0.30.2
[    22.707] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    22.707] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    22.707] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Feb 26 14:29:44 2019
[    22.707] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    22.707] (==) No Layout section.  Using the first Screen section.
[    22.707] (==) No screen section available. Using defaults.
[    22.707] (**) |-->Screen "Default Screen Section" (0)
[    22.707] (**) |   |-->Monitor "<default monitor>"
[    22.707] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    22.707] (==) Automatically adding devices
[    22.707] (==) Automatically enabling devices
[    22.707] (==) Automatically adding GPU devices
[    22.707] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    22.707] 	Entry deleted from font path.
[    22.707] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    22.707] 	Entry deleted from font path.
[    22.707] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    22.707] 	Entry deleted from font path.
[    22.707] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    22.707] 	Entry deleted from font path.
[    22.707] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    22.707] 	Entry deleted from font path.
[    22.707] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    22.707] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    22.707] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    22.707] (II) Loader magic: 0x7f88f5e54d40
[    22.707] (II) Module ABI versions:
[    22.707] 	X.Org ANSI C Emulation: 0.4
[    22.707] 	X.Org Video Driver: 15.0
[    22.707] 	X.Org XInput driver : 20.0
[    22.707] 	X.Org Server Extension : 8.0
[    22.709] (--) PCI:*(0:1:0:0) 10de:1b80:1458:3774 rev 161, Mem @ 0xde000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[    22.709] Initializing built-in extension Generic Event Extension
[    22.709] Initializing built-in extension SHAPE
[    22.709] Initializing built-in extension MIT-SHM
[    22.709] Initializing built-in extension XInputExtension
[    22.709] Initializing built-in extension XTEST
[    22.709] Initializing built-in extension BIG-REQUESTS
[    22.709] Initializing built-in extension SYNC
[    22.709] Initializing built-in extension XKEYBOARD
[    22.709] Initializing built-in extension XC-MISC
[    22.709] Initializing built-in extension SECURITY
[    22.709] Initializing built-in extension XINERAMA
[    22.709] Initializing built-in extension XFIXES
[    22.709] Initializing built-in extension RENDER
[    22.709] Initializing built-in extension RANDR
[    22.709] Initializing built-in extension COMPOSITE
[    22.709] Initializing built-in extension DAMAGE
[    22.709] Initializing built-in extension MIT-SCREEN-SAVER
[    22.709] Initializing built-in extension DOUBLE-BUFFER
[    22.709] Initializing built-in extension RECORD
[    22.709] Initializing built-in extension DPMS
[    22.709] Initializing built-in extension Present
[    22.709] Initializing built-in extension DRI3
[    22.709] Initializing built-in extension X-Resource
[    22.709] Initializing built-in extension XVideo
[    22.709] Initializing built-in extension XVideo-MotionCompensation
[    22.709] Initializing built-in extension SELinux
[    22.709] Initializing built-in extension XFree86-VidModeExtension
[    22.709] Initializing built-in extension XFree86-DGA
[    22.709] Initializing built-in extension XFree86-DRI
[    22.709] Initializing built-in extension DRI2
[    22.709] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    22.709] (II) "glx" will be loaded by default.
[    22.709] (WW) "xmir" is not to be loaded by default. Skipping.
[    22.709] (II) LoadModule: "glx"
[    22.709] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    22.712] (II) Module glx: vendor="NVIDIA Corporation"
[    22.712] 	compiled for 4.0.2, module version = 1.0.0
[    22.712] 	Module class: X.Org Server Extension
[    22.712] (II) NVIDIA GLX Module  384.130  Wed Mar 21 02:54:48 PDT 2018
[    22.712] Loading extension GLX
[    22.712] (==) Matched nvidia as autoconfigured driver 0
[    22.712] (==) Matched nouveau as autoconfigured driver 1
[    22.712] (==) Matched modesetting as autoconfigured driver 2
[    22.712] (==) Matched fbdev as autoconfigured driver 3
[    22.712] (==) Matched vesa as autoconfigured driver 4
[    22.712] (==) Assigned the driver to the xf86ConfigLayout
[    22.712] (II) LoadModule: "nvidia"
[    22.712] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    22.712] (II) Module nvidia: vendor="NVIDIA Corporation"
[    22.712] 	compiled for 4.0.2, module version = 1.0.0

```

Below are the first 100 lines of kern.log
```

Feb 25 07:35:02 lab kernel: [154928.766983] type=1400 audit(1551047702.637:38): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=30997 comm="apparmor_parser"
Feb 25 07:35:02 lab kernel: [154928.766987] type=1400 audit(1551047702.637:39): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=30997 comm="apparmor_parser"
Feb 25 19:13:36 lab kernel: [196925.062508] e1000e: eth1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
Feb 25 19:13:39 lab kernel: [196927.638697] e1000e: eth1 NIC Link is Down
Feb 25 19:13:42 lab kernel: [196930.725586] e1000e: eth1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
Feb 25 19:15:02 lab kernel: [197011.306150] usb 1-4: new high-speed USB device number 9 using xhci_hcd
Feb 25 19:15:02 lab kernel: [197011.322856] usb 1-4: New USB device found, idVendor=0781, idProduct=5567
Feb 25 19:15:02 lab kernel: [197011.322859] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Feb 25 19:15:02 lab kernel: [197011.322862] usb 1-4: Product: Cruzer Blade
Feb 25 19:15:02 lab kernel: [197011.322864] usb 1-4: Manufacturer: SanDisk
Feb 25 19:15:02 lab kernel: [197011.322866] usb 1-4: SerialNumber: 200535503313DA03627C
Feb 25 19:15:02 lab kernel: [197011.323190] usb-storage 1-4:1.0: USB Mass Storage device detected
Feb 25 19:15:02 lab kernel: [197011.323559] scsi11 : usb-storage 1-4:1.0
Feb 25 19:15:03 lab kernel: [197012.324930] scsi 11:0:0:0: Direct-Access     SanDisk  Cruzer Blade     1.26 PQ: 0 ANSI: 5
Feb 25 19:15:03 lab kernel: [197012.325085] sd 11:0:0:0: Attached scsi generic sg1 type 0
Feb 25 19:15:03 lab kernel: [197012.327017] sd 11:0:0:0: [sdb] 15633408 512-byte logical blocks: (8.00 GB/7.45 GiB)
Feb 25 19:15:03 lab kernel: [197012.328141] sd 11:0:0:0: [sdb] Write Protect is off
Feb 25 19:15:03 lab kernel: [197012.328145] sd 11:0:0:0: [sdb] Mode Sense: 43 00 00 00
Feb 25 19:15:03 lab kernel: [197012.328510] sd 11:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Feb 25 19:15:03 lab kernel: [197012.346677]  sdb: sdb1
Feb 25 19:15:03 lab kernel: [197012.348011] sd 11:0:0:0: [sdb] Attached SCSI removable disk
Feb 25 19:15:04 lab kernel: [197012.530118] FAT-fs (sdb1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
Feb 25 19:15:08 lab kernel: [197016.849293] usb 1-4: USB disconnect, device number 9
Feb 25 19:18:57 lab kernel: [197246.213417] usb 1-4: new high-speed USB device number 10 using xhci_hcd
Feb 25 19:18:57 lab kernel: [197246.230162] usb 1-4: New USB device found, idVendor=0781, idProduct=5567
Feb 25 19:18:57 lab kernel: [197246.230165] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Feb 25 19:18:57 lab kernel: [197246.230167] usb 1-4: Product: Cruzer Blade
Feb 25 19:18:57 lab kernel: [197246.230168] usb 1-4: Manufacturer: SanDisk
Feb 25 19:18:57 lab kernel: [197246.230170] usb 1-4: SerialNumber: 200535503313DA03627C
Feb 25 19:18:57 lab kernel: [197246.230458] usb-storage 1-4:1.0: USB Mass Storage device detected
Feb 25 19:18:57 lab kernel: [197246.230672] scsi12 : usb-storage 1-4:1.0
Feb 25 19:18:58 lab kernel: [197247.232306] scsi 12:0:0:0: Direct-Access     SanDisk  Cruzer Blade     1.26 PQ: 0 ANSI: 5
Feb 25 19:18:58 lab kernel: [197247.232798] sd 12:0:0:0: Attached scsi generic sg1 type 0
Feb 25 19:18:58 lab kernel: [197247.233729] sd 12:0:0:0: [sdb] 15633408 512-byte logical blocks: (8.00 GB/7.45 GiB)
Feb 25 19:18:58 lab kernel: [197247.234708] sd 12:0:0:0: [sdb] Write Protect is off
Feb 25 19:18:58 lab kernel: [197247.234715] sd 12:0:0:0: [sdb] Mode Sense: 43 00 00 00
Feb 25 19:18:58 lab kernel: [197247.234949] sd 12:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Feb 25 19:18:58 lab kernel: [197247.251650]  sdb: sdb1
Feb 25 19:18:58 lab kernel: [197247.252507] sd 12:0:0:0: [sdb] Attached SCSI removable disk
Feb 25 19:18:58 lab kernel: [197247.435305] FAT-fs (sdb1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
Feb 25 19:56:33 lab kernel: [199507.000010] usb 1-4: USB disconnect, device number 10
Feb 25 19:57:54 lab kernel: [199588.280418] usb 1-4: new high-speed USB device number 11 using xhci_hcd
Feb 25 19:57:54 lab kernel: [199588.296368] usb 1-4: New USB device found, idVendor=0781, idProduct=5567
Feb 25 19:57:54 lab kernel: [199588.296371] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Feb 25 19:57:54 lab kernel: [199588.296373] usb 1-4: Product: Cruzer Blade
Feb 25 19:57:54 lab kernel: [199588.296375] usb 1-4: Manufacturer: SanDisk
Feb 25 19:57:54 lab kernel: [199588.296376] usb 1-4: SerialNumber: 200535503313DA03627C
Feb 25 19:57:54 lab kernel: [199588.296757] usb-storage 1-4:1.0: USB Mass Storage device detected
Feb 25 19:57:54 lab kernel: [199588.296850] scsi13 : usb-storage 1-4:1.0
Feb 25 19:57:55 lab kernel: [199589.298514] scsi 13:0:0:0: Direct-Access     SanDisk  Cruzer Blade     1.26 PQ: 0 ANSI: 5
Feb 25 19:57:55 lab kernel: [199589.298687] sd 13:0:0:0: Attached scsi generic sg1 type 0
Feb 25 19:57:55 lab kernel: [199589.300991] sd 13:0:0:0: [sdb] 15633408 512-byte logical blocks: (8.00 GB/7.45 GiB)
Feb 25 19:57:55 lab kernel: [199589.302573] sd 13:0:0:0: [sdb] Write Protect is off
Feb 25 19:57:55 lab kernel: [199589.302576] sd 13:0:0:0: [sdb] Mode Sense: 43 00 00 00
Feb 25 19:57:55 lab kernel: [199589.302794] sd 13:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Feb 25 19:57:55 lab kernel: [199589.320186]  sdb: sdb1
Feb 25 19:57:55 lab kernel: [199589.321097] sd 13:0:0:0: [sdb] Attached SCSI removable disk
Feb 25 19:57:56 lab kernel: [199589.503471] FAT-fs (sdb1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
Feb 26 03:22:23 lab kernel: [226309.639763] usb 1-4: USB disconnect, device number 11
Feb 26 14:26:36 lab kernel: [    0.000000] CPU0 microcode updated early to revision 0x8e, date = 2018-03-24
Feb 26 14:26:36 lab kernel: [    0.000000] Initializing cgroup subsys cpuset
Feb 26 14:26:36 lab kernel: [    0.000000] Initializing cgroup subsys cpu
Feb 26 14:26:36 lab kernel: [    0.000000] Initializing cgroup subsys cpuacct
Feb 26 14:26:36 lab kernel: [    0.000000] Linux version 3.13.0-165-generic (buildd@lcy01-amd64-025) (gcc version 4.8.4 (Ubuntu 4.8.4-2ubuntu1~14.04.4) ) #215-Ubuntu SMP Wed Jan 16 11:46:47 UTC 2019 (Ubuntu 3.13.0-165.215-generic 3.13.11-ckt39)
Feb 26 14:26:36 lab kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-165-generic.efi.signed root=UUID=c0eee90f-7184-4ed5-a6a8-8c87a33425e0 ro quiet splash usbcore.usbfs_memory_mb=256 vt.handoff=7
Feb 26 14:26:36 lab kernel: [    0.000000] KERNEL supported cpus:
Feb 26 14:26:36 lab kernel: [    0.000000]   Intel GenuineIntel
Feb 26 14:26:36 lab kernel: [    0.000000]   AMD AuthenticAMD
Feb 26 14:26:36 lab kernel: [    0.000000]   Centaur CentaurHauls
Feb 26 14:26:36 lab kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Feb 26 14:26:36 lab kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x0000000000057fff] usable
Feb 26 14:26:36 lab kernel: [    0.000000] BIOS-e820: [mem 0x0000000000058000-0x0000000000058fff] reserved
Feb 26 14:26:36 lab kernel: [    0.000000] BIOS-e820: [mem 0x0000000000059000-0x000000000009efff] usable
Feb 26 14:26:36 lab kernel: [    0.000000] BIOS-e820: [mem 0x000000000009f000-0x00000000000fffff] reserved
Feb 26 14:26:36 lab kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x0000000085408fff] usable
Feb 26 14:26:36 lab kernel: [    0.000000] BIOS-e820: [mem 0x0000000085409000-0x0000000085409fff] ACPI NVS
Feb 26 14:26:36 lab kernel: [    0.000000] BIOS-e820: [mem 0x000000008540a000-0x000000008540afff] reserved
Feb 26 14:26:36 lab kernel: [    0.000000] BIOS-e820: [mem 0x000000008540b000-0x000000008e5a2fff] usable
Feb 26 14:26:36 lab kernel: [    0.000000] BIOS-e820: [mem 0x000000008e5a3000-0x000000008e8fefff] reserved
Feb 26 14:26:36 lab kernel: [    0.000000] BIOS-e820: [mem 0x000000008e8ff000-0x000000008ea93fff] usable
Feb 26 14:26:36 lab kernel: [    0.000000] BIOS-e820: [mem 0x000000008ea94000-0x000000008f0fffff] ACPI NVS
Feb 26 14:26:36 lab kernel: [    0.000000] BIOS-e820: [mem 0x000000008f100000-0x000000008fba2fff] reserved
Feb 26 14:26:36 lab kernel: [    0.000000] BIOS-e820: [mem 0x000000008fba3000-0x000000008fbfefff] type 20
Feb 26 14:26:36 lab kernel: [    0.000000] BIOS-e820: [mem 0x000000008fbff000-0x000000008fbfffff] usable
Feb 26 14:26:36 lab kernel: [    0.000000] BIOS-e820: [mem 0x000000008fc00000-0x000000008fffffff] reserved
Feb 26 14:26:36 lab kernel: [    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
Feb 26 14:26:36 lab kernel: [    0.000000] BIOS-e820: [mem 0x00000000fe000000-0x00000000fe010fff] reserved
Feb 26 14:26:36 lab kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
Feb 26 14:26:36 lab kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed00fff] reserved
Feb 26 14:26:36 lab kernel: [    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
Feb 26 14:26:36 lab kernel: [    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
Feb 26 14:26:36 lab kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000046effffff] usable
Feb 26 14:26:36 lab kernel: [    0.000000] NX (Execute Disable) protection: active
Feb 26 14:26:36 lab kernel: [    0.000000] efi: EFI v2.50 by American Megatrends
Feb 26 14:26:36 lab kernel: [    0.000000] efi:  ACPI=0x8f094000  ACPI 2.0=0x8f094000  SMBIOS=0xf05e0  MPS=0xfc470 
Feb 26 14:26:36 lab kernel: [    0.000000] efi: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000008000) (0MB)
Feb 26 14:26:36 lab kernel: [    0.000000] efi: mem01: type=7, attr=0xf, range=[0x0000000000008000-0x0000000000058000) (0MB)
Feb 26 14:26:36 lab kernel: [    0.000000] efi: mem02: type=0, attr=0xf, range=[0x0000000000058000-0x0000000000059000) (0MB)
Feb 26 14:26:36 lab kernel: [    0.000000] efi: mem03: type=7, attr=0xf, range=[0x0000000000059000-0x000000000005f000) (0MB)
Feb 26 14:26:36 lab kernel: [    0.000000] efi: mem04: type=4, attr=0xf, range=[0x000000000005f000-0x0000000000060000) (0MB)

```



Below is the content of blacklist.conf
```

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.


# evbug is a debug tool that should be loaded explicitly
blacklist evbug


# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd


# replaced by e100
blacklist eepro100


# replaced by tulip
blacklist de4x5


# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394


# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m


# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2


# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801


# replaced by p54pci
blacklist prism54


# replaced by b43 and ssb.
blacklist bcm43xx


# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps


# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi


# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp


# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr


# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


# blacklist the noveau drivers
blacklist nouveau
blacklist lbm-nouveau
options nouveau modeset=0
alias nouveau off
alias lbm-nouveau off

```

[B]Pastebin Links:
[/B] 
[LIST=1]
[*][kern.log]("https://pastebin.com/qu5bvu79")
[*][Xorg.0.log]("https://pastebin.com/5BuE7YZE")
[/LIST]

**My Observation:** I found something related to NVIDIA inside Xorg.0.log file at line number 163 as shown below:
```

[    22.722] (EE) NVIDIA: Failed to initialize the NVIDIA kernel module. Please see the[    22.722] (EE) NVIDIA:     system's kernel log for additional error messages and
[    22.722] (EE) NVIDIA:     consult the NVIDIA README for details.

```

---

### Post by mastablasta on 2019-02-26
> **Bashing-om said:**
>  However, booting with the 'nomodeset' kernel boot parameter gives a usable system.

nomodeset switches off GPU acceleration, right?

> **ravi_joshi said:**
> Hello CatKiller and Bashing-om,

Thank you very much for your help. I am following your advice and I tried once again installing NVIDIA driver version 384.130 (proprietary) from "additional drivers" under "software and updates". Although, I have added "ppa:graphics-drivers/ppa -y" and I can see recent new versions of NVIDIA driver under the same window but I chose version 384.130 (proprietary) since Ubuntu 14.04 is too old to support new versions (maybe!).



i too had issues with nvidia and 14.04. i got wrong resolution on nouveau (that was solvable) and only text mode with blinking cursor with GPU drivers installed. i returned the card after that. anyway, is there a chance you do an upgrade to latest version? the 14.04 is supported only until april this year unless you bought some extended support. 

also try to boot using older kernel. hold shift at boot to get to grub menu.

finally, my troubles tought me that nvidia (driver) also has their own logs and troubleshooting procedure. check the nvidia on linux forums and you can also post there.

---

### Post by ravi_joshi on 2019-02-26
Hi mastablasta,

Thank you very much.

> **mastablasta said:**
>  is there a chance you do an upgrade to latest version?

I am restricted to Ubutun 14.04 due to some project limitations at this point. Please note that this PC with Ubuntu 14.04 along with the same graphics card used to work in the past few weeks earlier. However suddenly, a few days before, after restarting the PC, this problem arrived.


> **mastablasta said:**
>  try to boot using older kernel. hold shift at boot to get to grub menu.

I just ran "uname -r" and found that I am using 3.13.0-165-generic kernel. I will check with 3.12 and 3.10 and let you know the status by tomorrow.

---

### Post by ravi_joshi on 2019-02-28
It seems that the package shim-signed was the culprit. Hence after removing it, I reinstalled NVIDIA. We need to restart the PC and it works

```

sudo apt-get remove shim-signed
sudo apt-get install nvidia-384

```

The secure boot was disabled in my PC from the BIOS menu. Please note that the answer is originally posted [here]("https://askubuntu.com/a/1121510/569883"). Thank you very much!

---

### Post by CatKiller on 2019-02-28
Glad to hear that you found a solution that works. Don't forget to mark the thread as Solved, to help others find a solution.

---

### Post by ravi_joshi on 2019-02-28
Thanks, CatKiller. I have marked the thread as Solved.

---

