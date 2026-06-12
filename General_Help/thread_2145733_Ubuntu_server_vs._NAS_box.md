---
title: "Ubuntu server vs. NAS box"
date: 2013-05-16
forum: General Help
---

### Post by zen83 on 2013-05-16
I am deciding between a Qnap 4 bay NAS box or Ubuntu Server to fulfill needs for:

[LIST]
[*]Creating a large fault tolerant RAID array with SMB shares
[*]Media serving to desktop and Western Digital TV Live
[*]torrent, ftp and perhaps other remote file services
[*]Network services (DHCP, firewall, etc.)...total replacement of a dd-wrt wireless router would be nice
[/LIST]

It looks to me like the Qnap device will do about 90% of what I want, but of course, they are not cheap, upgradable, or expandable. I also worry that even the higher end model with a 2.0 GHz ARM CPU and 512MB of memory will be overloaded with all the roles I want to implement. But, they do look very simple to administer, and time is money too. 

Here is the hardware I have now for an Ubuntu server:
[LIST]
[*]mATX case with 300w SeaSonic bronze PSU, 6x 3.5" bays and 2x 5.25" bays
[*]AMD Athlon II X2 250 (3.0 GHz dual core)
[*]ECS AM2+ mATX board with 4GB DDR2 memory (effective max due to cost), 6x SATA II headers, 1x PATA header, 16x PCIe, 1x PCIe, 2x PCI, integrated video
[*]2x Intel Pro/1000 PCI NICs, single port (each)
[*]3x 120GB SATA hard disk for testing
[/LIST]

Anyway, I am just wondering if Ubuntu server might be the right OS for me considering the needs, and whether my hardware is suitable (minus hard disk, but I don't want to invest in 3TB disk or a hardware RAID controller until I know this will work).

---

### Post by Bob65536 on 2013-05-16
I have been doing pretty much the same thing with my Ubuntu Server box for years. The only down side is that it takes longer to configure, but you have practically unlimited control.

Your hardware looks fine. Rather than using hardware raid, I use btrfs.

---

### Post by tgalati4 on 2013-05-16
Check the power consumption of both options and your electric rates.  The QNAP box may be cheaper after 3 years of use.  RAID array may not be helpful if you use green drives that spin down frequently.

---

### Post by 2F4U on 2013-05-16
> Anyway, I am just wondering if Ubuntu server might be the right OS for  me considering the needs, and whether my hardware is suitable (minus  hard disk, but I don't want to invest in 3TB disk or a hardware RAID  controller until I know this will work).


If you look at the hardware of a typical NAS, you will realize that your hardware is superior to the NAS. But as already said, what makes the difference is power consumption, especially if you are planning to run the device over extended periods of time, e. g. 24 hours a day. I doubt that the PC will be as power efficient as a NAS.

---

### Post by tgalati4 on 2013-05-16
What you want is both.  (1) NAS running 24/7 with green drives that spin down and burns 15 to 25 watts. (2)  A more powerful linux server that burns 100 watts but put to sleep and use wake-on-lan on all of your tablets, phones, and laptops, so you can wake up the linux machine and use its services.  Use a script to back up the linux server to the NAS once a week or so.  This is what I have set up currently, although instead of a QNAP, I built a freenas server using an old, white-box PC with green drives and it burns 35 watts--more than a QNAP, but it was free--literally a curbside PC.

---

