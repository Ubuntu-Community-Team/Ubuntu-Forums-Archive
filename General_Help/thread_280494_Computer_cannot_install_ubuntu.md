---
title: "Computer cannot install ubuntu"
date: 2006-10-19
forum: General Help
---

### Post by telepheedian on 2006-10-19
My computer cannot detect the cd in the ubuntu installer. What hardware from my computer would be disallowing this? My hardware list goes as follows (from Sandra) :

Processor
Model : Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
Speed : 1.87GHz
Performance Rating : PR6342 (estimated)
Cores per Processor : 2 Unit(s)
Threads per Core : 1 Unit(s)
Type : Dual-Core
Internal Data Cache : 2x 32kB Synchronous, Write-Thru, 8-way set, 64 byte line size
L2 On-board Cache : 2MB ECC Synchronous, ATC, 8-way set, 64 byte line size, 2 threads sharing

Mainboard
Bus(es) : ISA X-Bus PCI PCIe IMB USB FireWire/1394 i2c/SMBus
MP Support : 1 Processor(s)
MP APIC : Yes
System BIOS : AT/AT COMPATIBLE INTEL  - 330
Mainboard : Intel Corporation DP965LT
Total Memory : 1014MB

Chipset 1
Model : Intel Corporation ??? (29A0)
Front Side Bus Speed : 4x 266MHz (1064MHz data rate)

Video System
Adapter : NVIDIA GeForce 7600 GS


Physical Storage Devices
Removable Drive : Floppy disk drive
Hard Disk : WDC WD2500JS-22NCB1 (233GB)
CD-ROM/DVD : LITE-ON DVDRW SHW-160P6S (CD 48X Rd, 48X Wr) (DVD 6X Rd, 6X Wr)
CD-ROM/DVD : LITE-ON DVD SHD-16P1S (CD 48X Rd) (DVD 6X Rd)

Logical Storage Devices
Hard Disk (C: ) : 233GB (159GB, 68% Free Space) (NTFS)
3.5" 1.44MB (A: ) : N/A
Removable Drive (F: ) : N/A
Removable Drive (G: ) : N/A

Network Services
Adapter : NETGEAR WG311v3 802.11g Wireless PCI Adapter
Adapter : Intel(R) 82566DC Gigabit Platform LAN Connect

What piece of hardware in this configuration could cause ubuntu to fail and what is the support status of it? Thanks in advance.

---

### Post by Old Pink on 2006-10-19
Try downloading the "alternate CD image".

Or, tell me exactly what disc you are using. Is it a Live CD? Did it come through the post? Did you make it yourself? How did you get the .iso on the CD?

---

### Post by telepheedian on 2006-10-19
I was using a standard dapper drake 32bit disc that I burned myself, and I know that it was good because I used the same image for a VM. Other distributions give me this problem as well. I used nero to burn the disc as an image and I know I did it properly, it is when ubuntu actually initializes that I have problems.

---

### Post by doobit on 2006-10-19
Installing from DVD drives seems to be a problem on some systems. It was on mine. I had to put a regular, old CDROM drive in for it to install properly.

---

### Post by telepheedian on 2006-10-19
Could it be my SATA controller? I have used dvd drives for ubuntu installs before and have had no problem yet.

---

### Post by az on 2006-10-19
> **telepheedian said:**
> My computer cannot detect the cd in the ubuntu installer. What hardware from my computer would be disallowing this? 

Is your bios set to boot from the cdrom first?

Your bios should have a "boot order" setting.  Make sure it tries to boot from the cdrom before it tries to boot from the hard drive.

---

### Post by Old Pink on 2006-10-19
If that fails, try the alternate (non GUI) CD. :)

---

### Post by Henry Rayker on 2006-10-19
I had some trouble using nero. It could have been my older version, but I preferred Alcohol 120% anyway...

---

### Post by telepheedian on 2006-10-19
I think that my problem is different. When it is actually time for the kernel to initialize, the boot messages indicate that the system could not find the CD. I think that this has to do with linux drivers in general, as knoppix gives me the same error. I know that my cd is correctly burned and it does get to the ubuntu boot selection screen.

---

### Post by louieb on 2006-10-19
Hit escape when you get to the installation menu. try using the nopic and nolapic kernel options. I know what you mean I have one computer that it is really hit or miss getting it to load Linux from CD. I can get it to boot to DSL, Slackware, and Ubuntu 5. But I never could get Ubuntu 6, xubuntu 6, Zenwalk, Puppy and a host of other distros to boot.

I am suprised that your machine is having the same problem as mine since this computer is a P1 200 128 mb and was built in the early 90's.

I had another machine that would not boot to any CD unless i took out the PCI USB card. Go figure.

---

