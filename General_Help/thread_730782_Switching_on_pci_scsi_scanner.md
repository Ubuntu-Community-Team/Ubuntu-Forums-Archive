---
title: "Switching on pci scsi scanner?"
date: 2008-03-21
forum: General Help
---

### Post by momist on 2008-03-21
Hi everyone,

I have an old Epson GT-7000 scanner (scsi interface) connected by a PCI adapter.  This scanner works well right away in Gutsy 7.10 (thanks the XSANE team!), but only if it's already switched on at boot time.  If I switch it on once the system is running, the adapter is seen, but not the scanner.

Output from lspci shows:
00:11.0 SCSI storage controller: Adaptec AHA-7850 (rev 01)

but output from  cat /proc/scsi/scsi shows only:
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: ST380011A        Rev: 8.01
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi0 Channel: 00 Id: 01 Lun: 00
  Vendor: ATA      Model: Maxtor 2F030J0   Rev: VAM5
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: LITE-ON  Model: DVDRW LH-20A1H   Rev: LL0C
  Type:   CD-ROM                           ANSI  SCSI revision: 05

Can anyone tell me the right way to make the system see the scanner?  The ideal solution would be to detect that the connected device has been switched on,  but  it would suffice if I knew the command to place in a script to connect the scanner, maybe from a button on the desktop, after I've switched it on.  Rebooting every time is plain "wrong".  :roll:

TIA

---

