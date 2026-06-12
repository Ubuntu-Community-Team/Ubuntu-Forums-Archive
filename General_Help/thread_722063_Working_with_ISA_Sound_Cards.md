---
title: "Working with ISA Sound Cards"
date: 2008-03-12
forum: General Help
---

### Post by Conray on 2008-03-12
I have an old ISA Soundblaster 16 card that is not being recognized by Ubuntu 6.0. Does anyone have a simple fix for this issue. I'm new to Linux and would love to eliminate Windows from my PC's one day. Starting with this PC I'm working on first.

 My motherboard is an Asus P3B-F with two ISA slots. I've had this Sound Blaster card for several years in storage. it worked perfect under Windows 98. Now I have Ubuntu full force and it isn't seen by the OS.

Any ideas would be appreciated.

Thanks
:guitar:

---

### Post by dcstar on 2008-03-12
> **Conray said:**
> I have an old ISA Soundblaster 16 card that is not being recognized by Ubuntu 6.0. Does anyone have a simple fix for this issue. I'm new to Linux and would love to eliminate Windows from my PC's one day. Starting with this PC I'm working on first.

 My motherboard is an Asus P3B-F with two ISA slots. I've had this Sound Blaster card for several years in storage. it worked perfect under Windows 98. Now I have Ubuntu full force and it isn't seen by the OS.

Any ideas would be appreciated.


Simple, no... but you could probably compile your own kernel with support for that hardware switched on.

---

### Post by prshah on 2008-03-12
> **Conray said:**
> I have an old ISA Soundblaster 16 card that is not being recognized by Ubuntu 
Any ideas would be appreciated.


ISA is from the days of pre-plng-n-play. You will have to know which IRQ and Memory ranges it uses. If you still have that Win98 machine, type ```
set
``` in a command prompt and look for a line like > BLASTER=A220 I15 D5...

The "A" part is the address, and the "I" part the IRQ.If you cant get at the old machine, take a look at the card; it will have a jumper settings table printed on the back of it.

Once you get the settings, you can pass them to ```
sudo modprobe snd-sbawe address=220 irq=15 dma=05
``` or whatever. If snd-sbawe doesn't work try snd-sb8 or snd-sb16.

If it still fails, post the output of ```
dmesg | tail -50
``` here and lets see where its tripping up.

Cheers,
PRShah

---

### Post by Conray on 2008-03-13
Details didn't work. It saw the sound card, but no cigar. I'm going to try a PCI and see what happens. :confused:

Thanks for the advice.

---

### Post by jrusso2 on 2008-03-13
If you have a pci thats a much better choice with modern Linux distros.

---

### Post by kostkon on 2008-03-13
> **Conray said:**
> I have an old ISA Soundblaster 16 card that is not being recognized by Ubuntu 6.0. Does anyone have a simple fix for this issue. I'm new to Linux and would love to eliminate Windows from my PC's one day. Starting with this PC I'm working on first.

 My motherboard is an Asus P3B-F with two ISA slots. I've had this Sound Blaster card for several years in storage. it worked perfect under Windows 98. Now I have Ubuntu full force and it isn't seen by the OS.

Any ideas would be appreciated.

Thanks
:guitar:

The Linux kernel *does not auto-detect* ISA sound cards any more, since ISA tech is obsolete. This does not mean that you cannot make your card to work, you just need to load the driver yourself. Follow [this how-to from the *Ubuntu documentation* for instructions on how to set up your old ISA card]("https://help.ubuntu.com/community/HowToSetupSoundCards").

But, I have to say the obvious thing: you should better buy a PCI sound card. You can find a decent one for less than $5.

---

### Post by dig314 on 2008-05-03
Same problem ( old pc - mainly used to watch DVDs, win98se, ISA AWE 64 ) different person.

I type SET to get the specifics on the card. 

THEN 
sudo modprobe snd-sbawe address=220 irq=15 dma=05
- except I used my specific settings.
When that didn't seem to help, I tried it by adding 
isapnp=0

It is entirely possible that something I have tried earlier in the week is causing the steps above to fail - I don't know much about LINUX.

Finally, going PCI would be a minor issue - I will either have to remove the NIC card or snuggle a PCI sound card next to the Graphics Card.


Below is the output from dmesg | tail -50

Thank you for your help.

council@council-desktop:~$ dmesg | tail -50
[   63.081807] lp0: using parport0 (interrupt-driven).
[   63.441056] sbawe: AUDIO the requested resources are invalid, using auto config
[   63.441184] pnp: Unable to assign resources to device 01:01.00.
[   63.441190] sbawe: AUDIO pnp configure failure
[   64.648881] EXT3 FS on sdb5, internal journal
[   83.011383] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[   83.011558] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[   83.012028] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[   83.012252] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[   85.124125] eth0:  setting half-duplex.
[   85.351573] ppdev: user-space parallel port driver
[   85.704644] audit(1209824073.398:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4385 profile="/usr/sbin/cupsd"
[   85.954843] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   86.694184] Failure registering capabilities with primary security module.
[   87.238775] Bluetooth: Core ver 2.11
[   87.239032] NET: Registered protocol family 31
[   87.239039] Bluetooth: HCI device and connection manager initialized
[   87.239048] Bluetooth: HCI socket layer initialized
[   87.296044] Bluetooth: L2CAP ver 2.8
[   87.296055] Bluetooth: L2CAP socket layer initialized
[   87.345229] Bluetooth: RFCOMM socket layer initialized
[   87.345434] Bluetooth: RFCOMM TTY layer initialized
[   87.345441] Bluetooth: RFCOMM ver 1.8
[  216.924525] usb 1-2: new full speed USB device using uhci_hcd and address 2
[  217.096626] usb 1-2: configuration #1 chosen from 1 choice
[  217.797344] usbcore: registered new interface driver libusual
[  217.957967] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[  217.958185] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[  218.226691] Initializing USB Mass Storage driver...
[  218.228110] scsi2 : SCSI emulation for USB Mass Storage devices
[  218.229529] usb-storage: device found at 2
[  218.229542] usb-storage: waiting for device to settle before scanning
[  218.229914] usbcore: registered new interface driver usb-storage
[  218.230090] USB Mass Storage support registered.
[  223.225632] usb-storage: device scan complete
[  223.229622] scsi 2:0:0:0: Direct-Access     Imation   USB Flash Drive 2.00 PQ: 0 ANSI: 2
[  224.562329] sd 2:0:0:0: [sdc] 1013760 512-byte hardware sectors (519 MB)
[  224.565986] sd 2:0:0:0: [sdc] Write Protect is off
[  224.566001] sd 2:0:0:0: [sdc] Mode Sense: 03 00 00 00
[  224.566007] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[  224.580312] sd 2:0:0:0: [sdc] 1013760 512-byte hardware sectors (519 MB)
[  224.584288] sd 2:0:0:0: [sdc] Write Protect is off
[  224.584303] sd 2:0:0:0: [sdc] Mode Sense: 03 00 00 00
[  224.584310] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[  224.584322]  sdc: sdc1
[  224.591299] sd 2:0:0:0: [sdc] Attached SCSI removable disk
[  224.591416] sd 2:0:0:0: Attached scsi generic sg3 type 0
[  273.883592] NET: Registered protocol family 10
[  273.885164] lo: Disabled Privacy Extensions
[  273.885446] ADDRCONF(NETDEV_UP): eth0: link is not ready

Update
About every other time I restart the system, UBUNTU sees my TV Tuner card.
After restart, here is the exact command I used:
sudo modprobe snd-sbawe address=240 irq=10 dma=03

council@council-desktop:~$ dmesg | tail -50
[   58.846415] cx88[0]:    card=54 -> Norwood Micro TV Tuner
[   58.846421] cx88[0]:    card=55 -> Shenzhen Tungsten Ages Tech TE-DTV-250 / Swann OEM
[   58.846428] cx88[0]:    card=56 -> Hauppauge WinTV-HVR1300 DVB-T/Hybrid MPEG Encoder
[   58.846436] CORE cx88[0]: subsystem: 0000:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[   58.846445] TV tuner -1 at 0x1fe, Radio tuner -1 at 0x1fe
[   59.564576] Linux agpgart interface v0.102 (c) Dave Jones
[   60.160461] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[   60.415256] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   60.674590] input: PC Speaker as /class/input/input3
[   60.805456] pnp: Device 01:01.01 activated.
[   60.822133] gameport: NS558 PnP Gameport is pnp01:01.01/gameport0, io 0x200, speed 745kHz
[   60.936313] pnp: Device 00:13 activated.
[   60.936324] parport_pc 00:13: reported by Plug and Play BIOS
[   60.936358] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   60.954512] tveeprom 0-0050: Huh, no eeprom present (err=-121)?
[   60.954547] cx88[0]/0: found at 0000:00:0e.0, rev: 5, irq: 10, latency: 165, mmio: 0xe8000000
[   61.176305] tuner 0-0060: All bytes are equal. It is not a TEA5767
[   61.176316] tuner 0-0060: chip found @ 0xc0 (cx88[0])
[   61.187185] cx88[0]/0: registered device video0 [v4l2]
[   61.187255] cx88[0]/0: registered device vbi0
[   61.187278] tuner 0-0060: tuner type not set
[   61.187391] agpgart: Detected an Intel 440BX Chipset.
[   61.191666] agpgart: AGP aperture is 64M @ 0xec000000
[   61.191952] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   61.192774] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[   62.701332] lp0: using parport0 (interrupt-driven).
[   63.447257] pnp: Unable to assign resources to device 01:01.00.
[   63.447269] sbawe: AUDIO pnp configure failure
[   64.781789] EXT3 FS on sdb5, internal journal
[   83.152989] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[   83.153160] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[   83.153625] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[   83.153845] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[   85.190153] eth0:  setting half-duplex.
[   85.255039] ppdev: user-space parallel port driver
[   85.522747] audit(1209826546.897:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4353 profile="/usr/sbin/cupsd"
[   85.628364] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   86.518557] Failure registering capabilities with primary security module.
[   87.104520] Bluetooth: Core ver 2.11
[   87.104778] NET: Registered protocol family 31
[   87.104786] Bluetooth: HCI device and connection manager initialized
[   87.104794] Bluetooth: HCI socket layer initialized
[   87.168660] Bluetooth: L2CAP ver 2.8
[   87.168671] Bluetooth: L2CAP socket layer initialized
[   87.282250] Bluetooth: RFCOMM socket layer initialized
[   87.282461] Bluetooth: RFCOMM TTY layer initialized
[   87.282468] Bluetooth: RFCOMM ver 1.8
[  188.338010] NET: Registered protocol family 10
[  188.338461] lo: Disabled Privacy Extensions
[  188.338734] ADDRCONF(NETDEV_UP): eth0: link is not ready

---

### Post by dig314 on 2008-05-03
I got my ISA SB AWE working by physically removing the TV Tuner CARD. 

Dig314

---

### Post by rowerdave on 2008-05-04
ISA sound cards can be configured fine - it does take a little bit of manual configuration though.

There is a very good guide linked below.
[https://help.ubuntu.com/community/HowToSetupSoundCards](https://help.ubuntu.com/community/HowToSetupSoundCards)

One afterthought: if you set your ISA card up (say) with IRQ10, the BIOS settings should be such that no other devices use the selected IRQ.

Further details on debugging IRQ conflicts can be found here:
[https://help.ubuntu.com/community/DebuggingIRQProblems](https://help.ubuntu.com/community/DebuggingIRQProblems)

---

