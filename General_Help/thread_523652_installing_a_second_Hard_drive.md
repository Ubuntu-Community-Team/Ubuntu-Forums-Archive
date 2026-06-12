---
title: "installing a second Hard drive"
date: 2007-08-12
forum: General Help
---

### Post by mrlarone on 2007-08-12
Hi,

i'm trying to install a second hard drive. it's plugged in and spinning but not appearing using:

fdisk -l

any ideas?

---

### Post by GerryB on 2007-08-12
> **mrlarone said:**
> Hi,

i'm trying to install a second hard drive. it's plugged in and spinning but not appearing using:

fdisk -l

any ideas?

If they are IDE (wide grey ribbon with 4 pin power connector) drives, you need to configure them as master and slave. There should be a pin configuration picture on the drive.

---

### Post by Arwen on 2007-08-12
Make sure your wires(1 to the PSU and 1 to the motherboard) are OK and you can hear the disc spinning.Also if your disc is SATA2(thin red wires) and your motherboard supports only SATA1 you should move the jumper so as to make the disc work as SATA1.

---

### Post by mrlarone on 2007-08-12
the hard ware is all set up working. i can install one or the other but not together despite which one is set to master and slave.

---

### Post by GerryB on 2007-08-13
> **mrlarone said:**
> the hard ware is all set up working. i can install one or the other but not together despite which one is set to master and slave.

Does it show up in your BIOS?

---

