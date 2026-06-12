---
title: "(driver ?) problem with brand new sata hd"
date: 2008-01-17
forum: General Help
---

### Post by addict3d2x on 2008-01-17
Hello, I'm having a problem with getting my brand new WD5000AAJS hard drive to interact with my system. The HD doesn't seem to be getting recognized by my kernel. So I think its a driver issue, or I have something configured wrong. Currently the device is showing up under /dev/hdd. It should be under /dev/sd* shouldn't it? GParted tells me the drive has an unrecognized disk label, so it cannot format it. fdisk also cannot format it.

edit to make things more clear:
Im posting from this system currently. I have two other ide hard drives, both work great.

I'm running kernel 2.6.23.14 which I compiled the other day, to try and fix this problem. I built in sata_sil, which I think was actually already in my old kernel.

lspci:
```
00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (re    v c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller     (rev a1)
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Process    ing Unit (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio C    ontroler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394    ) Controller (rev a3)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:0b.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid    ] Serial ATA Controller (rev 02)
03:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT]     (rev a2)

```

some of dmesg:
```

[   37.185803] ACPI: PCI Interrupt 0000:01:0b.0[A] -> Link [APC3] -> GSI 18     (level, high) -> IRQ 19
[   37.186287] scsi0 : sata_sil
[   37.186890] scsi1 : sata_sil
[   37.186920] ata1: SATA max UDMA/100 cmd 0xf88ec080 ctl 0xf88ec08a bmdma 0    xf88ec000 irq 19
[   37.186925] ata2: SATA max UDMA/100 cmd 0xf88ec0c0 ctl 0xf88ec0ca bmdma 0    xf88ec008 irq 19
[   37.497234] ata1: SATA link down (SStatus 0 SControl 310)
[   37.810312] ata2: SATA link down (SStatus 0 SControl 310)

...

[   41.066956] hdd: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDM    A(33)

...

[   68.042936] hdd: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[   68.042946] hdd: drive_cmd: error=0x04 { AbortedCommand }
[   68.042948] ide: failed opcode was: 0xec

```

anyone have any suggestions? if you need more info or command output to help, let me know.

---

### Post by Lostincyberspace on 2008-01-17
how old is your motherboard it might not support a drive that large?

---

### Post by addict3d2x on 2008-01-17
Condensed information:

my motherboard is abit nf7-s. It's sata controller " Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] " is turned on in the bios, and not set to raid mode.

Kernel options i have tried booting with:
pci=nomsi

From a newegg.com review:
"In order to set this drive to work with SATA 1.5GB (I don't have a SATA 2 controller, so this was necessary for me), you have to find a jumper cap. Place the jumper cap across pins 5 and 6 on the pin jumper block on the drive".
That is the second row of pins from the left side, when the drive is sitting flat and upright, viewed facing the connector side

so my hardware is ready, and should be accessible now, but i still get the same message from dmesg. can someone with working sata drives post their kernel .config please?

---

### Post by danwood76 on 2008-01-17
it could be that your sata controller is set to raid mode which may cause some issues when trying to access it normally.
Try changing it to IDE mode in the bios which could help.

I have that sata controller on my PC and had one of its variants on my Abit IC7-Max3 which Im pretty sure I had working properly.

regards,
Danny

---

### Post by addict3d2x on 2008-01-17
> **danwood76 said:**
> it could be that your sata controller is set to raid mode which may cause some issues when trying to access it normally.
Try changing it to IDE mode in the bios which could help.
Danny

done.

---

### Post by addict3d2x on 2008-01-17
I condensed info into one post, sorry i posted a lot.

---

### Post by addict3d2x on 2008-01-17
see above
I condensed info into one post, sorry i posted a lot.

---

