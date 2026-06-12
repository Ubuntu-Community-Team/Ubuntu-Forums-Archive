---
title: "My feisty doesn't boot"
date: 2007-07-22
forum: General Help
---

### Post by francky_51 on 2007-07-22
I'm a french guy so sorry for my english :D

This morning like everyday since one year I booted  my computer on Ubuntu.

After my grub choice the computer stoped at "Starting up ..."

I restarted it and chose the safe mode. At this moment the computer stopped at ACPI: Looking for DSTD in intramfs file DSTD.aml not found 

I restarted it again and added to grub the option noapic but the computer stopped at ACPI: setting ELCR to 0200

Then I tried to boot on live cds (dapper edgy and feisty) but each time I get the same errors.

Please help me !!!!

Thanks

---

### Post by grahams on 2007-07-23
Sounds like you have a major hardware or bios problem. Did you update the bios recently? If so, try to go back to the previous version and see if that fixes things.

Can you boot any OS on the system? 
Are there any diagnostic programs you can run?
As a last resort, try if possible to set the bios to the default settings, then try to boot again.

---

### Post by francky_51 on 2007-07-23
Windows boots normally.
I did a memtest during 2 hours and no errors.
I did a clear cmos try to boot but it didn't work.
I rebooted and now it works.
I really don't understand what's happening.

---

### Post by grahams on 2007-07-25
Sounds like your BIOS was messed up. Are you able to boot ubuntu now?

---

### Post by francky_51 on 2007-07-26
Yes.
Now it's ok.But if I turn off the power supply than turn it on and boot the pc I can't boot on ubuntu.
It only boots after several tries.
The solution is to never turn off the power supply.

I think it can be also a problem with the power supply.
Is it possible under linux to know if voltages on the motherboard are ok ?
I had a look on it in the bios and it was ok.

---

### Post by grahams on 2007-07-27
Is ubuntu installed on a different disk than windows? If so maybe the disk with ubuntu is not powering up when you 1st start your PC, possible if it is configured as a slave ATA drive. That may explain why it keeps working fine until you cycle the power.

---

### Post by francky_51 on 2007-08-17
I love hollidays !!!!

Ubuntu is installed on a different disk and you are right on a ATA drive.

We can say that my problem is solved.

Thank you very much grahams.

See you later on ubuntuforums !!!!

---

