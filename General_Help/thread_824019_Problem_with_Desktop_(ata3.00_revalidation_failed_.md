---
title: "Problem with Desktop (ata3.00 revalidation failed (errno=-5))"
date: 2008-06-09
forum: General Help
---

### Post by Zeeded on 2008-06-09
Whenever I try to install either Ubuntu 7 or 8 I get this error

(initramfs) [   107.820791] ata3.00 revalidation failed (errno=-5)

I have installed other Linux distro's on this computer. So I'm wondering what's wrong.

CPU: 2.8 ghz
RAM: 3gb
HardDrive: 250gb

---

### Post by Rocket2DMn on 2008-06-09
This is either a problem with the SATA disks or JMicron support.  I was able to get around this by adding "acpi=off noapic" to the kernel boot line from GRUB.

---

