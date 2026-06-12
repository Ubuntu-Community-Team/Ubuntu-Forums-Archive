---
title: "ouch weird errors from ata"
date: 2007-04-05
forum: General Help
---

### Post by inphektion on 2007-04-05
ok have ubuntu with my own feisty fawn upgrade from edgy eft running in vmware workstation.  after the upgrade my 4gb of space was filled so I couldn't login.  I ran aptitude clean and freed up 750 MB to login.  To resolve my space issue for the future I then ran the virtual disk manager program from vmware to expand my .vmdk from 4GB to 6GB.  Then I booted gparted Live CD and grew my / partition from 4gb to 6gb and moved the swap to the end of the 6gb (used to be at end of the 4gb).  everything completed successfully and I can boot and login and df shows 6GB of space.  However when I boot I get this a lot in the output:
```
[   46.538368] agpgart: AGP aperture is 64M @ 0xe8000000
[   46.854049] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   46.997776] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   47.061628] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[   47.061782] piix4_smbus 0000:00:07.3: Host SMBus controller not enabled!
[   47.108430] input: PC Speaker as /class/input/input2
[   47.916309] parport: PnPBIOS parport detected.
[   47.918340] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   48.006470] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   48.493728] sr0: scsi3-mmc drive: 1x/1x xa/form2 cdda tray
[   48.494964] Uniform CD-ROM driver Revision: 3.20
[   48.495317] sr 2:0:0:0: Attached scsi CD-ROM sr0
[   48.808752] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   48.808946] ata2.00: (BMDMA stat 0x26)
[   48.809197] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x43 data 12 in
[   48.810356]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   49.128470] ata2.00: configured for UDMA/33
[   49.128956] ata2: EH complete
[   49.129355] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   49.129469] ata2.00: (BMDMA stat 0x26)
[   49.129538] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x43 data 12 in
[   49.129558]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)

```

and it repeats A LOT with the ata2.00 stuff you see.  
anyone know what is going on here? how can i fix or even troubleshoot?

---

### Post by inphektion on 2007-04-05
updated the UUID of my swap partition in /etc/fstab as it was wrong based on the changes I made.  However that didn't help the errors.

---

### Post by inphektion on 2007-04-06
nothing?  killing me.  pls don't make me do a clean reinstall of the whole OS.

---

### Post by inphektion on 2007-04-06
no linux wiz here?

---

### Post by crouton on 2007-04-21
This appears to be an unfortunately common problem for a subset of ubuntu users.  There's already a couple threads on it for just about each release.  Sometimes disabling SATA works, sometimes switching optical drives works, sometimes resetting BIOS to default works, sometimes nothing works. :(

---

### Post by ccesare on 2007-07-03
I also get these errors on my virtualized Archlinux distribution, but everything seems to work fine after the errors.

Found any more information?

---

