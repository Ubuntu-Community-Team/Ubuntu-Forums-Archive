---
title: "[SOLVED] S3 Suspend resumes with blank screen"
date: 2007-08-31
forum: General Help
---

### Post by Arcturus691 on 2007-08-31
Hello all,
I am having a problem where my machine suspends to ram  (S3 suspend) correctly but when I resume, the fans and hard drive spin up but I get no video (monitor never comes out of standby) and my keyboard is locked up .  I have to reboot the computer to get a screen back.   Here are the machine specs:

AMD Athlon 64 3800+ Venice 2.4GHz Socket 939 Processor
ABIT KN8 SLI 939 NVIDIA nForce4 SLI ATX AMD Motherboard
Crucial Ballistix 1GB (2 x 512MB) 184-Pin DDR SDRAM DDR 400 (PC 3200) Dual Channel
GIGABYTE GV-NX73T256P-RH GeForce 7300GT 256MB 128-bit GDDR2 PCI Express x16
Western Digital Caviar RE WD1600YS 160GB 7200 RPM SATA
Maxtor 6Y160P0 160GB ATA 133
ENERMAX Liberty ELT500AWT ATX12V 500W Power Supply
Microsoft Digital Media Pro Keyboard USB
LCd Monitor Samsung SyncMaster 931BF

~$ uname -r
2.6.20-16-generic
running Ubuntu Feisty Fawn 7.04 x86 64bit

I have attached my /var/log/syslog 

nvidia-settings:
Driver Version 1.0-9631
Server Version 11.0
Server Vendor Version 7.2.0

I can suspend to ram in windows XP SP2, so I don't think this is a BIOS configuration issue. BIOS version is NF-CK804-6A61fA1DC-16

Any help will be greatly appreciated :)

---

### Post by Arcturus691 on 2007-08-31
Solved the problem by updating bios to version 19.  The funny thing is that Abit doesn't mention any fixes for S3 suspending in the bios fix log.

---

