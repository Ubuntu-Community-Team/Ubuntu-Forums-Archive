---
title: "System updates killed effects..."
date: 2013-02-27
forum: General Help
---

### Post by x C0MMAND0 x on 2013-02-27
Ran system updates, after rebooting all of my desktop effects are disabled.  Please note I am running Kubuntu, and therefore not running Compiz.

Any ideas?  See the screenshot attached.  You can see that around Cairo-Dock there is a "black rectangle".

Not sure what happened.  Any advice?

[[img]http://s17.postimage.org/5abctixiz/snapshot1.jpg[/img]](http://postimage.org/image/5abctixiz/)

---

### Post by dabl on 2013-02-27
Pop open konsole and enter

```
kwin --replace
```

You should either get desktop effects or an error message.

---

### Post by x C0MMAND0 x on 2013-02-27
> **dabl said:**
> Pop open konsole and enter

```
kwin --replace
```

You should either get desktop effects or an error message.

Here is my output...

```

brent@Poseidon:~$ kwin --replace
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
kwin(4997): Failed to initialize compositing, compositing disabled 
kwin(4997): Consult http://techbase.kde.org/Projects/KWin/4.0-release-notes#Setting_up 

```

---

### Post by dabl on 2013-02-27
First, verify that you have these packages installed:

kde-workspace-bin
mesa-utils

If they are both already installed, then it is probably a video driver issue, in which case we need to see the "VGA" device output section from 

```
lspci -vk
```

---

### Post by x C0MMAND0 x on 2013-02-27
Output is:

```

brent@Poseidon:~$ sudo lspci -vk
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
        Subsystem: Dell Device 0209
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] Vendor Specific Information: Len=0a <?>

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: f2000000-f6efffff
        Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
        Capabilities: [88] Subsystem: Dell Device 0209
        Capabilities: [80] Power Management version 3
        Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Capabilities: [a0] Express Root Port (Slot+), MSI 00
        Capabilities: [100] Virtual Channel
        Capabilities: [140] Root Complex Link
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Device 0209
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 6f20 [size=32]
        Kernel driver in use: uhci_hcd

00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Device 0209
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 6f00 [size=32]
        Kernel driver in use: uhci_hcd

00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Dell Device 0209
        Flags: bus master, medium devsel, latency 0, IRQ 22
        Memory at fed1c400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port: BAR=1 offset=00a0
        Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
        Subsystem: Dell Device 0209
        Flags: bus master, fast devsel, latency 0, IRQ 45
        Memory at f6ffc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [100] Virtual Channel
        Capabilities: [130] Root Complex Link
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: f0400000-f05fffff
        Prefetchable memory behind bridge: 00000000f0600000-00000000f07fffff
        Capabilities: [40] Express Root Port (Slot+), MSI 00
        Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Capabilities: [90] Subsystem: Dell Device 0209
        Capabilities: [a0] Power Management version 2
        Capabilities: [100] Virtual Channel
        Capabilities: [180] Root Complex Link
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0c, subordinate=0d, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: f1e00000-f1ffffff
        Prefetchable memory behind bridge: 00000000f0000000-00000000f01fffff
        Capabilities: [40] Express Root Port (Slot+), MSI 00
        Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Capabilities: [90] Subsystem: Dell Device 0209
        Capabilities: [a0] Power Management version 2
        Capabilities: [100] Virtual Channel
        Capabilities: [180] Root Complex Link
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: f1d00000-f1dfffff
        Prefetchable memory behind bridge: 00000000f0200000-00000000f03fffff
        Capabilities: [40] Express Root Port (Slot+), MSI 00
        Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Capabilities: [90] Subsystem: Dell Device 0209
        Capabilities: [a0] Power Management version 2
        Capabilities: [100] Virtual Channel
        Capabilities: [180] Root Complex Link
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Device 0209
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 6f80 [size=32]
        Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Device 0209
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 6f60 [size=32]
        Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Device 0209
        Flags: bus master, medium devsel, latency 0, IRQ 22
        I/O ports at 6f40 [size=32]
        Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Dell Device 0209
        Flags: bus master, medium devsel, latency 0, IRQ 20
        Memory at fed1c000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port: BAR=1 offset=00a0
        Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
        Memory behind bridge: f1c00000-f1cfffff
        Capabilities: [50] Subsystem: Dell Device 0209

00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 02)
        Subsystem: Dell Device 0209
        Flags: bus master, medium devsel, latency 0
        Capabilities: [e0] Vendor Specific Information: Len=0c <?>
        Kernel modules: iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Dell Device 0209
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 6fa0 [size=16]
        Kernel driver in use: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 02) (prog-if 01 [AHCI 1.0])
        Subsystem: Dell Device 0209
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 44
        I/O ports at 6eb0 [size=8]
        I/O ports at 6eb8 [size=4]
        I/O ports at 6ec0 [size=8]
        I/O ports at 6ec8 [size=4]
        I/O ports at 6ee0 [size=32]
        Memory at f6ffb800 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [80] MSI: Enable+ Count=1/4 Maskable- 64bit-
        Capabilities: [70] Power Management version 3
        Capabilities: [a8] SATA HBA v1.0
        Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
        Subsystem: Dell Device 0209
        Flags: medium devsel, IRQ 10
        Memory at f6ffb700 (32-bit, non-prefetchable) [size=256]
        I/O ports at 10c0 [size=32]
        Kernel modules: i2c-i801

01:00.0 VGA compatible controller: NVIDIA Corporation G86 [GeForce 8400M GS] (rev a1) (prog-if 00 [VGA controller])
        Subsystem: Dell Device 0209
        Flags: bus master, fast devsel, latency 0, IRQ 7
        Memory at f5000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at f2000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at ef00 [size=128]
        [virtual] Expansion ROM at f4000000 [disabled] [size=128K]
        Capabilities: [60] Power Management version 2
        Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
        Capabilities: [78] Express Endpoint, MSI 00
        Capabilities: [100] Virtual Channel
        Capabilities: [128] Power Budgeting <?>
        Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
        Kernel modules: nouveau, nvidiafb

03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
        Subsystem: Dell Device 0209
        Flags: bus master, medium devsel, latency 64, IRQ 19
        Memory at f1cff800 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [dc] Power Management version 2
        Kernel driver in use: firewire_ohci
        Kernel modules: firewire-ohci

03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) (prog-if 01)
        Subsystem: Dell Device 0209
        Flags: bus master, medium devsel, latency 64, IRQ 18
        Memory at f1cff500 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2
        Kernel driver in use: sdhci-pci
        Kernel modules: sdhci-pci

03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
        Subsystem: Dell Device 0209
        Flags: bus master, medium devsel, latency 64, IRQ 18
        Memory at f1cff600 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2
        Kernel driver in use: r592
        Kernel modules: r592

03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
        Subsystem: Dell Device 0209
        Flags: bus master, medium devsel, latency 64, IRQ 18
        Memory at f1cff700 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2
        Kernel driver in use: r852
        Kernel modules: r852

09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
        Subsystem: Dell XPS M1330
        Flags: bus master, fast devsel, latency 0, IRQ 46
        Memory at f1df0000 (64-bit, non-prefetchable) [size=64K]
        Expansion ROM at <ignored> [disabled]
        Capabilities: [48] Power Management version 3
        Capabilities: [50] Vital Product Data
        Capabilities: [58] Vendor Specific Information: Len=78 <?>
        Capabilities: [e8] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [d0] Express Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [13c] Virtual Channel
        Capabilities: [160] Device Serial Number 00-21-9b-ff-fe-ed-ba-e4
        Kernel driver in use: tg3
        Kernel modules: tg3

```

Thank you for your help so far.  I know that everything on my system does work fine, as it has been for years.  Something got updated it didn't like...

---

### Post by dabl on 2013-02-27
OK you have an Nvidia 8400M and are using the nouveau driver.  Is that how you were configured before you started having this problem?  Personally I always had better luck with the non-free Nvidia proprietary driver.

---

### Post by x C0MMAND0 x on 2013-02-27
Yes, that is how I was configured.  I didn't change anything.  I literally just ran an apt-get update and apt-get upgrade and it prompted for reboot and things stopped working.

I can definitely change to other nvidia drivers if needed.  Download from their site or is their a better way to do so through CLI?

---

### Post by dabl on 2013-02-27
No, don't download it -- use the "System > Additional Drivers".

But first, open konsole and do these:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by x C0MMAND0 x on 2013-02-27
I didn't to a dist. upgrade (I want to stay on 12.04 LTS).

Attempting to activate any of the drivers listed (version current) (version 173) (post-release) etc failed every time.

I will update with /var/log/jockey.log in a minute and edit this post.

**Output of /var/log/jockey.log**
```

2013-02-27 16:52:25,738 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8>
2013-02-27 16:52:31,998 DEBUG: reading modalias file /lib/modules/3.2.0-34-generic/modules.alias
2013-02-27 16:52:32,117 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-02-27 16:52:32,130 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-02-27 16:52:32,191 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-02-27 16:52:32,257 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2013-02-27 16:52:32,262 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2013-02-27 16:52:32,262 DEBUG: fglrx.available: falling back to default
2013-02-27 16:52:32,553 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2013-02-27 16:52:32,557 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9

2013-02-27 16:52:32,585 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverExperimental9 from name FglrxDriverExperimental9
2013-02-27 16:52:32,586 DEBUG: fglrx.available: falling back to default
2013-02-27 16:52:32,747 DEBUG: ATI/AMD proprietary FGLRX graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-02-27 16:52:32,751 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-02-27 16:52:32,757 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2013-02-27 16:52:32,757 DEBUG: fglrx.available: falling back to default
2013-02-27 16:52:32,933 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2013-02-27 16:52:32,933 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-02-27 16:52:32,938 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-02-27 16:52:32,955 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-02-27 16:52:32,955 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-02-27 16:52:32,956 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-02-27 16:52:32,961 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2013-02-27 16:52:32,962 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-02-27 16:52:32,962 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-02-27 16:52:32,962 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-02-27 16:52:32,971 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2013-02-27 16:52:32,979 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-02-27 16:52:33,149 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-02-27 16:52:33,150 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2013-02-27 16:52:33,154 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx

2013-02-27 16:52:33,155 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2013-02-27 16:52:33,155 DEBUG: cdv.available: falling back to default
2013-02-27 16:52:33,300 DEBUG: Intel Cedarview graphics driver availability undetermined, adding to pool
2013-02-27 16:52:33,300 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-02-27 16:52:33,306 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2013-02-27 16:52:33,306 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-02-27 16:52:33,342 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-02-27 16:52:33,342 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-02-27 16:52:33,362 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2013-02-27 16:52:33,366 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2013-02-27 16:52:33,368 DEBUG: nvidia.available: falling back to default
2013-02-27 16:52:33,532 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-02-27 16:52:33,538 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2013-02-27 16:52:33,548 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2013-02-27 16:52:33,550 DEBUG: nvidia.available: falling back to default
2013-02-27 16:52:33,744 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-02-27 16:52:33,747 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-02-27 16:52:33,752 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2013-02-27 16:52:33,753 DEBUG: nvidia.available: falling back to default
2013-02-27 16:52:33,934 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-02-27 16:52:33,943 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2013-02-27 16:52:33,955 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2013-02-27 16:52:33,957 DEBUG: nvidia.available: falling back to default
2013-02-27 16:52:33,993 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI(s) xorg-video-abi-10 not compatible with X.org video ABI xorg-video-abi-11
2013-02-27 16:52:33,993 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-02-27 16:52:34,002 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2013-02-27 16:52:34,013 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2013-02-27 16:52:34,014 DEBUG: nvidia.available: falling back to default
2013-02-27 16:52:34,198 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-02-27 16:52:34,201 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2013-02-27 16:52:34,206 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2013-02-27 16:52:34,207 DEBUG: nvidia.available: falling back to default
2013-02-27 16:52:34,361 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-02-27 16:52:34,367 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310

2013-02-27 16:52:34,414 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental310 from name NvidiaDriverExperimental310
2013-02-27 16:52:34,416 DEBUG: nvidia.available: falling back to default
2013-02-27 16:52:34,583 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-02-27 16:52:34,587 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-02-27 16:52:34,615 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
2013-02-27 16:52:34,617 DEBUG: nvidia.available: falling back to default
2013-02-27 16:52:34,784 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-02-27 16:52:34,784 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-02-27 16:52:34,804 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-02-27 16:52:34,836 DEBUG: Software modem not available
2013-02-27 16:52:34,836 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-02-27 16:52:34,878 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-02-27 16:52:34,879 DEBUG: Firmware for DVB cards not available
2013-02-27 16:52:34,879 DEBUG: all custom handlers loaded
2013-02-27 16:52:34,879 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-02-27 16:52:34,879 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2013-02-27 16:52:34,884 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-27 16:52:34,979 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:34,980 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-27 16:52:34,980 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:34,980 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'acpi:PNP0100:')
2013-02-27 16:52:34,980 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'acpi:PNP0303:')
2013-02-27 16:52:34,980 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'pci:v00008086d00002834sv00001028sd00000209bc0Csc03i00')
2013-02-27 16:52:35,241 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'platform:dcdbas')
2013-02-27 16:52:35,241 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2013-02-27 16:52:35,270 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2013-02-27 16:52:35,270 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-27 16:52:35,270 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:35,270 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-27 16:52:35,270 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:35,270 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'usb:v05A9p7670d0100dcEFdsc02dp01ic0Eisc01ip00')
2013-02-27 16:52:35,274 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2013-02-27 16:52:35,274 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:35,274 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'usb:v0483p2016d0001dc00dsc00dp00icFFisc00ip00')
2013-02-27 16:52:35,281 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-02-27 16:52:35,281 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'platform:dell-laptop')
2013-02-27 16:52:35,281 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-02-27 16:52:35,282 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2013-02-27 16:52:35,282 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi'}
2013-02-27 16:52:35,282 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:35,282 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001028sd00000209bc06sc00i00')
2013-02-27 16:52:35,285 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'pci:v000014E4d00001713sv00001028sd00000209bc02sc00i00')
2013-02-27 16:52:35,323 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'tg3'}
2013-02-27 16:52:35,323 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'tg3', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:35,323 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-02-27 16:52:35,323 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'acpi:PNP0800:')
2013-02-27 16:52:35,323 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'pci:v00008086d00002829sv00001028sd00000209bc01sc06i01')
2013-02-27 16:52:35,326 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'acpi:PNP0F13:')
2013-02-27 16:52:35,326 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'pci:v000010DEd00000427sv00001028sd00000209bc03sc00i00')
2013-02-27 16:52:35,579 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current', 'package': 'nvidia-current'}
2013-02-27 16:52:35,651 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:52:35,651 DEBUG: KMH enabled: False
2013-02-27 16:52:35,579 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-02-27 16:52:35,656 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2013-02-27 16:52:35,663 DEBUG: nvidia.available: falling back to default
2013-02-27 16:52:35,823 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:52:35,824 DEBUG: KMH enabled: False
2013-02-27 16:52:35,807 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-02-27 16:52:35,824 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_173_updates', 'package': 'nvidia-173-updates'}
2013-02-27 16:52:35,837 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:52:35,837 DEBUG: nvidia_173_updates is not the alternative in use
2013-02-27 16:52:35,824 DEBUG: found match in handler pool xorg:nvidia_173_updates([NvidiaDriver173Updates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-02-27 16:52:35,841 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2013-02-27 16:52:35,847 DEBUG: nvidia.available: falling back to default
2013-02-27 16:52:36,012 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:52:36,012 DEBUG: nvidia_173_updates is not the alternative in use
2013-02-27 16:52:35,998 DEBUG: got handler xorg:nvidia_173_updates([NvidiaDriver173Updates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-02-27 16:52:36,012 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_experimental_310', 'package': 'nvidia-experimental-310'}
2013-02-27 16:52:36,026 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:52:36,027 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-02-27 16:52:36,012 DEBUG: found match in handler pool xorg:nvidia_experimental_310([NvidiaDriverExperimental310, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-02-27 16:52:36,030 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310

2013-02-27 16:52:36,037 DEBUG: nvidia.available: falling back to default
2013-02-27 16:52:36,202 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:52:36,202 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-02-27 16:52:36,186 DEBUG: got handler xorg:nvidia_experimental_310([NvidiaDriverExperimental310, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-02-27 16:52:36,203 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_173', 'package': 'nvidia-173'}
2013-02-27 16:52:36,227 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:52:36,228 DEBUG: nvidia_173 is not the alternative in use
2013-02-27 16:52:36,203 DEBUG: found match in handler pool xorg:nvidia_173([NvidiaDriver173, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-02-27 16:52:36,236 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2013-02-27 16:52:36,249 DEBUG: nvidia.available: falling back to default
2013-02-27 16:52:36,437 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:52:36,437 DEBUG: nvidia_173 is not the alternative in use
2013-02-27 16:52:36,422 DEBUG: got handler xorg:nvidia_173([NvidiaDriver173, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-02-27 16:52:36,437 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package': 'nvidia-current-updates'}
2013-02-27 16:52:36,456 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:52:36,457 DEBUG: nvidia_current_updates is not the alternative in use
2013-02-27 16:52:36,437 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-02-27 16:52:36,463 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-02-27 16:52:36,477 DEBUG: nvidia.available: falling back to default
2013-02-27 16:52:36,648 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:52:36,648 DEBUG: nvidia_current_updates is not the alternative in use
2013-02-27 16:52:36,635 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-02-27 16:52:36,649 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_experimental_304', 'package': 'nvidia-experimental-304'}
2013-02-27 16:52:36,663 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:52:36,664 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-02-27 16:52:36,649 DEBUG: found match in handler pool xorg:nvidia_experimental_304([NvidiaDriverExperimental304, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-02-27 16:52:36,669 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-02-27 16:52:36,676 DEBUG: nvidia.available: falling back to default
2013-02-27 16:52:36,845 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:52:36,845 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-02-27 16:52:36,829 DEBUG: got handler xorg:nvidia_experimental_304([NvidiaDriverExperimental304, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-02-27 16:52:36,845 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2013-02-27 16:52:36,846 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,846 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2013-02-27 16:52:36,846 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,846 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001028sd00000209bc04sc03i00')
2013-02-27 16:52:36,851 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-02-27 16:52:36,851 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,851 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-02-27 16:52:36,851 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,852 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-02-27 16:52:36,852 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001028sd00000209bc0Csc05i00')
2013-02-27 16:52:36,856 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2013-02-27 16:52:36,856 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,856 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd00000209bc08sc05i01')
2013-02-27 16:52:36,861 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci'}
2013-02-27 16:52:36,861 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,861 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci'}
2013-02-27 16:52:36,861 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,862 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'pci:v00008086d00002836sv00001028sd00000209bc0Csc03i20')
2013-02-27 16:52:36,866 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'pci:v00008086d00002815sv00001028sd00000209bc06sc01i00')
2013-02-27 16:52:36,869 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2013-02-27 16:52:36,869 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,870 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'usb:v413Cp8126d0367dcE0dsc01dp01icFEisc01ip00')
2013-02-27 16:52:36,883 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2013-02-27 16:52:36,883 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,883 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2013-02-27 16:52:36,884 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'input:b0003v05A9p7670e0100-e0,1,kD4,ramlsfw')
2013-02-27 16:52:36,884 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-27 16:52:36,884 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,884 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-27 16:52:36,884 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,884 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'input:b0003v0A5Cp4503e0111-e0,1,2,4,k110,111,112,r0,1,am4,lsfw')
2013-02-27 16:52:36,884 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-27 16:52:36,884 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,884 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-27 16:52:36,884 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,885 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2013-02-27 16:52:36,885 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-27 16:52:36,885 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,885 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2013-02-27 16:52:36,885 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'pci:v00008086d00002832sv00001028sd00000209bc0Csc03i00')
2013-02-27 16:52:36,888 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2013-02-27 16:52:36,888 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-27 16:52:36,888 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,888 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-27 16:52:36,888 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,888 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA15:bd12/26/2008:svnDellInc.:pnXPSM1330:pvr:rvnDellInc.:rn:rvr:cvnDellInc.:ct8:cvr:')
2013-02-27 16:52:36,903 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop'}
2013-02-27 16:52:36,903 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,903 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd00000209bc08sc80i00')
2013-02-27 16:52:36,903 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r592'}
2013-02-27 16:52:36,903 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r592', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,903 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'acpi:PNP0200:')
2013-02-27 16:52:36,903 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'pci:v00008086d00002448sv00001028sd00000209bc06sc04i01')
2013-02-27 16:52:36,906 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-02-27 16:52:36,906 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-27 16:52:36,906 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,907 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-27 16:52:36,907 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,907 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'usb:v0A5Cp4503d0100dc00dsc00dp00ic03isc01ip02')
2013-02-27 16:52:36,908 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-27 16:52:36,909 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,909 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2013-02-27 16:52:36,909 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,909 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2013-02-27 16:52:36,909 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'usb:v413Cp8126d0367dcE0dsc01dp01icE0isc01ip01')
2013-02-27 16:52:36,909 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2013-02-27 16:52:36,910 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,910 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'pci:v00008086d00002850sv00001028sd00000209bc01sc01i8a')
2013-02-27 16:52:36,912 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'pci:v00008086d00002835sv00001028sd00000209bc0Csc03i00')
2013-02-27 16:52:36,915 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd00000209bc08sc80i00')
2013-02-27 16:52:36,915 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r852'}
2013-02-27 16:52:36,916 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r852', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,916 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'input:b0003v0A5Cp4502e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2013-02-27 16:52:36,916 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-27 16:52:36,916 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,916 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-27 16:52:36,916 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,916 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'acpi:PNP0C32:')
2013-02-27 16:52:36,916 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2013-02-27 16:52:36,916 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'usb:v05A9p7670d0100dcEFdsc02dp01ic0Eisc02ip00')
2013-02-27 16:52:36,917 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2013-02-27 16:52:36,917 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'usb:v0A5Cp4502d0100dc00dsc00dp00ic03isc01ip01')
2013-02-27 16:52:36,917 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-27 16:52:36,917 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,917 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-02-27 16:52:36,917 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,917 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,ra0,1,18,1C,mlsfw')
2013-02-27 16:52:36,918 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-27 16:52:36,918 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,918 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-02-27 16:52:36,918 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,918 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-02-27 16:52:36,918 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,918 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-27 16:52:36,918 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,918 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-02-27 16:52:36,918 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'usb:v413Cp8126d0367dcE0dsc01dp01icFFiscFFipFF')
2013-02-27 16:52:36,919 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2013-02-27 16:52:36,919 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,919 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2013-02-27 16:52:36,919 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'platform:pcspkr')
2013-02-27 16:52:36,920 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-02-27 16:52:36,920 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,920 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-02-27 16:52:36,920 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,920 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd00000209bc0Csc00i10')
2013-02-27 16:52:36,920 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2013-02-27 16:52:36,920 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,920 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001028sd00000209bc0Csc03i20')
2013-02-27 16:52:36,923 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'pci:v00008086d00002831sv00001028sd00000209bc0Csc03i00')
2013-02-27 16:52:36,926 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-02-27 16:52:36,933 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-02-27 16:52:36,934 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,934 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-02-27 16:52:36,934 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,934 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,A1,E0,E1,E3,EC,EE,F0,ram4,lsfw')
2013-02-27 16:52:36,934 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-27 16:52:36,934 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,934 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-27 16:52:36,934 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 16:52:36,934 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'pci:v00008086d00002830sv00001028sd00000209bc0Csc03i00')
2013-02-27 16:52:36,937 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2013-02-27 16:52:36,937 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x26621b8> about HardwareID('modalias', 'acpi:PNP0000:')
2013-02-27 16:52:36,937 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-02-27 16:52:36,937 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2013-02-27 16:52:36,938 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'acpi:PNP0100:')
2013-02-27 16:52:36,938 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'acpi:PNP0303:')
2013-02-27 16:52:36,938 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'pci:v00008086d00002834sv00001028sd00000209bc0Csc03i00')
2013-02-27 16:52:36,938 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'platform:dcdbas')
2013-02-27 16:52:36,938 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2013-02-27 16:52:36,938 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2013-02-27 16:52:36,938 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'usb:v05A9p7670d0100dcEFdsc02dp01ic0Eisc01ip00')
2013-02-27 16:52:36,938 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'usb:v0483p2016d0001dc00dsc00dp00icFFisc00ip00')
2013-02-27 16:52:36,938 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-02-27 16:52:36,938 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'platform:dell-laptop')
2013-02-27 16:52:36,938 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-02-27 16:52:36,938 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2013-02-27 16:52:36,938 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001028sd00000209bc06sc00i00')
2013-02-27 16:52:36,939 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'pci:v000014E4d00001713sv00001028sd00000209bc02sc00i00')
2013-02-27 16:52:36,939 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-02-27 16:52:36,939 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'acpi:PNP0800:')
2013-02-27 16:52:36,939 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'pci:v00008086d00002829sv00001028sd00000209bc01sc06i01')
2013-02-27 16:52:36,939 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'acpi:PNP0F13:')
2013-02-27 16:52:36,939 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'pci:v000010DEd00000427sv00001028sd00000209bc03sc00i00')
2013-02-27 16:52:36,939 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001028sd00000209bc04sc03i00')
2013-02-27 16:52:36,939 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-02-27 16:52:36,939 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001028sd00000209bc0Csc05i00')
2013-02-27 16:52:36,939 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd00000209bc08sc05i01')
2013-02-27 16:52:36,939 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'pci:v00008086d00002836sv00001028sd00000209bc0Csc03i20')
2013-02-27 16:52:36,939 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'pci:v00008086d00002815sv00001028sd00000209bc06sc01i00')
2013-02-27 16:52:36,939 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'usb:v413Cp8126d0367dcE0dsc01dp01icFEisc01ip00')
2013-02-27 16:52:36,939 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2013-02-27 16:52:36,939 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'input:b0003v05A9p7670e0100-e0,1,kD4,ramlsfw')
2013-02-27 16:52:36,940 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'input:b0003v0A5Cp4503e0111-e0,1,2,4,k110,111,112,r0,1,am4,lsfw')
2013-02-27 16:52:36,940 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2013-02-27 16:52:36,940 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2013-02-27 16:52:36,940 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'pci:v00008086d00002832sv00001028sd00000209bc0Csc03i00')
2013-02-27 16:52:36,940 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2013-02-27 16:52:36,940 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA15:bd12/26/2008:svnDellInc.:pnXPSM1330:pvr:rvnDellInc.:rn:rvr:cvnDellInc.:ct8:cvr:')
2013-02-27 16:52:36,940 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd00000209bc08sc80i00')
2013-02-27 16:52:36,940 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'acpi:PNP0200:')
2013-02-27 16:52:36,940 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'pci:v00008086d00002448sv00001028sd00000209bc06sc04i01')
2013-02-27 16:52:36,940 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-02-27 16:52:36,940 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'usb:v0A5Cp4503d0100dc00dsc00dp00ic03isc01ip02')
2013-02-27 16:52:36,940 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2013-02-27 16:52:36,940 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'usb:v413Cp8126d0367dcE0dsc01dp01icE0isc01ip01')
2013-02-27 16:52:36,941 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'pci:v00008086d00002850sv00001028sd00000209bc01sc01i8a')
2013-02-27 16:52:36,941 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'pci:v00008086d00002835sv00001028sd00000209bc0Csc03i00')
2013-02-27 16:52:36,941 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd00000209bc08sc80i00')
2013-02-27 16:52:36,941 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'input:b0003v0A5Cp4502e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2013-02-27 16:52:36,941 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'acpi:PNP0C32:')
2013-02-27 16:52:36,941 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2013-02-27 16:52:36,941 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'usb:v05A9p7670d0100dcEFdsc02dp01ic0Eisc02ip00')
2013-02-27 16:52:36,941 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2013-02-27 16:52:36,941 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'usb:v0A5Cp4502d0100dc00dsc00dp00ic03isc01ip01')
2013-02-27 16:52:36,941 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,ra0,1,18,1C,mlsfw')
2013-02-27 16:52:36,941 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-02-27 16:52:36,941 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'usb:v413Cp8126d0367dcE0dsc01dp01icFFiscFFipFF')
2013-02-27 16:52:36,941 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2013-02-27 16:52:36,941 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'platform:pcspkr')
2013-02-27 16:52:36,942 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd00000209bc0Csc00i10')
2013-02-27 16:52:36,942 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001028sd00000209bc0Csc03i20')
2013-02-27 16:52:36,942 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'pci:v00008086d00002831sv00001028sd00000209bc0Csc03i00')
2013-02-27 16:52:36,942 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-02-27 16:52:36,942 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,A1,E0,E1,E3,EC,EE,F0,ram4,lsfw')
2013-02-27 16:52:36,942 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'pci:v00008086d00002830sv00001028sd00000209bc0Csc03i00')
2013-02-27 16:52:36,942 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2013-02-27 16:52:36,942 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2a0efc8> about HardwareID('modalias', 'acpi:PNP0000:')
2013-02-27 16:52:37,027 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:52:37,028 DEBUG: nvidia_173 is not the alternative in use
2013-02-27 16:52:38,887 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:52:38,887 DEBUG: nvidia_173_updates is not the alternative in use
2013-02-27 16:52:40,648 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:52:40,652 DEBUG: KMH enabled: False
2013-02-27 16:52:42,443 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:52:42,444 DEBUG: nvidia_current_updates is not the alternative in use
2013-02-27 16:52:44,309 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:52:44,309 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-02-27 16:52:46,280 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:52:46,280 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-02-27 16:52:48,092 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:52:48,093 DEBUG: nvidia_173 is not the alternative in use
2013-02-27 16:52:48,191 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:52:48,192 DEBUG: nvidia_173_updates is not the alternative in use
2013-02-27 16:52:48,289 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:52:48,290 DEBUG: KMH enabled: False
2013-02-27 16:52:48,385 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:52:48,385 DEBUG: nvidia_current_updates is not the alternative in use
2013-02-27 16:52:48,430 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:52:48,430 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-02-27 16:52:48,477 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:52:48,477 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-02-27 16:52:48,523 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:52:48,523 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-02-27 16:53:02,128 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:53:02,128 DEBUG: KMH enabled: False
2013-02-27 16:53:05,434 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:53:05,435 DEBUG: KMH enabled: False
2013-02-27 16:53:08,364 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2013-02-27 16:53:08,365 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2013-02-27 16:53:45,890 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:53:45,890 DEBUG: KMH enabled: False
2013-02-27 16:53:45,939 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:53:45,939 DEBUG: KMH enabled: False
2013-02-27 16:53:50,369 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:53:50,370 DEBUG: nvidia_173 is not the alternative in use
2013-02-27 16:53:50,437 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:53:50,437 DEBUG: nvidia_173_updates is not the alternative in use
2013-02-27 16:53:50,499 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:53:50,500 DEBUG: KMH enabled: False
2013-02-27 16:53:50,553 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:53:50,553 DEBUG: KMH enabled: False
2013-02-27 16:53:50,604 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:53:50,605 DEBUG: nvidia_current_updates is not the alternative in use
2013-02-27 16:53:50,658 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:53:50,659 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-02-27 16:53:50,700 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:53:50,701 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-02-27 16:53:50,764 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:53:50,764 DEBUG: nvidia_173 is not the alternative in use
2013-02-27 16:53:50,815 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:53:50,815 DEBUG: nvidia_173_updates is not the alternative in use
2013-02-27 16:53:50,861 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:53:50,861 DEBUG: KMH enabled: False
2013-02-27 16:53:50,918 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:53:50,919 DEBUG: KMH enabled: False
2013-02-27 16:53:51,016 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:53:51,017 DEBUG: nvidia_current_updates is not the alternative in use
2013-02-27 16:53:51,090 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:53:51,090 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-02-27 16:53:51,141 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:53:51,141 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-02-27 16:53:51,200 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:53:51,200 DEBUG: KMH enabled: False
2013-02-27 16:53:51,235 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:53:51,235 DEBUG: KMH enabled: False
2013-02-27 16:53:52,670 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:53:52,671 DEBUG: nvidia_173 is not the alternative in use
2013-02-27 16:53:55,682 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 16:53:55,682 DEBUG: nvidia_173 is not the alternative in use
2013-02-27 16:53:55,955 DEBUG: Installing package: nvidia-173
2013-02-27 16:53:58,636 DEBUG: download progress <Package: name:'nvidia-173' architecture='amd64' id:16913L> 0.000000
2013-02-27 16:53:58,637 DEBUG: download progress <Package: name:'nvidia-173' architecture='amd64' id:16913L> 0.000000
2013-02-27 16:53:58,709 DEBUG: download progress <Package: name:'nvidia-173' architecture='amd64' id:16913L> 0.000000
2013-02-27 16:53:58,770 DEBUG: download progress <Package: name:'nvidia-173' architecture='amd64' id:16913L> 0.000000
2013-02-27 16:53:58,845 DEBUG: download progress <Package: name:'nvidia-173' architecture='amd64' id:16913L> 0.014870
2013-02-27 16:53:59,347 DEBUG: download progress <Package: name:'nvidia-173' architecture='amd64' id:16913L> 2.082200
2013-02-27 16:53:59,848 DEBUG: download progress <Package: name:'nvidia-173' architecture='amd64' id:16913L> 5.249883
2013-02-27 16:54:00,350 DEBUG: download progress <Package: name:'nvidia-173' architecture='amd64' id:16913L> 9.542927
2013-02-27 16:54:00,851 DEBUG: download progress <Package: name:'nvidia-173' architecture='amd64' id:16913L> 15.511509
2013-02-27 16:54:01,352 DEBUG: download progress <Package: name:'nvidia-173' architecture='amd64' id:16913L> 24.997886
2013-02-27 16:54:01,854 DEBUG: download progress <Package: name:'nvidia-173' architecture='amd64' id:16913L> 37.251817
2013-02-27 16:54:02,355 DEBUG: download progress <Package: name:'nvidia-173' architecture='amd64' id:16913L> 49.455733
2013-02-27 16:54:02,856 DEBUG: download progress <Package: name:'nvidia-173' architecture='amd64' id:16913L> 61.851152
2013-02-27 16:54:03,358 DEBUG: download progress <Package: name:'nvidia-173' architecture='amd64' id:16913L> 74.121980
2013-02-27 16:54:03,859 DEBUG: download progress <Package: name:'nvidia-173' architecture='amd64' id:16913L> 86.676008
2013-02-27 16:54:04,361 DEBUG: download progress <Package: name:'nvidia-173' architecture='amd64' id:16913L> 99.013300
2013-02-27 16:54:04,400 DEBUG: download progress <Package: name:'nvidia-173' architecture='amd64' id:16913L> 100.000000
2013-02-27 16:54:05,153 DEBUG: install progress dpkg-exec 0.000000
2013-02-27 16:54:10,161 DEBUG: install progress nvidia-173 0.000000
2013-02-27 16:54:10,261 DEBUG: install progress nvidia-173 20.000000
2013-02-27 16:54:16,871 DEBUG: install progress nvidia-173 40.000000
2013-02-27 16:54:16,937 DEBUG: install progress nvidia-173 60.000000
2013-02-27 16:54:16,999 DEBUG: install progress man-db 60.000000
2013-02-27 16:54:18,806 DEBUG: install progress dpkg-exec 60.000000
2013-02-27 16:54:18,864 DEBUG: install progress nvidia-173 60.000000
2013-02-27 16:54:18,948 DEBUG: install progress nvidia-173 80.000000
2013-02-27 16:54:20,130 DEBUG: install progress nvidia-173 100.000000
2013-02-27 16:54:21,936 DEBUG: Selecting previously unselected package nvidia-173.
(Reading database ... 184653 files and directories currently installed.)
Unpacking nvidia-173 (from .../nvidia-173_173.14.35-0ubuntu0.2_amd64.deb) ...
Processing triggers for man-db ...
Setting up nvidia-173 (173.14.35-0ubuntu0.2) ...
Loading new nvidia-173-173.14.35 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-34-generic
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.

2013-02-27 16:54:22,184 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2013-02-27 16:54:22,185 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2013-02-27 16:54:57,903 DEBUG: NVidia(nvidia_173).enabled(): target_alt /usr/lib/nvidia-173/ld.so.conf current_alt /usr/lib/nvidia-173/ld.so.conf other target alt /usr/lib/nvidia-173/alt_ld.so.conf other current alt /usr/lib/nvidia-173/alt_ld.so.conf
2013-02-27 16:54:57,904 DEBUG: KMH enabled: False
2013-02-27 16:54:57,960 DEBUG: NVidia(nvidia_173).enabled(): target_alt /usr/lib/nvidia-173/ld.so.conf current_alt /usr/lib/nvidia-173/ld.so.conf other target alt /usr/lib/nvidia-173/alt_ld.so.conf other current alt /usr/lib/nvidia-173/alt_ld.so.conf
2013-02-27 16:54:57,960 DEBUG: KMH enabled: False
2013-02-27 16:56:14,786 DEBUG: NVidia(nvidia_173).enabled(): target_alt /usr/lib/nvidia-173/ld.so.conf current_alt /usr/lib/nvidia-173/ld.so.conf other target alt /usr/lib/nvidia-173/alt_ld.so.conf other current alt /usr/lib/nvidia-173/alt_ld.so.conf
2013-02-27 16:56:14,786 DEBUG: KMH enabled: False
2013-02-27 16:56:14,843 DEBUG: NVidia(nvidia_173).enabled(): target_alt /usr/lib/nvidia-173/ld.so.conf current_alt /usr/lib/nvidia-173/ld.so.conf other target alt /usr/lib/nvidia-173/alt_ld.so.conf other current alt /usr/lib/nvidia-173/alt_ld.so.conf
2013-02-27 16:56:14,843 DEBUG: KMH enabled: False
2013-02-27 16:56:14,911 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-173/ld.so.conf other target alt None other current alt /usr/lib/nvidia-173/alt_ld.so.conf
2013-02-27 16:56:14,911 DEBUG: nvidia_173_updates is not the alternative in use
2013-02-27 16:56:14,976 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-173/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-173/alt_ld.so.conf
2013-02-27 16:56:14,977 DEBUG: nvidia_current is not the alternative in use
2013-02-27 16:56:15,016 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-173/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-173/alt_ld.so.conf
2013-02-27 16:56:15,017 DEBUG: nvidia_current is not the alternative in use
2013-02-27 16:56:15,070 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-173/ld.so.conf other target alt None other current alt /usr/lib/nvidia-173/alt_ld.so.conf
2013-02-27 16:56:15,070 DEBUG: nvidia_current_updates is not the alternative in use
2013-02-27 16:56:15,124 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt None current_alt /usr/lib/nvidia-173/ld.so.conf other target alt None other current alt /usr/lib/nvidia-173/alt_ld.so.conf
2013-02-27 16:56:15,124 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-02-27 16:56:15,182 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt None current_alt /usr/lib/nvidia-173/ld.so.conf other target alt None other current alt /usr/lib/nvidia-173/alt_ld.so.conf
2013-02-27 16:56:15,182 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-02-27 16:56:15,263 DEBUG: NVidia(nvidia_173).enabled(): target_alt /usr/lib/nvidia-173/ld.so.conf current_alt /usr/lib/nvidia-173/ld.so.conf other target alt /usr/lib/nvidia-173/alt_ld.so.conf other current alt /usr/lib/nvidia-173/alt_ld.so.conf
2013-02-27 16:56:15,264 DEBUG: KMH enabled: False
2013-02-27 16:56:15,351 DEBUG: NVidia(nvidia_173).enabled(): target_alt /usr/lib/nvidia-173/ld.so.conf current_alt /usr/lib/nvidia-173/ld.so.conf other target alt /usr/lib/nvidia-173/alt_ld.so.conf other current alt /usr/lib/nvidia-173/alt_ld.so.conf
2013-02-27 16:56:15,352 DEBUG: KMH enabled: False
2013-02-27 16:56:15,451 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-173/ld.so.conf other target alt None other current alt /usr/lib/nvidia-173/alt_ld.so.conf
2013-02-27 16:56:15,451 DEBUG: nvidia_173_updates is not the alternative in use
2013-02-27 16:56:15,499 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-173/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-173/alt_ld.so.conf
2013-02-27 16:56:15,499 DEBUG: nvidia_current is not the alternative in use
2013-02-27 16:56:15,548 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-173/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-173/alt_ld.so.conf
2013-02-27 16:56:15,548 DEBUG: nvidia_current is not the alternative in use
2013-02-27 16:56:15,596 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-173/ld.so.conf other target alt None other current alt /usr/lib/nvidia-173/alt_ld.so.conf
2013-02-27 16:56:15,596 DEBUG: nvidia_current_updates is not the alternative in use
2013-02-27 16:56:15,644 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt None current_alt /usr/lib/nvidia-173/ld.so.conf other target alt None other current alt /usr/lib/nvidia-173/alt_ld.so.conf
2013-02-27 16:56:15,644 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-02-27 16:56:15,692 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt None current_alt /usr/lib/nvidia-173/ld.so.conf other target alt None other current alt /usr/lib/nvidia-173/alt_ld.so.conf
2013-02-27 16:56:15,693 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-02-27 16:56:15,742 DEBUG: NVidia(nvidia_173).enabled(): target_alt /usr/lib/nvidia-173/ld.so.conf current_alt /usr/lib/nvidia-173/ld.so.conf other target alt /usr/lib/nvidia-173/alt_ld.so.conf other current alt /usr/lib/nvidia-173/alt_ld.so.conf
2013-02-27 16:56:15,742 DEBUG: KMH enabled: False
2013-02-27 16:56:15,781 DEBUG: NVidia(nvidia_173).enabled(): target_alt /usr/lib/nvidia-173/ld.so.conf current_alt /usr/lib/nvidia-173/ld.so.conf other target alt /usr/lib/nvidia-173/alt_ld.so.conf other current alt /usr/lib/nvidia-173/alt_ld.so.conf
2013-02-27 16:56:15,781 DEBUG: KMH enabled: False
2013-02-27 16:56:18,290 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-173/ld.so.conf other target alt None other current alt /usr/lib/nvidia-173/alt_ld.so.conf
2013-02-27 16:56:18,290 DEBUG: nvidia_current_updates is not the alternative in use
2013-02-27 16:56:20,591 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-173/ld.so.conf other target alt None other current alt /usr/lib/nvidia-173/alt_ld.so.conf
2013-02-27 16:56:20,592 DEBUG: nvidia_current_updates is not the alternative in use
2013-02-27 16:56:23,742 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-173/ld.so.conf other target alt None other current alt /usr/lib/nvidia-173/alt_ld.so.conf
2013-02-27 16:56:23,742 DEBUG: nvidia_current_updates is not the alternative in use
2013-02-27 16:56:24,017 DEBUG: Installing package: nvidia-current-updates
2013-02-27 16:56:26,284 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 0.000000
2013-02-27 16:56:26,284 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 0.000000
2013-02-27 16:56:26,287 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 0.000000
2013-02-27 16:56:26,334 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 0.000000
2013-02-27 16:56:26,408 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 0.005769
2013-02-27 16:56:26,910 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 0.610838
2013-02-27 16:56:27,411 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 1.593040
2013-02-27 16:56:27,913 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 3.089136
2013-02-27 16:56:28,414 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 4.985159
2013-02-27 16:56:28,916 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 7.919331
2013-02-27 16:56:29,417 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 10.963328
2013-02-27 16:56:29,918 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 14.007325
2013-02-27 16:56:30,419 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 16.599511
2013-02-27 16:56:30,921 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 20.039370
2013-02-27 16:56:31,422 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 23.050212
2013-02-27 16:56:31,923 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 25.967808
2013-02-27 16:56:32,425 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 28.957928
2013-02-27 16:56:32,926 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 31.906606
2013-02-27 16:56:33,427 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 34.865644
2013-02-27 16:56:33,929 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 37.675487
2013-02-27 16:56:34,430 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 40.549567
2013-02-27 16:56:34,931 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 43.307607
2013-02-27 16:56:35,432 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 46.156821
2013-02-27 16:56:35,934 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 48.995674
2013-02-27 16:56:36,435 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 51.855249
2013-02-27 16:56:36,937 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 54.636082
2013-02-27 16:56:37,438 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 57.514306
2013-02-27 16:56:37,939 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 60.336582
2013-02-27 16:56:38,441 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 63.192013
2013-02-27 16:56:38,942 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 66.070237
2013-02-27 16:56:39,443 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 68.917379
2013-02-27 16:56:39,944 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 71.772810
2013-02-27 16:56:40,446 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 74.597158
2013-02-27 16:56:40,947 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 77.438084
2013-02-27 16:56:41,448 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 80.285226
2013-02-27 16:56:41,949 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 83.142728
2013-02-27 16:56:42,451 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 86.006448
2013-02-27 16:56:42,952 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 88.876383
2013-02-27 16:56:43,454 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 91.671721
2013-02-27 16:56:43,955 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 94.415256
2013-02-27 16:56:44,394 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 96.965762
2013-02-27 16:56:44,395 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 96.971854
2013-02-27 16:56:44,896 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 99.745473
2013-02-27 16:56:44,937 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16928L> 100.000000
2013-02-27 16:56:45,186 DEBUG: install progress dpkg-exec 0.000000
2013-02-27 16:56:45,751 DEBUG: install progress nvidia-current-updates 0.000000
2013-02-27 16:56:45,852 DEBUG: install progress nvidia-current-updates 10.000000
2013-02-27 16:56:54,108 DEBUG: install progress nvidia-current-updates 20.000000
2013-02-27 16:56:54,163 DEBUG: install progress nvidia-current-updates 30.000000
2013-02-27 16:56:54,435 DEBUG: install progress nvidia-settings-updates 30.000000
2013-02-27 16:56:54,535 DEBUG: install progress nvidia-settings-updates 40.000000
2013-02-27 16:56:54,867 DEBUG: install progress nvidia-settings-updates 50.000000
2013-02-27 16:56:54,922 DEBUG: install progress nvidia-settings-updates 60.000000
2013-02-27 16:56:54,979 DEBUG: install progress man-db 60.000000
2013-02-27 16:56:55,905 DEBUG: install progress dpkg-exec 60.000000
2013-02-27 16:56:55,966 DEBUG: install progress nvidia-current-updates 60.000000
2013-02-27 16:56:56,078 DEBUG: install progress nvidia-current-updates 70.000000
2013-02-27 16:56:56,735 DEBUG: install progress nvidia-current-updates 80.000000
2013-02-27 16:56:56,827 DEBUG: install progress nvidia-settings-updates 80.000000
2013-02-27 16:56:56,877 DEBUG: install progress nvidia-settings-updates 90.000000
2013-02-27 16:56:57,122 DEBUG: install progress nvidia-settings-updates 100.000000
2013-02-27 16:56:58,929 DEBUG: Selecting previously unselected package nvidia-current-updates.
(Reading database ... 184749 files and directories currently installed.)
Unpacking nvidia-current-updates (from .../nvidia-current-updates_304.64-0ubuntu0.2_amd64.deb) ...
Selecting previously unselected package nvidia-settings-updates.
Unpacking nvidia-settings-updates (from .../nvidia-settings-updates_304.43-0ubuntu0.2_amd64.deb) ...
Processing triggers for man-db ...
Setting up nvidia-current-updates (304.64-0ubuntu0.2) ...
INFO:Enable nvidia-current-updates
DEBUG:Parsing /usr/share/nvidia-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/nvidia-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/nvidia-common/quirks/put_your_quirks_here
DEBUG:Processing quirk ThinkPad T420s
DEBUG:Failure to match Dell Inc. with LENOVO
DEBUG:Quirk doesn't match
DEBUG:Processing quirk Latitude E6530
DEBUG:Failure to match XPS M1330 with Latitude E6530
DEBUG:Quirk doesn't match
Loading new nvidia-current-updates-304.64 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-34-generic
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
Setting up nvidia-settings-updates (304.43-0ubuntu0.2) ...
update-alternatives: using /usr/lib/nvidia-settings-updates/ld.so.conf to provide /etc/ld.so.conf.d/nvidia_settings.conf (nvidia_settings_conf) in auto mode.

2013-02-27 16:56:59,172 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-02-27 16:56:59,172 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2013-02-27 16:57:32,352 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 16:57:32,353 DEBUG: KMH enabled: False
2013-02-27 16:57:32,409 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 16:57:32,410 DEBUG: KMH enabled: False
2013-02-27 16:57:34,283 DEBUG: NVidia(nvidia_173).enabled(): target_alt /usr/lib/nvidia-173/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-173/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 16:57:34,283 DEBUG: nvidia_173 is not the alternative in use
2013-02-27 16:57:34,349 DEBUG: NVidia(nvidia_173).enabled(): target_alt /usr/lib/nvidia-173/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-173/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 16:57:34,349 DEBUG: nvidia_173 is not the alternative in use
2013-02-27 16:57:34,426 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 16:57:34,427 DEBUG: nvidia_173_updates is not the alternative in use
2013-02-27 16:57:34,493 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 16:57:34,493 DEBUG: nvidia_current is not the alternative in use
2013-02-27 16:57:34,580 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 16:57:34,580 DEBUG: nvidia_current is not the alternative in use
2013-02-27 16:57:34,648 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 16:57:34,648 DEBUG: KMH enabled: False
2013-02-27 16:57:34,698 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 16:57:34,698 DEBUG: KMH enabled: False
2013-02-27 16:57:34,750 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 16:57:34,750 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-02-27 16:57:34,807 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 16:57:34,808 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-02-27 16:57:34,907 DEBUG: NVidia(nvidia_173).enabled(): target_alt /usr/lib/nvidia-173/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-173/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 16:57:34,908 DEBUG: nvidia_173 is not the alternative in use
2013-02-27 16:57:34,952 DEBUG: NVidia(nvidia_173).enabled(): target_alt /usr/lib/nvidia-173/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-173/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 16:57:34,952 DEBUG: nvidia_173 is not the alternative in use
2013-02-27 16:57:35,012 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 16:57:35,012 DEBUG: nvidia_173_updates is not the alternative in use
2013-02-27 16:57:35,068 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 16:57:35,069 DEBUG: nvidia_current is not the alternative in use
2013-02-27 16:57:35,121 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 16:57:35,122 DEBUG: nvidia_current is not the alternative in use
2013-02-27 16:57:35,188 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 16:57:35,188 DEBUG: KMH enabled: False
2013-02-27 16:57:35,233 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 16:57:35,234 DEBUG: KMH enabled: False
2013-02-27 16:57:35,300 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 16:57:35,300 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-02-27 16:57:35,358 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 16:57:35,359 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-02-27 16:57:35,422 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 16:57:35,422 DEBUG: KMH enabled: False
2013-02-27 16:57:35,471 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 16:57:35,471 DEBUG: KMH enabled: False
2013-02-27 17:01:13,042 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8>
2013-02-27 17:01:15,983 DEBUG: reading modalias file /lib/modules/3.2.0-34-generic/modules.alias
2013-02-27 17:01:16,099 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-02-27 17:01:16,112 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-02-27 17:01:16,173 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-02-27 17:01:16,239 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2013-02-27 17:01:16,244 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2013-02-27 17:01:16,244 DEBUG: fglrx.available: falling back to default
2013-02-27 17:01:16,549 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2013-02-27 17:01:16,554 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9

2013-02-27 17:01:16,573 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverExperimental9 from name FglrxDriverExperimental9
2013-02-27 17:01:16,574 DEBUG: fglrx.available: falling back to default
2013-02-27 17:01:16,710 DEBUG: ATI/AMD proprietary FGLRX graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-02-27 17:01:16,714 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-02-27 17:01:16,718 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2013-02-27 17:01:16,719 DEBUG: fglrx.available: falling back to default
2013-02-27 17:01:16,873 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2013-02-27 17:01:16,873 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-02-27 17:01:16,878 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-02-27 17:01:16,896 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-02-27 17:01:16,897 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-02-27 17:01:16,897 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-02-27 17:01:16,902 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2013-02-27 17:01:16,902 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-02-27 17:01:16,902 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-02-27 17:01:16,902 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-02-27 17:01:16,908 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2013-02-27 17:01:16,913 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-02-27 17:01:17,053 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-02-27 17:01:17,054 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2013-02-27 17:01:17,058 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx

2013-02-27 17:01:17,059 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2013-02-27 17:01:17,059 DEBUG: cdv.available: falling back to default
2013-02-27 17:01:17,204 DEBUG: Intel Cedarview graphics driver availability undetermined, adding to pool
2013-02-27 17:01:17,204 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-02-27 17:01:17,209 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2013-02-27 17:01:17,209 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-02-27 17:01:17,233 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-02-27 17:01:17,233 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-02-27 17:01:17,252 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2013-02-27 17:01:17,257 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2013-02-27 17:01:17,258 DEBUG: nvidia.available: falling back to default
2013-02-27 17:01:17,415 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-02-27 17:01:17,419 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2013-02-27 17:01:17,425 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2013-02-27 17:01:17,426 DEBUG: nvidia.available: falling back to default
2013-02-27 17:01:17,607 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-02-27 17:01:17,611 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-02-27 17:01:17,615 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2013-02-27 17:01:17,616 DEBUG: nvidia.available: falling back to default
2013-02-27 17:01:17,785 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-02-27 17:01:17,789 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2013-02-27 17:01:17,794 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2013-02-27 17:01:17,795 DEBUG: nvidia.available: falling back to default
2013-02-27 17:01:17,809 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI(s) xorg-video-abi-10 not compatible with X.org video ABI xorg-video-abi-11
2013-02-27 17:01:17,809 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-02-27 17:01:17,813 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2013-02-27 17:01:17,819 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2013-02-27 17:01:17,820 DEBUG: nvidia.available: falling back to default
2013-02-27 17:01:18,004 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-02-27 17:01:18,013 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2013-02-27 17:01:18,019 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2013-02-27 17:01:18,020 DEBUG: nvidia.available: falling back to default
2013-02-27 17:01:18,169 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-02-27 17:01:18,173 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310

2013-02-27 17:01:18,203 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental310 from name NvidiaDriverExperimental310
2013-02-27 17:01:18,205 DEBUG: nvidia.available: falling back to default
2013-02-27 17:01:18,372 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-02-27 17:01:18,375 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-02-27 17:01:18,399 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
2013-02-27 17:01:18,400 DEBUG: nvidia.available: falling back to default
2013-02-27 17:01:18,529 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-02-27 17:01:18,529 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-02-27 17:01:18,551 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-02-27 17:01:18,577 DEBUG: Software modem not available
2013-02-27 17:01:18,578 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-02-27 17:01:18,637 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-02-27 17:01:18,637 DEBUG: Firmware for DVB cards not available
2013-02-27 17:01:18,637 DEBUG: all custom handlers loaded
2013-02-27 17:01:18,637 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-02-27 17:01:18,637 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2013-02-27 17:01:18,643 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-27 17:01:18,738 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:18,738 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-27 17:01:18,739 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:18,739 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'acpi:PNP0100:')
2013-02-27 17:01:18,739 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'acpi:PNP0303:')
2013-02-27 17:01:18,739 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'pci:v00008086d00002834sv00001028sd00000209bc0Csc03i00')
2013-02-27 17:01:19,001 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'platform:dcdbas')
2013-02-27 17:01:19,001 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2013-02-27 17:01:19,015 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2013-02-27 17:01:19,015 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-27 17:01:19,015 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:19,015 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-27 17:01:19,015 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:19,015 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'usb:v05A9p7670d0100dcEFdsc02dp01ic0Eisc01ip00')
2013-02-27 17:01:19,019 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2013-02-27 17:01:19,019 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:19,019 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'usb:v0483p2016d0001dc00dsc00dp00icFFisc00ip00')
2013-02-27 17:01:19,026 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-02-27 17:01:19,026 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'platform:dell-laptop')
2013-02-27 17:01:19,026 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-02-27 17:01:19,027 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2013-02-27 17:01:19,027 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi'}
2013-02-27 17:01:19,027 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:19,027 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001028sd00000209bc06sc00i00')
2013-02-27 17:01:19,030 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'pci:v000014E4d00001713sv00001028sd00000209bc02sc00i00')
2013-02-27 17:01:19,068 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'tg3'}
2013-02-27 17:01:19,068 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'tg3', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:19,068 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-02-27 17:01:19,068 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'acpi:PNP0800:')
2013-02-27 17:01:19,068 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'pci:v00008086d00002829sv00001028sd00000209bc01sc06i01')
2013-02-27 17:01:19,071 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'acpi:PNP0F13:')
2013-02-27 17:01:19,071 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'pci:v000010DEd00000427sv00001028sd00000209bc03sc00i00')
2013-02-27 17:01:19,326 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current', 'package': 'nvidia-current'}
2013-02-27 17:01:19,407 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 17:01:19,407 DEBUG: nvidia_current is not the alternative in use
2013-02-27 17:01:19,327 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-02-27 17:01:19,412 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2013-02-27 17:01:19,419 DEBUG: nvidia.available: falling back to default
2013-02-27 17:01:19,578 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 17:01:19,578 DEBUG: nvidia_current is not the alternative in use
2013-02-27 17:01:19,562 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-02-27 17:01:19,579 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_173_updates', 'package': 'nvidia-173-updates'}
2013-02-27 17:01:19,605 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 17:01:19,605 DEBUG: nvidia_173_updates is not the alternative in use
2013-02-27 17:01:19,579 DEBUG: found match in handler pool xorg:nvidia_173_updates([NvidiaDriver173Updates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-02-27 17:01:19,614 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2013-02-27 17:01:19,626 DEBUG: nvidia.available: falling back to default
2013-02-27 17:01:19,819 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 17:01:19,819 DEBUG: nvidia_173_updates is not the alternative in use
2013-02-27 17:01:19,804 DEBUG: got handler xorg:nvidia_173_updates([NvidiaDriver173Updates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-02-27 17:01:19,819 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_experimental_310', 'package': 'nvidia-experimental-310'}
2013-02-27 17:01:19,834 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 17:01:19,834 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-02-27 17:01:19,819 DEBUG: found match in handler pool xorg:nvidia_experimental_310([NvidiaDriverExperimental310, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-02-27 17:01:19,839 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310

2013-02-27 17:01:19,847 DEBUG: nvidia.available: falling back to default
2013-02-27 17:01:20,022 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 17:01:20,022 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-02-27 17:01:20,005 DEBUG: got handler xorg:nvidia_experimental_310([NvidiaDriverExperimental310, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-02-27 17:01:20,022 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_173', 'package': 'nvidia-173'}
2013-02-27 17:01:20,050 DEBUG: NVidia(nvidia_173).enabled(): target_alt /usr/lib/nvidia-173/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-173/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 17:01:20,050 DEBUG: nvidia_173 is not the alternative in use
2013-02-27 17:01:20,023 DEBUG: found match in handler pool xorg:nvidia_173([NvidiaDriver173, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-02-27 17:01:20,059 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2013-02-27 17:01:20,071 DEBUG: nvidia.available: falling back to default
2013-02-27 17:01:20,260 DEBUG: NVidia(nvidia_173).enabled(): target_alt /usr/lib/nvidia-173/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-173/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 17:01:20,260 DEBUG: nvidia_173 is not the alternative in use
2013-02-27 17:01:20,244 DEBUG: got handler xorg:nvidia_173([NvidiaDriver173, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-02-27 17:01:20,260 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package': 'nvidia-current-updates'}
2013-02-27 17:01:20,285 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 17:01:20,286 DEBUG: KMH enabled: False
2013-02-27 17:01:20,261 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-02-27 17:01:20,294 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-02-27 17:01:20,307 DEBUG: nvidia.available: falling back to default
2013-02-27 17:01:20,471 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 17:01:20,472 DEBUG: KMH enabled: False
2013-02-27 17:01:20,454 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-02-27 17:01:20,472 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_experimental_304', 'package': 'nvidia-experimental-304'}
2013-02-27 17:01:20,488 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 17:01:20,488 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-02-27 17:01:20,472 DEBUG: found match in handler pool xorg:nvidia_experimental_304([NvidiaDriverExperimental304, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-02-27 17:01:20,494 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-02-27 17:01:20,503 DEBUG: nvidia.available: falling back to default
2013-02-27 17:01:20,683 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 17:01:20,683 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-02-27 17:01:20,669 DEBUG: got handler xorg:nvidia_experimental_304([NvidiaDriverExperimental304, nonfree, disabled] NVIDIA accelerated graphics driver (**experimental** beta))
2013-02-27 17:01:20,684 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2013-02-27 17:01:20,684 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,684 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2013-02-27 17:01:20,684 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,684 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001028sd00000209bc04sc03i00')
2013-02-27 17:01:20,689 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-02-27 17:01:20,690 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,690 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-02-27 17:01:20,690 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,690 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-02-27 17:01:20,690 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001028sd00000209bc0Csc05i00')
2013-02-27 17:01:20,694 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2013-02-27 17:01:20,694 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,694 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd00000209bc08sc05i01')
2013-02-27 17:01:20,699 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci'}
2013-02-27 17:01:20,700 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,700 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci'}
2013-02-27 17:01:20,700 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,700 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'pci:v00008086d00002836sv00001028sd00000209bc0Csc03i20')
2013-02-27 17:01:20,704 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'pci:v00008086d00002815sv00001028sd00000209bc06sc01i00')
2013-02-27 17:01:20,708 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2013-02-27 17:01:20,708 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,708 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'usb:v413Cp8126d0367dcE0dsc01dp01icFEisc01ip00')
2013-02-27 17:01:20,722 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2013-02-27 17:01:20,722 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,722 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2013-02-27 17:01:20,722 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'input:b0003v05A9p7670e0100-e0,1,kD4,ramlsfw')
2013-02-27 17:01:20,722 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-27 17:01:20,722 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,723 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-27 17:01:20,723 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,723 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'input:b0003v0A5Cp4503e0111-e0,1,2,4,k110,111,112,r0,1,am4,lsfw')
2013-02-27 17:01:20,723 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-27 17:01:20,723 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,723 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-27 17:01:20,723 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,723 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2013-02-27 17:01:20,723 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-27 17:01:20,723 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,724 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2013-02-27 17:01:20,724 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'pci:v00008086d00002832sv00001028sd00000209bc0Csc03i00')
2013-02-27 17:01:20,726 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2013-02-27 17:01:20,727 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-27 17:01:20,727 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,727 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-27 17:01:20,727 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,727 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA15:bd12/26/2008:svnDellInc.:pnXPSM1330:pvr:rvnDellInc.:rn:rvr:cvnDellInc.:ct8:cvr:')
2013-02-27 17:01:20,742 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop'}
2013-02-27 17:01:20,742 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,742 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd00000209bc08sc80i00')
2013-02-27 17:01:20,742 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r592'}
2013-02-27 17:01:20,742 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r592', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,742 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'acpi:PNP0200:')
2013-02-27 17:01:20,742 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'pci:v00008086d00002448sv00001028sd00000209bc06sc04i01')
2013-02-27 17:01:20,745 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-02-27 17:01:20,745 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-27 17:01:20,745 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,746 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-27 17:01:20,746 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,746 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'usb:v0A5Cp4503d0100dc00dsc00dp00ic03isc01ip02')
2013-02-27 17:01:20,747 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-27 17:01:20,748 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,748 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2013-02-27 17:01:20,748 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,748 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2013-02-27 17:01:20,748 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'usb:v413Cp8126d0367dcE0dsc01dp01icE0isc01ip01')
2013-02-27 17:01:20,749 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2013-02-27 17:01:20,749 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,749 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'pci:v00008086d00002850sv00001028sd00000209bc01sc01i8a')
2013-02-27 17:01:20,752 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'pci:v00008086d00002835sv00001028sd00000209bc0Csc03i00')
2013-02-27 17:01:20,754 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd00000209bc08sc80i00')
2013-02-27 17:01:20,755 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r852'}
2013-02-27 17:01:20,755 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r852', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,755 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'input:b0003v0A5Cp4502e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2013-02-27 17:01:20,755 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-27 17:01:20,755 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,755 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-27 17:01:20,755 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,755 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'acpi:PNP0C32:')
2013-02-27 17:01:20,755 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2013-02-27 17:01:20,756 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'usb:v05A9p7670d0100dcEFdsc02dp01ic0Eisc02ip00')
2013-02-27 17:01:20,756 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2013-02-27 17:01:20,756 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'usb:v0A5Cp4502d0100dc00dsc00dp00ic03isc01ip01')
2013-02-27 17:01:20,756 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-27 17:01:20,756 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,756 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-02-27 17:01:20,757 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,757 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,ra0,1,18,1C,mlsfw')
2013-02-27 17:01:20,757 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-27 17:01:20,757 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,757 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-02-27 17:01:20,757 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,757 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-02-27 17:01:20,757 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,757 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-27 17:01:20,757 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,758 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-02-27 17:01:20,758 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'usb:v413Cp8126d0367dcE0dsc01dp01icFFiscFFipFF')
2013-02-27 17:01:20,758 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2013-02-27 17:01:20,758 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,758 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2013-02-27 17:01:20,758 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'platform:pcspkr')
2013-02-27 17:01:20,759 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-02-27 17:01:20,759 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,759 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-02-27 17:01:20,759 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,759 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd00000209bc0Csc00i10')
2013-02-27 17:01:20,759 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2013-02-27 17:01:20,759 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,760 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001028sd00000209bc0Csc03i20')
2013-02-27 17:01:20,762 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'pci:v00008086d00002831sv00001028sd00000209bc0Csc03i00')
2013-02-27 17:01:20,765 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-02-27 17:01:20,773 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-02-27 17:01:20,773 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,773 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-02-27 17:01:20,773 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,773 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,A1,E0,E1,E3,EC,EE,F0,ram4,lsfw')
2013-02-27 17:01:20,773 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-27 17:01:20,773 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,774 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-27 17:01:20,774 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-27 17:01:20,774 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'pci:v00008086d00002830sv00001028sd00000209bc0Csc03i00')
2013-02-27 17:01:20,777 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2013-02-27 17:01:20,777 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16791b8> about HardwareID('modalias', 'acpi:PNP0000:')
2013-02-27 17:01:20,777 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-02-27 17:01:20,777 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2013-02-27 17:01:20,777 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'acpi:PNP0100:')
2013-02-27 17:01:20,777 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'acpi:PNP0303:')
2013-02-27 17:01:20,777 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'pci:v00008086d00002834sv00001028sd00000209bc0Csc03i00')
2013-02-27 17:01:20,777 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'platform:dcdbas')
2013-02-27 17:01:20,777 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2013-02-27 17:01:20,777 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2013-02-27 17:01:20,777 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'usb:v05A9p7670d0100dcEFdsc02dp01ic0Eisc01ip00')
2013-02-27 17:01:20,778 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'usb:v0483p2016d0001dc00dsc00dp00icFFisc00ip00')
2013-02-27 17:01:20,778 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-02-27 17:01:20,778 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'platform:dell-laptop')
2013-02-27 17:01:20,778 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-02-27 17:01:20,778 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2013-02-27 17:01:20,778 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001028sd00000209bc06sc00i00')
2013-02-27 17:01:20,778 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'pci:v000014E4d00001713sv00001028sd00000209bc02sc00i00')
2013-02-27 17:01:20,778 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-02-27 17:01:20,778 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'acpi:PNP0800:')
2013-02-27 17:01:20,778 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'pci:v00008086d00002829sv00001028sd00000209bc01sc06i01')
2013-02-27 17:01:20,778 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'acpi:PNP0F13:')
2013-02-27 17:01:20,778 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'pci:v000010DEd00000427sv00001028sd00000209bc03sc00i00')
2013-02-27 17:01:20,778 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001028sd00000209bc04sc03i00')
2013-02-27 17:01:20,779 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-02-27 17:01:20,779 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001028sd00000209bc0Csc05i00')
2013-02-27 17:01:20,779 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd00000209bc08sc05i01')
2013-02-27 17:01:20,779 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'pci:v00008086d00002836sv00001028sd00000209bc0Csc03i20')
2013-02-27 17:01:20,779 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'pci:v00008086d00002815sv00001028sd00000209bc06sc01i00')
2013-02-27 17:01:20,779 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'usb:v413Cp8126d0367dcE0dsc01dp01icFEisc01ip00')
2013-02-27 17:01:20,779 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2013-02-27 17:01:20,779 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'input:b0003v05A9p7670e0100-e0,1,kD4,ramlsfw')
2013-02-27 17:01:20,779 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'input:b0003v0A5Cp4503e0111-e0,1,2,4,k110,111,112,r0,1,am4,lsfw')
2013-02-27 17:01:20,779 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2013-02-27 17:01:20,779 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2013-02-27 17:01:20,779 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'pci:v00008086d00002832sv00001028sd00000209bc0Csc03i00')
2013-02-27 17:01:20,779 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2013-02-27 17:01:20,779 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA15:bd12/26/2008:svnDellInc.:pnXPSM1330:pvr:rvnDellInc.:rn:rvr:cvnDellInc.:ct8:cvr:')
2013-02-27 17:01:20,780 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd00000209bc08sc80i00')
2013-02-27 17:01:20,780 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'acpi:PNP0200:')
2013-02-27 17:01:20,780 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'pci:v00008086d00002448sv00001028sd00000209bc06sc04i01')
2013-02-27 17:01:20,780 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-02-27 17:01:20,780 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'usb:v0A5Cp4503d0100dc00dsc00dp00ic03isc01ip02')
2013-02-27 17:01:20,780 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2013-02-27 17:01:20,780 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'usb:v413Cp8126d0367dcE0dsc01dp01icE0isc01ip01')
2013-02-27 17:01:20,780 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'pci:v00008086d00002850sv00001028sd00000209bc01sc01i8a')
2013-02-27 17:01:20,780 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'pci:v00008086d00002835sv00001028sd00000209bc0Csc03i00')
2013-02-27 17:01:20,780 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd00000209bc08sc80i00')
2013-02-27 17:01:20,780 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'input:b0003v0A5Cp4502e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2013-02-27 17:01:20,780 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'acpi:PNP0C32:')
2013-02-27 17:01:20,780 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2013-02-27 17:01:20,780 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'usb:v05A9p7670d0100dcEFdsc02dp01ic0Eisc02ip00')
2013-02-27 17:01:20,781 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2013-02-27 17:01:20,781 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'usb:v0A5Cp4502d0100dc00dsc00dp00ic03isc01ip01')
2013-02-27 17:01:20,781 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,ra0,1,18,1C,mlsfw')
2013-02-27 17:01:20,781 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-02-27 17:01:20,781 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'usb:v413Cp8126d0367dcE0dsc01dp01icFFiscFFipFF')
2013-02-27 17:01:20,781 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2013-02-27 17:01:20,781 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'platform:pcspkr')
2013-02-27 17:01:20,781 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd00000209bc0Csc00i10')
2013-02-27 17:01:20,781 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001028sd00000209bc0Csc03i20')
2013-02-27 17:01:20,781 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'pci:v00008086d00002831sv00001028sd00000209bc0Csc03i00')
2013-02-27 17:01:20,781 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-02-27 17:01:20,781 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,A1,E0,E1,E3,EC,EE,F0,ram4,lsfw')
2013-02-27 17:01:20,782 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'pci:v00008086d00002830sv00001028sd00000209bc0Csc03i00')
2013-02-27 17:01:20,782 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2013-02-27 17:01:20,782 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1a25fc8> about HardwareID('modalias', 'acpi:PNP0000:')
2013-02-27 17:01:20,822 DEBUG: NVidia(nvidia_173).enabled(): target_alt /usr/lib/nvidia-173/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-173/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 17:01:20,822 DEBUG: nvidia_173 is not the alternative in use
2013-02-27 17:01:22,629 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 17:01:22,629 DEBUG: nvidia_173_updates is not the alternative in use
2013-02-27 17:01:24,356 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 17:01:24,356 DEBUG: nvidia_current is not the alternative in use
2013-02-27 17:01:26,102 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 17:01:26,102 DEBUG: KMH enabled: False
2013-02-27 17:01:27,847 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 17:01:27,848 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-02-27 17:01:29,742 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 17:01:29,742 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-02-27 17:01:31,500 DEBUG: NVidia(nvidia_173).enabled(): target_alt /usr/lib/nvidia-173/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-173/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 17:01:31,500 DEBUG: nvidia_173 is not the alternative in use
2013-02-27 17:01:31,594 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 17:01:31,595 DEBUG: nvidia_173_updates is not the alternative in use
2013-02-27 17:01:31,690 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 17:01:31,690 DEBUG: nvidia_current is not the alternative in use
2013-02-27 17:01:31,785 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 17:01:31,785 DEBUG: KMH enabled: False
2013-02-27 17:01:31,879 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 17:01:31,880 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-02-27 17:01:31,974 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 17:01:31,974 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-02-27 17:01:32,072 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 17:01:32,073 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-02-27 17:01:36,596 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 17:01:36,597 DEBUG: nvidia_current is not the alternative in use
2013-02-27 17:01:37,111 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 17:01:37,112 DEBUG: nvidia_current is not the alternative in use
2013-02-27 17:01:38,905 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2013-02-27 17:01:38,905 DEBUG: nvidia_current is not the alternative in use
2013-02-27 17:01:42,721 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2013-02-27 17:01:42,722 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2013-02-27 17:02:22,546 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 17:02:22,546 DEBUG: KMH enabled: False
2013-02-27 17:02:22,597 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 17:02:22,597 DEBUG: KMH enabled: False
2013-02-27 17:02:48,154 DEBUG: NVidia(nvidia_173).enabled(): target_alt /usr/lib/nvidia-173/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-173/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 17:02:48,155 DEBUG: nvidia_173 is not the alternative in use
2013-02-27 17:02:48,223 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 17:02:48,223 DEBUG: nvidia_173_updates is not the alternative in use
2013-02-27 17:02:48,286 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 17:02:48,287 DEBUG: KMH enabled: False
2013-02-27 17:02:48,339 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 17:02:48,339 DEBUG: KMH enabled: False
2013-02-27 17:02:48,394 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 17:02:48,394 DEBUG: nvidia_current_updates is not the alternative in use
2013-02-27 17:02:48,442 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 17:02:48,442 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-02-27 17:02:48,486 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 17:02:48,486 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-02-27 17:02:48,552 DEBUG: NVidia(nvidia_173).enabled(): target_alt /usr/lib/nvidia-173/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-173/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 17:02:48,552 DEBUG: nvidia_173 is not the alternative in use
2013-02-27 17:02:48,594 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 17:02:48,594 DEBUG: nvidia_173_updates is not the alternative in use
2013-02-27 17:02:48,646 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 17:02:48,646 DEBUG: KMH enabled: False
2013-02-27 17:02:48,684 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 17:02:48,684 DEBUG: KMH enabled: False
2013-02-27 17:02:48,728 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 17:02:48,728 DEBUG: nvidia_current_updates is not the alternative in use
2013-02-27 17:02:48,778 DEBUG: NVidia(nvidia_experimental_304).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 17:02:48,778 DEBUG: nvidia_experimental_304 is not the alternative in use
2013-02-27 17:02:48,828 DEBUG: NVidia(nvidia_experimental_310).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 17:02:48,828 DEBUG: nvidia_experimental_310 is not the alternative in use
2013-02-27 17:02:48,875 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 17:02:48,875 DEBUG: KMH enabled: False
2013-02-27 17:02:48,913 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2013-02-27 17:02:48,914 DEBUG: KMH enabled: False

```

---

### Post by dabl on 2013-02-27
No, dist-upgrade will not change your Kubuntu version.  To prove it to yourself, do this:

```
sudo apt-get -s dist-upgrade
```

to simulate it.  I wanted to be sure you have all available upgrades installed before messing further with your video system.

---

### Post by x C0MMAND0 x on 2013-02-27
dabl - you are awesome!  Thank you so much!

All I did was run **sudo apt-get update && sudo apt-get dist-upgrade**, reboot and voila!  The issue was fixed.

I did not know what apt-get dist-upgrade, and had an incorrect assumption.  Thank you for teaching me something new.

Also, FYI my lspci -vk shows the following for my graphics card now, where previously it had nouveau listed as the main one.

```
kernel modules: nvidia_current_updates, nvidia_173, nvidia_current, nouveau, nvidiafb
```

Thank you so much again!  :D

---

### Post by dabl on 2013-02-27
Yay!

Please edit your original post and put a "[SOLVED]" at the beginning of the title, in case it might help another who runs into the same problem.

Thanks!

---

### Post by udippel on 2013-03-01
I guess someone was more lucky than me ... :(

I experienced exactly the same thing after the daily sudo apt-get update && sudo apt-get dist-upgrade, that usually keeps things afloat. In this case, this time, not a chance.
Trouble is, there is no GLX, no acceleration. The card is plugged:
$ dmesg | grep adeon
[    0.995260] [drm] radeon defaulting to kernel modesetting.
[    0.995263] [drm] radeon kernel modesetting enabled.
[    1.003597] radeon 0000:01:00.0: VRAM: 512M 0x0000000000000000 - 0x000000001FFFFFFF (512M used)
[    1.003600] radeon 0000:01:00.0: GTT: 512M 0x0000000020000000 - 0x000000003FFFFFFF
[    1.006485] [drm] radeon: 512M of VRAM memory ready
[    1.006487] [drm] radeon: 512M of GTT memory ready.
[    1.006559] radeon 0000:01:00.0: irq 48 for MSI/MSI-X
[    1.006571] radeon 0000:01:00.0: radeon: using MSI.
[    1.006601] [drm] radeon: irq initialized.
[    1.044509] radeon 0000:01:00.0: WB enabled
[    1.044511] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000020000c00 and cpu addr 0xffc74c00
[    1.060961] [drm] Radeon Display Connectors
[    1.061033] [drm] radeon: power management initialized
[    1.122478] fbcon: radeondrmfb (fb0) is primary device
[    1.122558] fb0: radeondrmfb frame buffer device
[    1.122563] [drm] Initialized radeon 2.18.0 20080528 for 0000:01:00.0 on minor 0

That's all.
Something must have been updated around yesterday (Feb.28 2013) that like to break NVIDIA-cards.?

Since this thread is 'SOLVED', should I better start a new one?

Uwe

---

### Post by udippel on 2013-03-02
Okay, sorted in my case.
Since February 28th, xorg was looking for GLX from Nvidia instead of ATI. I had an old and stale nvidia installation that never before came in the way of properly running the ATI-card.
After removal of the nvidia-packages, everything is back to normal.
(I consider it buggy, because an unused nvidia installation must not interfere with a detected ATI-card and its working drivers installed.)

---

