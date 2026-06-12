---
title: "How to boot from live cd"
date: 2014-11-14
forum: General Help
---

### Post by hop5uk on 2014-11-14
Can anyone tell me how to boot from either the live CD or recovery mode when ubuntu refuses to boot?

---

### Post by hop5uk on 2014-11-14
Any other method will also suffice!

---

### Post by Bucky Ball on 2014-11-14
Enter your BIOS and make the USB or disk your first boot device. Most machines also allow you to press F12 at boot and choose a boot device.

You be better off telling us what is happening when 'Ubuntu refuses to boot' and fixing that, unless you want to boot from Live media cos you already have some idea and want to take a closer look. 

Good luck. ;)

---

### Post by hop5uk on 2014-11-14
I can easily boot into the live USB and get into terminal-Its what to do then that i have the problem with.
Sequence of boot is:
1. BIOS splash screen ( I am able to go into the Bios if neccessary)
2. Controller card BIOS screen ( I am also able to go into this Bios if neccessary)
3. GNU Grub screen. This gives me the choice of:
    Ubuntu, with Linux 3.2.0-29-generic
    Ubuntu, with Linux 3.2.0-29-generic (recovery mode)
    Memory test (memtest86+)
    Memory test (memtest86+, serial console 115200)
At this point i leave the pc to chose the first selection as normal but  then the screen just goes blank and nothing else happens. That is as far as it goes

---

### Post by QIII on 2014-11-14
Hello!

Can you tell us the hardware specifications of your machine?

---

### Post by hop5uk on 2014-11-14
ASUS P8Z68-V LX, IBM Serveraid M1015 SAS/SATA  Controller, 2x 64Gb Kingston SSD Now V Series (SW Raid1), 4x Seagate  Barracuda 3 TB 7200RPM SATA 6 Gb/s (SW Raid 5), 2x Western Digital  Caviar Green 2TB 5400RPM SATA 3.0Gbps 64MB Cache 3.5" & 1x Hitachi  GST Deskstar 7K2000 (0F10311) 2TB 7200 RPM 32MB Cache SATA 3.0Gb/s 3.5"  (SW Raid 5), 4x Seagate Barracuda 7200.11 1.5TB 7200 RPM 32MB Cache SATA  3.0Gb/s 3.5" (SW Raid 5), Thermaltake TR2-600W, Coolermaster Centurion  590 Case

i am running Ubuntu 12.04.2 LTS using command line only. My disk set up is:
1) 2 x 64GB SSD disks configured in Raid 1 and running the Op Sys.
2) 4 x 3000GB disks in Raid 5 for storage
3) 3 x 2000GB disks in Raid 5 for storage
4) 4 x 1500GB disks in Raid 5 for storage
Arrays 1) and 4) are plugged into the motherboard SATA ports.
Arrays 2) and 3) are plugged into the an IBM m1015 controller card.
I am using mdadm for SW control of all arrays.

---

