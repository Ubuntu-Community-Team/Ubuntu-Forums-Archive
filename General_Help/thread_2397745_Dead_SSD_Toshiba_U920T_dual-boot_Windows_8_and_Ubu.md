---
title: "Dead SSD? Toshiba U920T dual-boot Windows 8 and Ubuntu 18.04"
date: 2018-08-02
forum: General Help
---

### Post by balkon16 on 2018-08-02
Hi, 

 I'm experiencing some boot problems. On starting my laptop I get a  boot error: "Insert system disk in drive. Press any key when ready....".  

  
I decided to run Live Ubuntu session (version 18.04). I strongly  believe that the SSD that both operating systems are installed on is  dead. Before I buy a new one I want to make sure that the SSD is  definitely dead and there is no way to make it work again.


  boot-repair output [http://paste.ubuntu.com/p/yXN7YpdJ7Y/](http://paste.ubuntu.com/p/yXN7YpdJ7Y/) As you can see there are only temporary partitions recognized and USB-stick which I'm running session from.
 There are no partitions visible apart from USB-stick (last entry below 7.2GB) (fdisk -l starts in line 272. gnome-disks tells me that there's only USB-stick and loop drive.

---

### Post by Autodave on 2018-08-02
Sounds like the drive has failed. Have you checked the connections to make sure that they haven't come loose?  That does happen.

When you boot from the USB stick and the main screen comes up: is the icon for the onboard hard drive visible?

---

