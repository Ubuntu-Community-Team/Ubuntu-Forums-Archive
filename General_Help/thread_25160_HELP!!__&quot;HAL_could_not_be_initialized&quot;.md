---
title: "HELP!!  &quot;HAL could not be initialized&quot;"
date: 2005-04-09
forum: General Help
---

### Post by artinla on 2005-04-09
I get a "Hal could not be Initialized" each time I boot.  The device manager is empty when this happens, flashes on the screen for a second and then closes. 

None of my pluggable media or CDROM drives work when my system is in this condition.

I have done some research and found that the following script will turn everything back on, but that is a pain to have to run this each time I reboot.  Does anyone have any ideas? Where would you start looking to find the problem?  This all started with some Ubuntu updates a couple of weeks ago.  It was working fine until then.

Script that fixes it:  (this restarts the HAL/DBUS and GVM)

sudo /etc/init.d/dbus-1 restart
wait
gnome-volume-manager


I don't want to have to reload my whole system to fix this.. It is just how I want it except for the HAL error.

Art

---

### Post by jdong on 2005-04-09
Moved to a more approprate forum.

The Tips, Tricks, and Customization forum is for people who write informative articles about how to get a task done in Ubuntu, **NOT** for asking questions.

---

### Post by Ranime on 2005-04-09
I had the same problem...

The time the system did work, I opened Synaptic and go to Search...
Entered "hal" (without the quotes) and started the search.

For all the hal-hits i either chose "re-install" if they were already installed, or "mark for installation" if they wheren't already.

Pop in the Ubuntu 5.04 cd and press UPDATE.

after the update, eject the cd and reboot.

---

### Post by artinla on 2005-04-09
Sorry Mod, I lost track of where I was when I made the post.

BTW, why do we have to have so many forums and none for just general troubleshooting or error messages within Hoary?

Up until the other day, I could just click the Development forum and most pertinent things were right there.  Now I have to decide if it is "Hardware", "Desktop", "Other Applications" etc..  Can't we just have a forum for general help with Ubuntu?  I feel like  far fewer people see my post when I have to put it on some obscure "Other software errors not covered elsewhere" forum.


BTW, How can I have the above mentioned script run in the background and not stop once I run it?  right now, it runs in a terminal window and the gvm stops fnding new drives when I shut down the terminal window.

---

### Post by artinla on 2005-04-09
I did try the reinstall of all HAL related things, but it does not help in my case.  Same problem after reinstalling 5 or 6 times.

Thanks

---

### Post by jdong on 2005-04-09
[QUOTE=artinla]
Up until the other day, I could just click the Development forum and most pertinent things were right there. Now I have to decide if it is "Hardware", "Desktop", "Other Applications" etc.. Can't we just have a forum for general help with Ubuntu? I feel like far fewer people see my post when I have to put it on some obscure "Other software errors not covered elsewhere" forum.[/QUOTE]


If we stuck everything in one forum, this thread would be buried 3+ pages deep within 12 hours. I'm sure you wouldn't want that to happen.

We keep very good watch on ALL the forums. No forum gets ignored.

---

### Post by artinla on 2005-04-09
I see your point.  I just have a hard time thinking of the HAL as an "Other Application"..

I bow to the forum masters.


Anyway.. How can I have the above mentioned script run in the background and not stop once I run it? right now, it runs in a terminal window and the gvm stops fnding new drives when I shut down the terminal window.


Better yet.. How can I FIX the problem?!!

 :grin:

---

### Post by JoKoT3 on 2005-04-09
here is my tips (just discovered)

just after starting your gnome session, open a terminal and type dmesg 
if you are as lucky as me you would find a huge amount of timeout in probing a peripheral (in my case it was an usb printer that I've plugged off)
simply uninstall it (in my case again it was easy to do)

and it will work fine  \\:D/ 

hope it will help some of you

ps : ubuntu roxx !

---

### Post by artinla on 2005-04-09
Here is the output.. I don't know how to make it into a scrollbox. Do you see anything (I see a hotplug error but I don't know what it means)

Art


```

sata_promise PATA port found
ata1: SATA max UDMA/133 cmd 0xE082E200 ctl 0xE082E238 bmdma 0x0 irq 19
ata2: SATA max UDMA/133 cmd 0xE082E280 ctl 0xE082E2B8 bmdma 0x0 irq 19
ata3: PATA max UDMA/133 cmd 0xE082E300 ctl 0xE082E338 bmdma 0x0 irq 19
ata1: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4003 85:3469 86:3c01 87:4003 88:407f
ata1: dev 0 ATA, max UDMA/133, 234441648 sectors: lba48
ata1: dev 0 configured for UDMA/133
scsi0 : sata_promise
ata2: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4003 85:3469 86:3c01 87:4003 88:407f
ata2: dev 0 ATA, max UDMA/133, 234441648 sectors: lba48
ata2: dev 0 configured for UDMA/133
scsi1 : sata_promise
ATA: abnormal status 0x8 on port 0xE082E31C
ata3: disabling port
scsi2 : sata_promise
elevator: using anticipatory as default io scheduler
  Vendor: ATA       Model: ST3120026AS       Rev: 3.05
  Type:   Direct-Access                      ANSI SCSI revision: 05
  Vendor: ATA       Model: ST3120827AS       Rev: 3.42
  Type:   Direct-Access                      ANSI SCSI revision: 05
SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
SCSI device sda: drive cache: write back
SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
SCSI device sda: drive cache: write back
 /dev/scsi/host0/bus0/target0/lun0: p1 p2 < p5 >
Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
SCSI device sdb: 234441648 512-byte hdwr sectors (120034 MB)
SCSI device sdb: drive cache: write back
SCSI device sdb: 234441648 512-byte hdwr sectors (120034 MB)
SCSI device sdb: drive cache: write back
 /dev/scsi/host1/bus0/target0/lun0: p1
Attached scsi disk sdb at scsi1, channel 0, id 0, lun 0
Stopping tasks: ==|
Freeing memory... done (446 pages freed)
Restarting tasks... done
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
Adding 1510068k swap on /dev/sda5.  Priority:-1 extents:1
EXT3 FS on sda1, internal journal
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Probing IDE interface ide0...
hda: ST320413A, ATA DISK drive
Probing IDE interface ide1...
hdc: HP DVD Writer 640, ATAPI CD/DVD-ROM drive
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
ide1 at 0x170-0x177,0x376 on irq 15
hda: max request size: 128KiB
hda: 39102336 sectors (20020 MB) w/512KiB Cache, CHS=38792/16/63
hda: cache flushes not supported
 /dev/ide/host0/bus0/target0/lun0: p1
hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20
lp: driver loaded but no devices found
mice: PS/2 mouse device common for all mice
Linux agpgart interface v0.100 (c) Dave Jones
nvidia: module license 'NVIDIA' taints kernel.
ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 16
ACPI: PCI interrupt 0000:02:00.0[A] -> GSI 16 (level, high) -> IRQ 16
NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7174  Tue Mar 22 06:44:39 PST 2005
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email="dm-devel@redhat.com"]dm-devel@redhat.com[/email]
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.10-5-386
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
agpgart: Detected AGP bridge 0
agpgart: Setting up Nforce3 AGP.
agpgart: Maximum main memory to use for agp memory: 439M
agpgart: AGP aperture is 128M @ 0xf0000000
i2c_adapter i2c-0: nForce2 SMBus adapter at 0x5000
i2c_adapter i2c-1: nForce2 SMBus adapter at 0x5040
usbcore: registered new driver usbfs
usbcore: registered new driver hub
ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 20
ACPI: PCI interrupt 0000:00:02.0[A] -> GSI 20 (level, high) -> IRQ 20
ohci_hcd 0000:00:02.0: nVidia Corporation nForce3 USB 1.1
PCI: Setting latency timer of device 0000:00:02.0 to 64
ohci_hcd 0000:00:02.0: irq 20, pci mem 0xfebfd000
ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 3 ports detected
ACPI: PCI Interrupt Link [LUS1] enabled at IRQ 20
ACPI: PCI interrupt 0000:00:02.1[B] -> GSI 20 (level, high) -> IRQ 20
ohci_hcd 0000:00:02.1: nVidia Corporation nForce3 USB 1.1 (#2)
PCI: Setting latency timer of device 0000:00:02.1 to 64
ohci_hcd 0000:00:02.1: irq 20, pci mem 0xfebfe000
ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 3 ports detected
ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 20
ACPI: PCI interrupt 0000:00:02.2[C] -> GSI 20 (level, high) -> IRQ 20
ehci_hcd 0000:00:02.2: nVidia Corporation nForce3 USB 2.0
PCI: Setting latency timer of device 0000:00:02.2 to 64
ehci_hcd 0000:00:02.2: irq 20, pci mem 0xfebffc00
usb 2-1: new low speed USB device using ohci_hcd and address 2
ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
PCI: cache line size of 64 is not supported by device 0000:00:02.2
ehci_hcd 0000:00:02.2: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 6 ports detected
forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.30.
PCI: Enabling device 0000:00:05.0 (0005 -> 0007)
ACPI: PCI Interrupt Link [LKLN] enabled at IRQ 21
ACPI: PCI interrupt 0000:00:05.0[A] -> GSI 21 (level, high) -> IRQ 21
PCI: Setting latency timer of device 0000:00:05.0 to 64
0000:00:05.0: Invalid Mac address detected: 01:23:45:67:89:ab
Please complain to your hardware vendor. Switching to a random MAC.
usb 2-1: new low speed USB device using ohci_hcd and address 3
eth0: forcedeth.c: subsystem: 01043:80c5 bound to 0000:00:05.0
usb 2-2: new low speed USB device using ohci_hcd and address 4
NFORCE3-150: IDE controller at PCI slot 0000:00:08.0
NFORCE3-150: chipset revision 165
NFORCE3-150: not 100% native mode: will probe irqs later
NFORCE3-150: BIOS didn't set cable bits correctly. Enabling workaround.
NFORCE3-150: 0000:00:08.0 (rev a5) UDMA133 controller
NFORCE3-150: port 0x01f0 already claimed by ide0
NFORCE3-150: port 0x0170 already claimed by ide1
NFORCE3-150: neither IDE port enabled (BIOS)
usbcore: registered new driver hiddev
input: USB HID v1.10 Keyboard [Switch Switch] on usb-0000:00:02.1-1
input: USB HID v1.10 Mouse [Switch Switch] on usb-0000:00:02.1-1
input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:02.1-2
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
eth0: no link during initialization.
ts: Compaq touchscreen protocol output
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
eth0: link up.
ACPI: PCI interrupt 0000:01:05.0[A] -> GSI 19 (level, high) -> IRQ 19
gameport: pci0000:01:05.1 speed 1193 kHz
agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
drivers/usb/input/hid-input.c: event field not found
drivers/usb/input/hid-input.c: event field not found
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) [PWRF]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
eth0: no IPv6 routers present
NET: Registered protocol family 17
eth0: Promiscuous mode enabled.
device eth0 entered promiscuous mode
UDF-fs: No VRS found
ISO 9660 Extensions: Microsoft Joliet Level 3
ISOFS: changing to secondary root

```

---

### Post by jdong on 2005-04-09
[QUOTE=artinla]Here is the output.. I don't know how to make it into a scrollbox.[/QUOTE]

You can do so by wrapping the text with [ CODE ] and [ /CODE ] tags (without the spaces)

I've taken the liberty to do so for you :)

---

### Post by artinla on 2005-04-09
Thanks JDong

---

### Post by jdong on 2005-04-09
Have you tried a reinstall of  dbus-1 and hotplug?

Can you post the output of "find /etc/rc*.d"

---

### Post by artinla on 2005-04-09
I have reinstalled both dbus-1 and hotplug several times.  

Here is the output of "find /etc/rc*.d"



```
art@flatulus:~$ find /etc/rc*.d
/etc/rc0.d
/etc/rc0.d/K20makedev
/etc/rc0.d/K25hwclock.sh
/etc/rc0.d/S30urandom
/etc/rc0.d/S20sendsigs
/etc/rc0.d/S31umountnfs.sh
/etc/rc0.d/S40umountfs
/etc/rc0.d/S90halt
/etc/rc0.d/K20rsync
/etc/rc0.d/S50lvm
/etc/rc0.d/K75hdparm
/etc/rc0.d/K89hotplug
/etc/rc0.d/S50mdadm-raid
/etc/rc0.d/K25mdadm
/etc/rc0.d/K11cron
/etc/rc0.d/K20inetd
/etc/rc0.d/S36ifupdown
/etc/rc0.d/S35networking
/etc/rc0.d/K86ppp
/etc/rc0.d/K20postfix
/etc/rc0.d/K89atd
/etc/rc0.d/K90sysklogd
/etc/rc0.d/K89klogd
/etc/rc0.d/S49evms
/etc/rc0.d/K20alsa
/etc/rc0.d/K15fetchmail
/etc/rc0.d/K20acpid
/etc/rc0.d/K20powernowd
/etc/rc0.d/K20dbus-1
/etc/rc0.d/K20acpi-support
/etc/rc0.d/K20apmd
/etc/rc0.d/K19cupsys
/etc/rc0.d/K01gdm
/etc/rc0.d/K76readahead
/etc/rc0.d/K20nvidia-glx
/etc/rc0.d/K91apache
/etc/rc0.d/K20backuppc
/etc/rc0.d/K20wwwoffle
/etc/rc0.d/K20postgresql
/etc/rc0.d/S32portmap
/etc/rc0.d/K19nis
/etc/rc0.d/K20ssh
/etc/rc0.d/K20dhcp
/etc/rc0.d/K20exim4
/etc/rc0.d/K40frox
/etc/rc0.d/K05heartbeat
/etc/rc0.d/K20jabber
/etc/rc0.d/K20pptpd
/etc/rc0.d/K85quota
/etc/rc0.d/K79quotarpc
/etc/rc0.d/K19samba
/etc/rc0.d/K20snort
/etc/rc0.d/K21spamassassin
/etc/rc0.d/K20usermin
/etc/rc0.d/K20webmin
/etc/rc0.d/K20mon
/etc/rc0.d/K20slpd
/etc/rc0.d/K20xinetd
/etc/rc0.d/K30squid
/etc/rc0.d/K50proftpd
/etc/rc0.d/K80slapd
/etc/rc0.d/K20firestarter
/etc/rc1.d
/etc/rc1.d/K20makedev
/etc/rc1.d/S20single
/etc/rc1.d/K20rsync
/etc/rc1.d/K25mdadm
/etc/rc1.d/K11cron
/etc/rc1.d/K20inetd
/etc/rc1.d/K86ppp
/etc/rc1.d/K20postfix
/etc/rc1.d/K89atd
/etc/rc1.d/K90sysklogd
/etc/rc1.d/K89klogd
/etc/rc1.d/K20alsa
/etc/rc1.d/K15fetchmail
/etc/rc1.d/K20acpid
/etc/rc1.d/K20powernowd
/etc/rc1.d/K20dbus-1
/etc/rc1.d/K20acpi-support
/etc/rc1.d/K20apmd
/etc/rc1.d/K19cupsys
/etc/rc1.d/K01gdm
/etc/rc1.d/K20nvidia-glx
/etc/rc1.d/K91apache
/etc/rc1.d/K20backuppc
/etc/rc1.d/K20wwwoffle
/etc/rc1.d/K20postgresql
/etc/rc1.d/K81portmap
/etc/rc1.d/K19nis
/etc/rc1.d/K20ssh
/etc/rc1.d/K20dhcp
/etc/rc1.d/K20exim4
/etc/rc1.d/K40frox
/etc/rc1.d/K05heartbeat
/etc/rc1.d/K20jabber
/etc/rc1.d/K20pptpd
/etc/rc1.d/K79quotarpc
/etc/rc1.d/K19samba
/etc/rc1.d/K20snort
/etc/rc1.d/K21spamassassin
/etc/rc1.d/K20usermin
/etc/rc1.d/K20webmin
/etc/rc1.d/K20mon
/etc/rc1.d/K20slpd
/etc/rc1.d/K20xinetd
/etc/rc1.d/K30squid
/etc/rc1.d/K50proftpd
/etc/rc1.d/K80slapd
/etc/rc1.d/K20firestarter
/etc/rc2.d
/etc/rc2.d/S20makedev
/etc/rc2.d/S99rmnologin
/etc/rc2.d/S99stop-bootlogd
/etc/rc2.d/S20rsync
/etc/rc2.d/S25mdadm
/etc/rc2.d/S89cron
/etc/rc2.d/S20inetd
/etc/rc2.d/S14ppp
/etc/rc2.d/S20postfix
/etc/rc2.d/S89atd
/etc/rc2.d/S10sysklogd
/etc/rc2.d/S11klogd
/etc/rc2.d/S12alsa
/etc/rc2.d/S99fetchmail
/etc/rc2.d/S20acpid
/etc/rc2.d/K11anacron
/etc/rc2.d/S89anacron
/etc/rc2.d/S20powernowd
/etc/rc2.d/S20dbus-1
/etc/rc2.d/S05vbesave
/etc/rc2.d/S99acpi-support
/etc/rc2.d/S20apmd
/etc/rc2.d/S19cupsys
/etc/rc2.d/S13gdm
/etc/rc2.d/S20nvidia-glx
/etc/rc2.d/S91apache
/etc/rc2.d/S20backuppc
/etc/rc2.d/K77ntp-server
/etc/rc2.d/S20wwwoffle
/etc/rc2.d/S20postgresql
/etc/rc2.d/S18portmap
/etc/rc2.d/S19nis
/etc/rc2.d/S20ssh
/etc/rc2.d/S20dhcp
/etc/rc2.d/S20exim4
/etc/rc2.d/S40frox
/etc/rc2.d/S75heartbeat
/etc/rc2.d/S20jabber
/etc/rc2.d/S20pptpd
/etc/rc2.d/S21quotarpc
/etc/rc2.d/S20samba
/etc/rc2.d/S20snort
/etc/rc2.d/S19spamassassin
/etc/rc2.d/S20usermin
/etc/rc2.d/S20webmin
/etc/rc2.d/S20mon
/etc/rc2.d/S20slpd
/etc/rc2.d/S20xinetd
/etc/rc2.d/S30squid
/etc/rc2.d/S50proftpd
/etc/rc2.d/S19slapd
/etc/rc2.d/S20firestarter
/etc/rc3.d
/etc/rc3.d/S20makedev
/etc/rc3.d/S99rmnologin
/etc/rc3.d/S99stop-bootlogd
/etc/rc3.d/S20rsync
/etc/rc3.d/S25mdadm
/etc/rc3.d/S89cron
/etc/rc3.d/S20inetd
/etc/rc3.d/S14ppp
/etc/rc3.d/S20postfix
/etc/rc3.d/S89atd
/etc/rc3.d/S10sysklogd
/etc/rc3.d/S11klogd
/etc/rc3.d/S12alsa
/etc/rc3.d/S99fetchmail
/etc/rc3.d/S20acpid
/etc/rc3.d/K11anacron
/etc/rc3.d/S89anacron
/etc/rc3.d/S20powernowd
/etc/rc3.d/S20dbus-1
/etc/rc3.d/S05vbesave
/etc/rc3.d/S99acpi-support
/etc/rc3.d/S20apmd
/etc/rc3.d/S19cupsys
/etc/rc3.d/S13gdm
/etc/rc3.d/S20nvidia-glx
/etc/rc3.d/S91apache
/etc/rc3.d/S20backuppc
/etc/rc3.d/K77ntp-server
/etc/rc3.d/S20wwwoffle
/etc/rc3.d/S20postgresql
/etc/rc3.d/S18portmap
/etc/rc3.d/S19nis
/etc/rc3.d/S20ssh
/etc/rc3.d/S20dhcp
/etc/rc3.d/S20exim4
/etc/rc3.d/S40frox
/etc/rc3.d/S75heartbeat
/etc/rc3.d/S20jabber
/etc/rc3.d/S20pptpd
/etc/rc3.d/S21quotarpc
/etc/rc3.d/S20samba
/etc/rc3.d/S20snort
/etc/rc3.d/S19spamassassin
/etc/rc3.d/S20usermin
/etc/rc3.d/S20webmin
/etc/rc3.d/S20mon
/etc/rc3.d/S20slpd
/etc/rc3.d/S20xinetd
/etc/rc3.d/S30squid
/etc/rc3.d/S50proftpd
/etc/rc3.d/S19slapd
/etc/rc3.d/S20firestarter
/etc/rc4.d
/etc/rc4.d/S20makedev
/etc/rc4.d/S99rmnologin
/etc/rc4.d/S99stop-bootlogd
/etc/rc4.d/S20rsync
/etc/rc4.d/S25mdadm
/etc/rc4.d/S89cron
/etc/rc4.d/S20inetd
/etc/rc4.d/S14ppp
/etc/rc4.d/S20postfix
/etc/rc4.d/S89atd
/etc/rc4.d/S10sysklogd
/etc/rc4.d/S11klogd
/etc/rc4.d/S12alsa
/etc/rc4.d/S99fetchmail
/etc/rc4.d/S20acpid
/etc/rc4.d/K11anacron
/etc/rc4.d/S89anacron
/etc/rc4.d/S20powernowd
/etc/rc4.d/S20dbus-1
/etc/rc4.d/S05vbesave
/etc/rc4.d/S99acpi-support
/etc/rc4.d/S20apmd
/etc/rc4.d/S19cupsys
/etc/rc4.d/S13gdm
/etc/rc4.d/S20nvidia-glx
/etc/rc4.d/S91apache
/etc/rc4.d/S20backuppc
/etc/rc4.d/S20wwwoffle
/etc/rc4.d/S20postgresql
/etc/rc4.d/S18portmap
/etc/rc4.d/S19nis
/etc/rc4.d/S20ssh
/etc/rc4.d/S20dhcp
/etc/rc4.d/S20exim4
/etc/rc4.d/S40frox
/etc/rc4.d/S75heartbeat
/etc/rc4.d/S20jabber
/etc/rc4.d/S20pptpd
/etc/rc4.d/S21quotarpc
/etc/rc4.d/S20samba
/etc/rc4.d/S20snort
/etc/rc4.d/S19spamassassin
/etc/rc4.d/S20usermin
/etc/rc4.d/S20webmin
/etc/rc4.d/S20mon
/etc/rc4.d/S20slpd
/etc/rc4.d/S20xinetd
/etc/rc4.d/S30squid
/etc/rc4.d/S50proftpd
/etc/rc4.d/S19slapd
/etc/rc4.d/S20firestarter
/etc/rc5.d
/etc/rc5.d/S20makedev
/etc/rc5.d/S99rmnologin
/etc/rc5.d/S99stop-bootlogd
/etc/rc5.d/S20rsync
/etc/rc5.d/S25mdadm
/etc/rc5.d/S89cron
/etc/rc5.d/S20inetd
/etc/rc5.d/S14ppp
/etc/rc5.d/S20postfix
/etc/rc5.d/S89atd
/etc/rc5.d/S10sysklogd
/etc/rc5.d/S11klogd
/etc/rc5.d/S12alsa
/etc/rc5.d/S99fetchmail
/etc/rc5.d/S20acpid
/etc/rc5.d/K11anacron
/etc/rc5.d/S89anacron
/etc/rc5.d/S20powernowd
/etc/rc5.d/S20dbus-1
/etc/rc5.d/S05vbesave
/etc/rc5.d/S99acpi-support
/etc/rc5.d/S20apmd
/etc/rc5.d/S19cupsys
/etc/rc5.d/S13gdm
/etc/rc5.d/S20nvidia-glx
/etc/rc5.d/S91apache
/etc/rc5.d/S20backuppc
/etc/rc5.d/S20wwwoffle
/etc/rc5.d/S20postgresql
/etc/rc5.d/S18portmap
/etc/rc5.d/S19nis
/etc/rc5.d/S20ssh
/etc/rc5.d/S20dhcp
/etc/rc5.d/S20exim4
/etc/rc5.d/S40frox
/etc/rc5.d/S75heartbeat
/etc/rc5.d/S20jabber
/etc/rc5.d/S20pptpd
/etc/rc5.d/S21quotarpc
/etc/rc5.d/S20samba
/etc/rc5.d/S20snort
/etc/rc5.d/S19spamassassin
/etc/rc5.d/S20usermin
/etc/rc5.d/S20webmin
/etc/rc5.d/S20mon
/etc/rc5.d/S20slpd
/etc/rc5.d/S20xinetd
/etc/rc5.d/S30squid
/etc/rc5.d/S50proftpd
/etc/rc5.d/S19slapd
/etc/rc5.d/S20firestarter
/etc/rc6.d
/etc/rc6.d/K20makedev
/etc/rc6.d/K25hwclock.sh
/etc/rc6.d/S30urandom
/etc/rc6.d/S20sendsigs
/etc/rc6.d/S31umountnfs.sh
/etc/rc6.d/S40umountfs
/etc/rc6.d/S90reboot
/etc/rc6.d/K20rsync
/etc/rc6.d/S50lvm
/etc/rc6.d/K75hdparm
/etc/rc6.d/K89hotplug
/etc/rc6.d/S50mdadm-raid
/etc/rc6.d/K25mdadm
/etc/rc6.d/K11cron
/etc/rc6.d/K20inetd
/etc/rc6.d/S36ifupdown
/etc/rc6.d/S35networking
/etc/rc6.d/K86ppp
/etc/rc6.d/K20postfix
/etc/rc6.d/K89atd
/etc/rc6.d/K90sysklogd
/etc/rc6.d/K89klogd
/etc/rc6.d/S49evms
/etc/rc6.d/K20alsa
/etc/rc6.d/K15fetchmail
/etc/rc6.d/K20acpid
/etc/rc6.d/K20powernowd
/etc/rc6.d/K20dbus-1
/etc/rc6.d/K20acpi-support
/etc/rc6.d/K20apmd
/etc/rc6.d/K19cupsys
/etc/rc6.d/K01gdm
/etc/rc6.d/K76readahead
/etc/rc6.d/K20nvidia-glx
/etc/rc6.d/K91apache
/etc/rc6.d/K20backuppc
/etc/rc6.d/K20wwwoffle
/etc/rc6.d/K20postgresql
/etc/rc6.d/S32portmap
/etc/rc6.d/K19nis
/etc/rc6.d/K20ssh
/etc/rc6.d/K20dhcp
/etc/rc6.d/K20exim4
/etc/rc6.d/K40frox
/etc/rc6.d/K05heartbeat
/etc/rc6.d/K20jabber
/etc/rc6.d/K20pptpd
/etc/rc6.d/K85quota
/etc/rc6.d/K79quotarpc
/etc/rc6.d/K19samba
/etc/rc6.d/K20snort
/etc/rc6.d/K21spamassassin
/etc/rc6.d/K20usermin
/etc/rc6.d/K20webmin
/etc/rc6.d/K20mon
/etc/rc6.d/K20slpd
/etc/rc6.d/K20xinetd
/etc/rc6.d/K30squid
/etc/rc6.d/K50proftpd
/etc/rc6.d/K80slapd
/etc/rc6.d/K20firestarter
/etc/rcS.d
/etc/rcS.d/README
/etc/rcS.d/S30procps.sh
/etc/rcS.d/S50hwclock.sh
/etc/rcS.d/S18hwclockfirst.sh
/etc/rcS.d/S02mountvirtfs
/etc/rcS.d/S36mountvirtfs
/etc/rcS.d/S05bootlogd
/etc/rcS.d/S10checkroot.sh
/etc/rcS.d/S30checkfs.sh
/etc/rcS.d/S35mountall.sh
/etc/rcS.d/S40hostname.sh
/etc/rcS.d/S45mountnfs.sh
/etc/rcS.d/S55bootmisc.sh
/etc/rcS.d/S55urandom
/etc/rcS.d/S75sudo
/etc/rcS.d/S20module-init-tools
/etc/rcS.d/S26lvm
/etc/rcS.d/S07hdparm
/etc/rcS.d/S40hotplug
/etc/rcS.d/S25mdadm-raid
/etc/rcS.d/S51ntpdate
/etc/rcS.d/S04udev
/etc/rcS.d/S36udev-mtab
/etc/rcS.d/S25libdevmapper1.00
/etc/rcS.d/S39ifupdown
/etc/rcS.d/S18ifupdown-clean
/etc/rcS.d/S05initrd-tools.sh
/etc/rcS.d/S40networking
/etc/rcS.d/S38pppd-dns
/etc/rcS.d/S39dns-clean
/etc/rcS.d/S05keymap.sh
/etc/rcS.d/S27evms
/etc/rcS.d/S48console-screen.sh
/etc/rcS.d/S70xorg-common
/etc/rcS.d/S70screen-cleanup
/etc/rcS.d/S39readahead
/etc/rcS.d/S43portmap
/etc/rcS.d/S35quota
art@flatulus:~$ 



```


Can I make the box smaller?

---

### Post by brickbat on 2005-04-10
Hi,

I had the same problem after I made an invalid mod to the hdparm.conf file.

To ensure this it is not a problem with this file, you can boot with the kernel option nohdparm.

good luck!

ciao
bb

---

### Post by artinla on 2005-04-10
Thanks, I will give that a try.

Art

---

