---
title: "2 Gb Sandisk not recognized"
date: 2007-04-20
forum: General Help
---

### Post by FreeSoul on 2007-04-20
I searched for this problem but have yet to find a solution. I have a Dell XPS 1710 2Gz Core2duo. 
I don't see the sandisk coming up anywhere. Anyone have any ideas?

Here is the output of LSPCI command:

0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0297 (rev a1)
0000:03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd: Unknown device 0832
0000:03:01.1 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
0000:03:01.2 System peripheral: Ricoh Co Ltd: Unknown device 0843 (rev 01)
0000:03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
0000:03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)0000:09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0000:0c:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)

thanks

---

### Post by Wim Sturkenboom on 2007-04-20
Stick your memory stick in and capture the output of the *dmesg* command after a couple of seconds. It will  have some references to your memory stick (probably at the end.
Post the result here.

I will not be able to follow up as I go on holiday for 2 weeks in a couple of hours.

My output refering to memory sticks; sdb refers to a sandisk (bold), sdc to a memory card in my printer.
```

[B][17179600.448000]   Vendor: SanDisk   Model: Cruzer Micro      Rev: 0.1
[17179600.448000]   Type:   Direct-Access                      ANSI SCSI revision: 02[/B]
[17179600.448000]   Vendor: EPSON     Model: Stylus Storage    Rev: 1.00
[17179600.448000]   Type:   Direct-Access                      ANSI SCSI revision: 02
**[17179600.448000] SCSI device sdb: 2001888 512-byte hdwr sectors (1025 MB)**
[17179600.448000] SCSI device sdc: 62720 512-byte hdwr sectors (32 MB)
[B][17179600.452000] sdb: Write Protect is off
[17179600.452000] sdb: Mode Sense: 03 00 00 00
[17179600.452000] sdb: assuming drive cache: write through[/B]
[17179600.452000] sdc: Write Protect is off
[17179600.452000] sdc: Mode Sense: 0d 00 00 08
[17179600.452000] sdc: assuming drive cache: write through
[B][17179600.452000] SCSI device sdb: 2001888 512-byte hdwr sectors (1025 MB)
[17179600.452000] sdb: Write Protect is off
[17179600.452000] sdb: Mode Sense: 03 00 00 00
[17179600.452000] sdb: assuming drive cache: write through
[17179600.452000]  sdb:<5>SCSI device sdc: 62720 512-byte hdwr sectors (32 MB)
[17179600.456000]  sdb1
[17179600.456000] sd 3:0:0:0: Attached scsi removable disk sdb
[17179600.456000] sd 3:0:0:0: Attached scsi generic sg1 type 0
[17179600.456000] usb-storage: device scan complete[/B]
[17179600.456000] sdc: Write Protect is off
[17179600.456000] sdc: Mode Sense: 0d 00 00 08
[17179600.456000] sdc: assuming drive cache: write through
[17179600.456000]  sdc: sdc1
[17179600.460000] sd 2:0:0:0: Attached scsi removable disk sdc
[17179600.460000] sd 2:0:0:0: Attached scsi generic sg2 type 0
[17179600.460000] usb-storage: device scan complete

```
PS I had a 2 GB that worked, but it died on me

---

