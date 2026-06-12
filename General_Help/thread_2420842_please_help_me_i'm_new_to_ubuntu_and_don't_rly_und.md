---
title: "please help me i'm new to ubuntu and don't rly understand -sound don't work"
date: 2019-06-11
forum: General Help
---

### Post by jdchurchill on 2019-06-11
okay so i have this problem with my sound not working.  i've looked at alot of help pages and none of the fixes are working for me.  for example, every step in this one did not fix the problem [https://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/](https://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/)  
i've checked alsamixer and that all seems fine.  it's not a stupid cable mixup cuz it's one hdmi cable.  i'm just frustrated and confused.  
i don't have a dummy output.  when i open sound settings i have 'Digital Output (S/PDIF) built in audio.  and when i do lspci -v i get 

                       ```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] RS880 Host Bridge
    Subsystem: Advanced Micro Devices, Inc. [AMD] RS880 Host Bridge
    Flags: bus master, 66MHz, medium devsel, latency 0, NUMA node 0
    Capabilities: <access denied>

00:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (int gfx) (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, medium devsel, latency 64, NUMA node 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fe900000-feafffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: <access denied>

00:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 17, NUMA node 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: feb00000-febfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] (prog-if 01 [AHCI 1.0])
    Subsystem: Micro-Star International Co., Ltd. [MSI] SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22, NUMA node 0
    I/O ports at c000 [size=8]
    I/O ports at b000 [size=4]
    I/O ports at a000 [size=8]
    I/O ports at 9000 [size=4]
    I/O ports at 8000 [size=16]
    Memory at fe8ffc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Micro-Star International Co., Ltd. [MSI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16, NUMA node 0
    Memory at fe8fe000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci

00:12.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller (prog-if 10 [OHCI])
    Subsystem: Micro-Star International Co., Ltd. [MSI] SB7x0 USB OHCI1 Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16, NUMA node 0
    Memory at fe8fd000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci

00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Micro-Star International Co., Ltd. [MSI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17, NUMA node 0
    Memory at fe8ff800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Micro-Star International Co., Ltd. [MSI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18, NUMA node 0
    Memory at fe8fc000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci

00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller (prog-if 10 [OHCI])
    Subsystem: Micro-Star International Co., Ltd. [MSI] SB7x0 USB OHCI1 Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18, NUMA node 0
    Memory at fe8fb000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci

00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19, NUMA node 0
    Memory at fe8ff400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 3c)
    Subsystem: Micro-Star International Co., Ltd. [MSI] SBx00 SMBus Controller
    Flags: 66MHz, medium devsel, NUMA node 0
    Capabilities: <access denied>
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c_piix4, sp5100_tco

00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller (prog-if 8a [ISA Compatibility mode controller, supports both channels switched to PCI native mode, supports bus mastering])
    Subsystem: Micro-Star International Co., Ltd. [MSI] SB7x0/SB8x0/SB9x0 IDE Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16, NUMA node 0
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4
    I/O ports at 0170 [size=8]
    I/O ports at 0374
    I/O ports at ff00 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp, pata_acpi

00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)
    Subsystem: Micro-Star International Co., Ltd. [MSI] SBx00 Azalia (Intel HDA)
    Flags: bus master, slow devsel, latency 64, IRQ 16, NUMA node 0
    Memory at fe8f4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller
    Flags: bus master, 66MHz, medium devsel, latency 0, NUMA node 0

00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
    Flags: bus master, 66MHz, medium devsel, latency 64, NUMA node 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=64

00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller (prog-if 10 [OHCI])
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18, NUMA node 0
    Memory at fe8fa000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci

00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor HyperTransport Configuration
    Flags: fast devsel, NUMA node 0
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Address Map
    Flags: fast devsel, NUMA node 0

00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor DRAM Controller
    Flags: fast devsel, NUMA node 0

00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Miscellaneous Control
    Flags: fast devsel, NUMA node 0
    Capabilities: <access denied>
    Kernel driver in use: k10temp
    Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Link Control
    Flags: fast devsel, NUMA node 0

01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS880 [Radeon HD 4250] (prog-if 00 [VGA controller])
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] RS880 [Radeon HD 4250]
    Flags: bus master, fast devsel, latency 0, IRQ 18, NUMA node 0
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at d000 [size=256]
    Memory at feaf0000 (32-bit, non-prefetchable) [size=64K]
    Memory at fe900000 (32-bit, non-prefetchable) [size=1M]
    [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon

01:05.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RS880 HDMI Audio [Radeon HD 4200 Series]
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] RS880 HDMI Audio [Radeon HD 4200 Series]
    Flags: bus master, fast devsel, latency 0, IRQ 19, NUMA node 0
    Memory at feae8000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

02:00.0 Ethernet controller: Qualcomm Atheros AR8131 Gigabit Ethernet (rev c0)
    Subsystem: Micro-Star International Co., Ltd. [MSI] AR8131 Gigabit Ethernet
    Flags: bus master, fast devsel, latency 0, IRQ 24, NUMA node 0
    Memory at febc0000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at e800 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: atl1c
    Kernel modules: atl1c  
```
so it seems like it's not a problem of the sound card not being detected and the drivers not being installed.  but i don't know what to do to get my damn sound back on.  please help.

---

### Post by &amp;wP*!) on 2019-06-11
You are talking about an HDMI cable.  Have you got sound without an HDMI?

Secondly, run **[COLOR="#FF0000"]sudo[/COLOR] lscpi -v**, not **lspci -v**, and gives us the output.

Have you checked the steps described [here]("https://wiki.ubuntu.com/Audio/Testing")?

---

### Post by jdchurchill on 2019-06-11
i am looking at the link now, but at a glance lspci -v and sudo lspci -v gives the same response.  i don't have any other cables than the hdmi currently, but the thing used to work before i upgraded the software.

---

### Post by jdchurchill on 2019-06-11
if i do pavucontrol it looks like it's registering decibels but i can't hear them.  and i did 
rm -r ~/.config/pulse; pulseaudio -k 

still no sound.  does 18.10 come with firerstarter firewall?

---

### Post by jdchurchill on 2019-06-11
following the troubleshooting link: if i check the contents of 
/proc/asound/cards it say
bash: proc/asound/cards: Permission denied
but aplay -l gives me
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1828S Analog [VT1828S Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: VT1828S Digital [VT1828S Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 2: VT1828S Alt Analog [VT1828S Alt Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

so it seems to be recognized.  alsamixer is no mutes.  i am confused abt generating a logfile or log output cuz the link mentions 12.10, will that still work?

---

### Post by jdchurchill on 2019-06-11
```
'pactl list' gives me 
 Module #0
    Name: module-device-restore
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Automatically restore the volume/mute state of devices"
        module.version = "12.2"

Module #1
    Name: module-stream-restore
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Automatically restore the volume/mute/device state of streams"
        module.version = "12.2"

Module #2
    Name: module-card-restore
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Automatically restore profile of cards"
        module.version = "12.2"

Module #3
    Name: module-augment-properties
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Augment the property sets of streams with additional static information"
        module.version = "12.2"

Module #4
    Name: module-switch-on-port-available
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "David Henningsson"
        module.description = "Switches ports and profiles when devices are plugged/unplugged"
        module.version = "12.2"

Module #5
    Name: module-switch-on-connect
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Michael Terry"
        module.description = "When a sink/source is added, switch to it or conditionally switch to it"
        module.version = "12.2"

Module #6
    Name: module-udev-detect
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Detect available audio hardware and load matching drivers"
        module.version = "12.2"

Module #7
    Name: module-alsa-card
    Argument: device_id="1" name="pci-0000_01_05.1" card_name="alsa_card.pci-0000_01_05.1" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes card_properties="module-udev-detect.discovered=1"
    Usage counter: 0
    Properties:
        module.author = "Lennart Poettering"
        module.description = "ALSA Card"
        module.version = "12.2"

Module #8
    Name: module-alsa-card
    Argument: device_id="0" name="pci-0000_00_14.2" card_name="alsa_card.pci-0000_00_14.2" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes card_properties="module-udev-detect.discovered=1"
    Usage counter: 1
    Properties:
        module.author = "Lennart Poettering"
        module.description = "ALSA Card"
        module.version = "12.2"

Module #9
    Name: module-bluetooth-policy
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Frédéric Dalleau, Pali Rohár"
        module.description = "Policy module to make using bluetooth devices out-of-the-box easier"
        module.version = "12.2"

Module #10
    Name: module-bluetooth-discover
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "João Paulo Rechi Vita"
        module.description = "Detect available Bluetooth daemon and load the corresponding discovery module"
        module.version = "12.2"

Module #11
    Name: module-bluez5-discover
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "João Paulo Rechi Vita"
        module.description = "Detect available BlueZ 5 Bluetooth audio devices and load BlueZ 5 Bluetooth audio drivers"
        module.version = "12.2"

Module #12
    Name: module-native-protocol-unix
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Native protocol (UNIX sockets)"
        module.version = "12.2"

Module #13
    Name: module-default-device-restore
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Automatically restore the default sink and source"
        module.version = "12.2"

Module #14
    Name: module-rescue-streams
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "When a sink/source is removed, try to move its streams to the default sink/source"
        module.version = "12.2"

Module #15
    Name: module-always-sink
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Colin Guthrie"
        module.description = "Always keeps at least one sink loaded even if it's a null one"
        module.version = "12.2"

Module #16
    Name: module-intended-roles
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Automatically set device of streams based on intended roles of devices"
        module.version = "12.2"

Module #17
    Name: module-suspend-on-idle
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "When a sink/source is idle for too long, suspend it"
        module.version = "12.2"

Module #18
    Name: module-console-kit
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Create a client for each ConsoleKit session of this user"
        module.version = "12.2"

Module #19
    Name: module-systemd-login
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Create a client for each login session of this user"
        module.version = "12.2"

Module #20
    Name: module-position-event-sounds
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Position event sounds between L and R depending on the position on screen of the widget triggering them."
        module.version = "12.2"

Module #21
    Name: module-role-cork
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Mute & cork streams with certain roles while others exist"
        module.version = "12.2"

Module #22
    Name: module-snap-policy
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Canonical Ltd"
        module.description = "Ubuntu Snap policy management"
        module.version = "12.2"

Module #23
    Name: module-filter-heuristics
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Colin Guthrie"
        module.description = "Detect when various filters are desirable"
        module.version = "12.2"

Module #24
    Name: module-filter-apply
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Colin Guthrie"
        module.description = "Load filter sinks automatically when needed"
        module.version = "12.2"

Module #25
    Name: module-x11-publish
    Argument: display=:0
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "X11 credential publisher"
        module.version = "12.2"

Module #26
    Name: module-x11-bell
    Argument: display=:0 sample=bell.ogg
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "X11 bell interceptor"
        module.version = "12.2"

Module #27
    Name: module-x11-cork-request
    Argument: display=:0
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Synthesize X11 media key events when cork/uncork is requested"
        module.version = "12.2"

Module #28
    Name: module-x11-xsmp
    Argument: display=:0 session_manager=local/bing-bong:@/tmp/.ICE-unix/2282,unix/bing-bong:/tmp/.ICE-unix/2282
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "X11 session management"
        module.version = "12.2"

Sink #0
    State: RUNNING
    Name: alsa_output.pci-0000_00_14.2.iec958-stereo
    Description: Built-in Audio Digital Stereo (IEC958)
    Driver: module-alsa-card.c
    Sample Specification: s16le 2ch 44100Hz
    Channel Map: front-left,front-right
    Owner Module: 8
    Mute: no
    Volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
            balance 0.00
    Base Volume: 65536 / 100% / 0.00 dB
    Monitor Source: alsa_output.pci-0000_00_14.2.iec958-stereo.monitor
    Latency: 70285 usec, configured 90000 usec
    Flags: HARDWARE HW_MUTE_CTRL DECIBEL_VOLUME LATENCY SET_FORMATS 
    Properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "VT1828S Digital"
        alsa.id = "VT1828S Digital"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "1"
        alsa.card = "0"
        alsa.card_name = "HDA ATI SB"
        alsa.long_card_name = "HDA ATI SB at 0xfe8f4000 irq 16"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:14.2"
        sysfs.path = "/devices/pci0000:00/0000:00:14.2/sound/card0"
        device.bus = "pci"
        device.vendor.id = "1002"
        device.vendor.name = "Advanced Micro Devices, Inc. [AMD/ATI]"
        device.product.id = "4383"
        device.product.name = "SBx00 Azalia (Intel HDA)"
        device.form_factor = "internal"
        device.string = "iec958:0"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "iec958-stereo"
        device.profile.description = "Digital Stereo (IEC958)"
        device.description = "Built-in Audio Digital Stereo (IEC958)"
        alsa.mixer_name = "VIA VT1828S"
        alsa.components = "HDA:11064441,14627623,00100100"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    Ports:
        iec958-stereo-output: Digital Output (S/PDIF) (priority: 0)
    Active Port: iec958-stereo-output
    Formats:
        pcm

Source #0
    State: IDLE
    Name: alsa_output.pci-0000_00_14.2.iec958-stereo.monitor
    Description: Monitor of Built-in Audio Digital Stereo (IEC958)
    Driver: module-alsa-card.c
    Sample Specification: s16le 2ch 44100Hz
    Channel Map: front-left,front-right
    Owner Module: 8
    Mute: no
    Volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
            balance 0.00
    Base Volume: 65536 / 100% / 0.00 dB
    Monitor of Sink: alsa_output.pci-0000_00_14.2.iec958-stereo
    Latency: 0 usec, configured 371519 usec
    Flags: DECIBEL_VOLUME LATENCY 
    Properties:
        device.description = "Monitor of Built-in Audio Digital Stereo (IEC958)"
        device.class = "monitor"
        alsa.card = "0"
        alsa.card_name = "HDA ATI SB"
        alsa.long_card_name = "HDA ATI SB at 0xfe8f4000 irq 16"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:14.2"
        sysfs.path = "/devices/pci0000:00/0000:00:14.2/sound/card0"
        device.bus = "pci"
        device.vendor.id = "1002"
        device.vendor.name = "Advanced Micro Devices, Inc. [AMD/ATI]"
        device.product.id = "4383"
        device.product.name = "SBx00 Azalia (Intel HDA)"
        device.form_factor = "internal"
        device.string = "0"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    Formats:
        pcm

Source #1
    State: SUSPENDED
    Name: alsa_input.pci-0000_00_14.2.analog-stereo
    Description: Built-in Audio Analog Stereo
    Driver: module-alsa-card.c
    Sample Specification: s16le 2ch 44100Hz
    Channel Map: front-left,front-right
    Owner Module: 8
    Mute: no
    Volume: front-left: 10093 /  15% / -48.75 dB,   front-right: 10093 /  15% / -48.75 dB
            balance 0.00
    Base Volume: 6368 /  10% / -60.75 dB
    Monitor of Sink: n/a
    Latency: 0 usec, configured 0 usec
    Flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY 
    Properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "VT1828S Analog"
        alsa.id = "VT1828S Analog"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "0"
        alsa.card_name = "HDA ATI SB"
        alsa.long_card_name = "HDA ATI SB at 0xfe8f4000 irq 16"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:14.2"
        sysfs.path = "/devices/pci0000:00/0000:00:14.2/sound/card0"
        device.bus = "pci"
        device.vendor.id = "1002"
        device.vendor.name = "Advanced Micro Devices, Inc. [AMD/ATI]"
        device.product.id = "4383"
        device.product.name = "SBx00 Azalia (Intel HDA)"
        device.form_factor = "internal"
        device.string = "front:0"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "analog-stereo"
        device.profile.description = "Analog Stereo"
        device.description = "Built-in Audio Analog Stereo"
        alsa.mixer_name = "VIA VT1828S"
        alsa.components = "HDA:11064441,14627623,00100100"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    Ports:
        analog-input-front-mic: Front Microphone (priority: 8500, not available)
        analog-input-rear-mic: Rear Microphone (priority: 8200, not available)
        analog-input-linein: Line In (priority: 8100, not available)
    Active Port: analog-input-front-mic
    Formats:
        pcm

Sink Input #3
    Driver: protocol-native.c
    Owner Module: 12
    Client: 19
    Sink: 0
    Sample Specification: float32le 2ch 44100Hz
    Channel Map: front-left,front-right
    Format: pcm, format.sample_format = "\"float32le\""  format.channels = "2"  format.rate = "44100"  format.channel_map = "\"front-left,front-right\""
    Corked: no
    Mute: no
    Volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
            balance 0.00
    Buffer Latency: 104603 usec
    Sink Latency: 69776 usec
    Resample method: copy
    Properties:
        media.name = "'El Carretero' by 'Buena Vista Social Club'"
        application.name = "Rhythmbox"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "32"
        media.role = "music"
        application.process.id = "3524"
        application.process.user = "jd"
        application.process.host = "bing-bong"
        application.process.binary = "rhythmbox"
        application.icon_name = "rhythmbox"
        application.language = "en_US.UTF-8"
        window.x11.display = ":0"
        application.process.machine_id = "1b1bc546acab4b3a8373b725750ada85"
        module-stream-restore.id = "sink-input-by-media-role:music"
        media.title = " El Carretero"
        media.artist = "Buena Vista Social Club "

Client #0
    Driver: module-systemd-login.c
    Owner Module: 19
    Properties:
        application.name = "Login Session c1"
        systemd-login.session = "c1"

Client #1
    Driver: protocol-native.c
    Owner Module: 12
    Properties:
        application.name = "Ubuntu Audio Settings"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "32"
        application.id = "com.canonical.settings.sound"
        application.icon_name = "multimedia-volume-control"
        application.version = "0.1"
        application.process.id = "2276"
        application.process.user = "jd"
        application.process.host = "bing-bong"
        application.process.binary = "indicator-sound-service"
        application.language = "en_US.UTF-8"
        window.x11.display = ":0"
        application.process.machine_id = "1b1bc546acab4b3a8373b725750ada85"

Client #2
    Driver: protocol-native.c
    Owner Module: 12
    Properties:
        application.name = "Ubuntu Audio Settings"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "32"
        application.id = "com.canonical.settings.sound"
        application.icon_name = "multimedia-volume-control"
        application.version = "0.1"
        application.process.id = "2276"
        application.process.user = "jd"
        application.process.host = "bing-bong"
        application.process.binary = "indicator-sound-service"
        application.language = "en_US.UTF-8"
        window.x11.display = ":0"
        application.process.machine_id = "1b1bc546acab4b3a8373b725750ada85"

Client #3
    Driver: protocol-native.c
    Owner Module: 12
    Properties:
        application.name = "GNOME Volume Control Media Keys"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "32"
        application.id = "org.gnome.VolumeControl"
        application.icon_name = "multimedia-volume-control"
        application.version = "1.0"
        application.process.id = "2278"
        application.process.user = "jd"
        application.process.host = "bing-bong"
        application.process.binary = "unity-settings-daemon"
        application.language = "en_US.UTF-8"
        window.x11.display = ":0"
        application.process.machine_id = "1b1bc546acab4b3a8373b725750ada85"

Client #9
    Driver: module-x11-xsmp.c
    Owner Module: 28
    Properties:
        application.name = "XSMP Session on gnome-session as 105404e29d878776c2156029016868903500000022820056"
        xsmp.vendor = "gnome-session"
        xsmp.client.id = "105404e29d878776c2156029016868903500000022820056"

Client #10
    Driver: protocol-native.c
    Owner Module: 12
    Properties:
        application.name = "Firefox"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "32"
        window.x11.display = ":0"
        window.x11.screen = "0"
        application.process.id = "2930"
        application.process.user = "jd"
        application.process.host = "bing-bong"
        application.process.binary = "firefox"
        application.language = "en_US.UTF-8"
        application.process.machine_id = "1b1bc546acab4b3a8373b725750ada85"
        application.icon_name = "firefox"

Client #11
    Driver: protocol-native.c
    Owner Module: 12
    Properties:
        application.name = "Firefox"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "32"
        application.icon_name = "firefox"
        application.version = "67.0.1"
        application.process.id = "2930"
        application.process.user = "jd"
        application.process.host = "bing-bong"
        application.process.binary = "firefox"
        application.language = "en_US.UTF-8"
        window.x11.display = ":0"
        application.process.machine_id = "1b1bc546acab4b3a8373b725750ada85"

Client #12
    Driver: protocol-native.c
    Owner Module: 12
    Properties:
        application.name = "Rhythmbox"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "32"
        application.icon_name = "rhythmbox"
        window.x11.display = ":0"
        window.x11.screen = "0"
        media.role = "music"
        application.process.id = "3524"
        application.process.user = "jd"
        application.process.host = "bing-bong"
        application.process.binary = "rhythmbox"
        application.language = "en_US.UTF-8"
        application.process.machine_id = "1b1bc546acab4b3a8373b725750ada85"

Client #15
    Driver: protocol-native.c
    Owner Module: 12
    Properties:
        application.name = "Terminal"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "32"
        application.icon_name = "utilities-terminal"
        window.x11.display = ":0"
        window.x11.screen = "0"
        application.process.id = "3701"
        application.process.user = "jd"
        application.process.host = "bing-bong"
        application.process.binary = "gnome-terminal-server"
        application.language = "en_US.UTF-8"
        application.process.machine_id = "1b1bc546acab4b3a8373b725750ada85"

Client #19
    Driver: protocol-native.c
    Owner Module: 12
    Properties:
        application.name = "Rhythmbox"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "32"
        media.role = "music"
        application.process.id = "3524"
        application.process.user = "jd"
        application.process.host = "bing-bong"
        application.process.binary = "rhythmbox"
        application.icon_name = "rhythmbox"
        application.language = "en_US.UTF-8"
        window.x11.display = ":0"
        application.process.machine_id = "1b1bc546acab4b3a8373b725750ada85"

Client #21
    Driver: protocol-native.c
    Owner Module: 12
    Properties:
        application.name = "pactl"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "32"
        application.process.id = "3957"
        application.process.user = "jd"
        application.process.host = "bing-bong"
        application.process.binary = "pactl"
        application.language = "en_US.UTF-8"
        window.x11.display = ":0"
        application.process.machine_id = "1b1bc546acab4b3a8373b725750ada85"

Sample #0
    Name: bell.ogg
    Sample Specification: float32le 1ch 44100Hz
    Channel Map: mono
    Volume: (invalid)
            balance 0.00
    Duration: 0.2s
    Size: 34.5 KiB
    Lazy: no
    Filename: n/a
    Properties:
        media.role = "event"
        media.name = "bell.ogg"
        application.name = "pactl"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "32"
        application.process.id = "2616"
        application.process.user = "jd"
        application.process.host = "bing-bong"
        application.process.binary = "pactl"
        application.language = "en_US.UTF-8"
        window.x11.display = ":0"
        application.process.machine_id = "1b1bc546acab4b3a8373b725750ada85"

Card #0
    Name: alsa_card.pci-0000_01_05.1
    Driver: module-alsa-card.c
    Owner Module: 7
    Properties:
        alsa.card = "1"
        alsa.card_name = "HDA ATI HDMI"
        alsa.long_card_name = "HDA ATI HDMI at 0xfeae8000 irq 19"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:01:05.1"
        sysfs.path = "/devices/pci0000:00/0000:00:01.0/0000:01:05.1/sound/card1"
        device.bus = "pci"
        device.vendor.id = "1002"
        device.vendor.name = "Advanced Micro Devices, Inc. [AMD/ATI]"
        device.product.id = "970f"
        device.product.name = "RS880 HDMI Audio [Radeon HD 4200 Series]"
        device.string = "1"
        device.description = "RS880 HDMI Audio [Radeon HD 4200 Series]"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    Profiles:
        output:hdmi-stereo: Digital Stereo (HDMI) Output (sinks: 1, sources: 0, priority: 5900, available: no)
        output:hdmi-surround: Digital Surround 5.1 (HDMI) Output (sinks: 1, sources: 0, priority: 800, available: no)
        output:hdmi-surround71: Digital Surround 7.1 (HDMI) Output (sinks: 1, sources: 0, priority: 800, available: no)
        off: Off (sinks: 0, sources: 0, priority: 0, available: yes)
    Active Profile: off
    Ports:
        hdmi-output-0: HDMI / DisplayPort (priority: 5900, latency offset: 0 usec, not available)
            Properties:
                device.icon_name = "video-display"
            Part of profile(s): output:hdmi-stereo, output:hdmi-surround, output:hdmi-surround71

Card #1
    Name: alsa_card.pci-0000_00_14.2
    Driver: module-alsa-card.c
    Owner Module: 8
    Properties:
        alsa.card = "0"
        alsa.card_name = "HDA ATI SB"
        alsa.long_card_name = "HDA ATI SB at 0xfe8f4000 irq 16"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:14.2"
        sysfs.path = "/devices/pci0000:00/0000:00:14.2/sound/card0"
        device.bus = "pci"
        device.vendor.id = "1002"
        device.vendor.name = "Advanced Micro Devices, Inc. [AMD/ATI]"
        device.product.id = "4383"
        device.product.name = "SBx00 Azalia (Intel HDA)"
        device.form_factor = "internal"
        device.string = "0"
        device.description = "Built-in Audio"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    Profiles:
        input:analog-stereo: Analog Stereo Input (sinks: 0, sources: 1, priority: 65, available: no)
        output:analog-stereo: Analog Stereo Output (sinks: 1, sources: 0, priority: 6500, available: no)
        output:analog-stereo+input:analog-stereo: Analog Stereo Duplex (sinks: 1, sources: 1, priority: 6565, available: no)
        output:analog-surround-21: Analog Surround 2.1 Output (sinks: 1, sources: 0, priority: 1300, available: no)
        output:analog-surround-21+input:analog-stereo: Analog Surround 2.1 Output + Analog Stereo Input (sinks: 1, sources: 1, priority: 1365, available: no)
        output:analog-surround-40: Analog Surround 4.0 Output (sinks: 1, sources: 0, priority: 1200, available: no)
        output:analog-surround-40+input:analog-stereo: Analog Surround 4.0 Output + Analog Stereo Input (sinks: 1, sources: 1, priority: 1265, available: no)
        output:analog-surround-41: Analog Surround 4.1 Output (sinks: 1, sources: 0, priority: 1300, available: no)
        output:analog-surround-41+input:analog-stereo: Analog Surround 4.1 Output + Analog Stereo Input (sinks: 1, sources: 1, priority: 1365, available: no)
        output:analog-surround-50: Analog Surround 5.0 Output (sinks: 1, sources: 0, priority: 1200, available: no)
        output:analog-surround-50+input:analog-stereo: Analog Surround 5.0 Output + Analog Stereo Input (sinks: 1, sources: 1, priority: 1265, available: no)
        output:analog-surround-51: Analog Surround 5.1 Output (sinks: 1, sources: 0, priority: 1300, available: no)
        output:analog-surround-51+input:analog-stereo: Analog Surround 5.1 Output + Analog Stereo Input (sinks: 1, sources: 1, priority: 1365, available: no)
        output:analog-surround-71: Analog Surround 7.1 Output (sinks: 1, sources: 0, priority: 1200, available: no)
        output:analog-surround-71+input:analog-stereo: Analog Surround 7.1 Output + Analog Stereo Input (sinks: 1, sources: 1, priority: 1265, available: no)
        output:iec958-stereo: Digital Stereo (IEC958) Output (sinks: 1, sources: 0, priority: 5500, available: yes)
        output:iec958-stereo+input:analog-stereo: Digital Stereo (IEC958) Output + Analog Stereo Input (sinks: 1, sources: 1, priority: 5565, available: yes)
        off: Off (sinks: 0, sources: 0, priority: 0, available: yes)
    Active Profile: output:iec958-stereo+input:analog-stereo
    Ports:
        analog-input-front-mic: Front Microphone (priority: 8500, latency offset: 0 usec, not available)
            Properties:
                device.icon_name = "audio-input-microphone"
            Part of profile(s): input:analog-stereo, output:analog-stereo+input:analog-stereo, output:analog-surround-21+input:analog-stereo, output:analog-surround-40+input:analog-stereo, output:analog-surround-41+input:analog-stereo, output:analog-surround-50+input:analog-stereo, output:analog-surround-51+input:analog-stereo, output:analog-surround-71+input:analog-stereo, output:iec958-stereo+input:analog-stereo
        analog-input-rear-mic: Rear Microphone (priority: 8200, latency offset: 0 usec, not available)
            Properties:
                device.icon_name = "audio-input-microphone"
            Part of profile(s): input:analog-stereo, output:analog-stereo+input:analog-stereo, output:analog-surround-21+input:analog-stereo, output:analog-surround-40+input:analog-stereo, output:analog-surround-41+input:analog-stereo, output:analog-surround-50+input:analog-stereo, output:analog-surround-51+input:analog-stereo, output:analog-surround-71+input:analog-stereo, output:iec958-stereo+input:analog-stereo
        analog-input-linein: Line In (priority: 8100, latency offset: 0 usec, not available)
            Part of profile(s): input:analog-stereo, output:analog-stereo+input:analog-stereo, output:analog-surround-21+input:analog-stereo, output:analog-surround-40+input:analog-stereo, output:analog-surround-41+input:analog-stereo, output:analog-surround-50+input:analog-stereo, output:analog-surround-51+input:analog-stereo, output:analog-surround-71+input:analog-stereo, output:iec958-stereo+input:analog-stereo
        analog-output-lineout: Line Out (priority: 9900, latency offset: 0 usec, not available)
            Part of profile(s): output:analog-stereo, output:analog-stereo+input:analog-stereo, output:analog-surround-21, output:analog-surround-21+input:analog-stereo, output:analog-surround-40, output:analog-surround-40+input:analog-stereo, output:analog-surround-41, output:analog-surround-41+input:analog-stereo, output:analog-surround-50, output:analog-surround-50+input:analog-stereo, output:analog-surround-51, output:analog-surround-51+input:analog-stereo, output:analog-surround-71, output:analog-surround-71+input:analog-stereo
        analog-output-headphones: Headphones (priority: 9000, latency offset: 0 usec, not available)
            Properties:
                device.icon_name = "audio-headphones"
            Part of profile(s): output:analog-stereo, output:analog-stereo+input:analog-stereo
        iec958-stereo-output: Digital Output (S/PDIF) (priority: 0, latency offset: 0 usec)
            Part of profile(s): output:iec958-stereo, output:iec958-stereo+input:analog-stereo
```

---

### Post by jdchurchill on 2019-06-13
anything anyone can tell me to help me fix this would really make me happy

---

### Post by jdchurchill on 2019-06-14
if i do
```
sudo nano /etc/pulse/client.conf
```
i get 

code:
```
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, see <http://www.gnu.org/licenses/>.

## Configuration file for PulseAudio clients. See pulse-client.conf(5) for
[COLOR=#06989a]## more information. Default values are commented out.  Use either ; or # for## commenting.[/COLOR]

; default-sink =
; default-source =
; default-server =
; default-dbus-server =

; autospawn = yes
; daemon-binary = /usr/bin/pulseaudio
; extra-arguments = --log-target=syslog

; cookie-file =

; enable-shm = yes
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 M$

; auto-connect-localhost = no
; auto-connect-display = no
```

---

### Post by tea for one on 2019-06-14
> **jdchurchill said:**
> i don't have any other cables than the hdmi currently, but the thing used to work before i upgraded the software.

Which software did you upgrade?

As a suggestion, I would try a live session with only necessary peripherals attached. i.e. monitor, mouse, keyboard. 

You never know, you may have sound?

Lastly, I noticed that you had pulse audio installed, do you have under the configuration tab **Digital Stereo (HDMI) Output + Analogue Stereo Input**?

---

### Post by jdchurchill on 2019-06-15
thanks for your reply
i will try a live session when i have time
as stated above when i do pavucontrol i can see decibels registering, but i can't hear anything
and i am not sure what u mean about the configuration tab for pulse audio.  in sound settings, as stated above there is only one thing
Digital Output (S/PDIF) built in audio
and there is no analogue stereo input

---

### Post by jdchurchill on 2019-06-15
oh and upgraded to 18.10

---

### Post by tea for one on 2019-06-15
> **jdchurchill said:**
> oh and upgraded to 18.10

Therefore, you had sound in Ubuntu 18.04?

---

### Post by TheFu on 2019-06-15
Support for 18.10 ends next month. Probably not worth troubleshooting this on an OS going away. It is time to move to 19.04. Also plan on moving to 19.10 before Xmas. Schedule it now.  These moves are required to stay on a supported Ubuntu.
Or you could go back to 18.04, which will be supported until 2023.  I prefer LTS releases to avoid the forced upgrade every 6 months.  For me, "new" is the enemy of "stable."   I'm on 16.04 for my desktop, as an example.

As for audio issues, I'm terrible at audio stuff, but I believe HDMI audio needs to use the video card drivers for it to work. Are you using the F/LOSS GPU drivers or the proprietary drivers?  From the lspci (which I tend to avoid), it appears you have AMD audio and Intel audio.  If you have an AMD video card, using the AMD audio driver is probably necessary for HDMI audio to work.  I don't know, but suspect the Intel audio probably controls the audio jacks that aren't tied to the video card.  Which gets used when is probably outlined in the motherboard manual.

I find the output from **sudo lshw -C multimedia** to be clear about audio stuff. Without using sudo, we don't get the detailed information that is needed when troubleshooting.

Have you found the audio troubleshooter yet?  There's a script that gathers all the information and posts it for experts to see.  Here it is: [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)  There are 16 steps, including one that uses the script.

---

### Post by jdchurchill on 2019-06-24
ok thanks for the replies
if i do 
sudo lshw -C multimedia 
i get 
```
 
*-multimedia              
       description: Audio device
       product: RS880 HDMI Audio [Radeon HD 4200 Series]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 5.1
       bus info: pci@0000:01:05.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:19 memory:feae8000-feaebfff
  *-multimedia
       description: Audio device
       product: SBx00 Azalia (Intel HDA)
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=snd_hda_intel latency=64
       resources: irq:16 memory:fe8f4000-fe8f7fff

```

i'll look at that troubleshooting guide when i can soon, but how hard would it be to just downgrade?
as i look at this i get scared [https://linuxconfig.org/how-to-downgrade-ubuntu-linux-system-to-its-previous-version](https://linuxconfig.org/how-to-downgrade-ubuntu-linux-system-to-its-previous-version)

---

### Post by TheFu on 2019-06-24
There is no downgrade migration option assuming you are thinking 18.04 as the downgrade target.  You should be scared. This is major surgery.

Basically, you manually backup stuff you don't want to loss, wipe the prior OS and perform a fresh install, being 100% certain to format the disks.  After, you restore the backup files.  I would NOT restore any settings from my HOME directory, since newer versions of the programs were used and likely modified those settings.

---

### Post by jdchurchill on 2019-07-04
ok so now in addition to not having sound, my monitor doesn't work right.  like the aspect ratio is way out of wack: the mouse pointer looks huge and i can't even move around in the gui.  ugh!

---

### Post by jdchurchill on 2019-07-09
how do i do a live session?  i'm really sick of this machine not working and have the time to do it finally.

---

