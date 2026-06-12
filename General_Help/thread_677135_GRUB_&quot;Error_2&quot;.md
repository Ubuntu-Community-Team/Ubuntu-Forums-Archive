---
title: "GRUB &quot;Error 2&quot;"
date: 2008-01-24
forum: General Help
---

### Post by Kbeginner on 2008-01-24
Hello,

I am new to Kubuntu.  I just got a new computer (specs below) which had a formatted HD (no pre-existing OS).  I imaged Gutsy Gibbon and ran the live CD.  Everything worked fine.  I tried 3-4 applications, connected to internet, all worked great and super fast.

I ran install and everything went smoothly.  I rebooted and then it started to run GRUB, got to level 1.5, then simply: "Error 2".  And there the computer sat.

I re-installed, same error, although it continues to run fine from the live CD.

Any thoughts or assistance would be much appreciated.

Here is my set-up:

> AMD X2 6000 AM2 CPU RETAIL
2 160GB SATA-II 3GB/S 8MB 7200RPM HD (2 HDS - run side-by-side)
1G DDR2 PC6400 MEMORY
CM HYPER TX2 GAMING CPU COOLING FAN
BLACK LG 20X DVDRW
BLACK SONY 16X DVD
12-IN-ONE INTERNAL CARD READER
RAID-0 STRIPING
ASUS M2N-E SLI AM2 NFORCE 500
COOLERMASTER 600WATT EXTREME POWER
CREATIVE LABS AUDIGY SE BULK
GEFORCE 8600GT 512MB PCI-E

---

### Post by wolfen69 on 2008-01-24
from here: [http://www.uruk.org/orig-grub/errors.html](http://www.uruk.org/orig-grub/errors.html)  "This error is returned if the device part of a device- or full filename refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system." take alook at your hard drive settings in bios.

---

### Post by Kbeginner on 2008-01-24
Thank you.  When I installed, I let Kubuntu choose the whole HD for installation, but as there are 2, might it be going to the wrong one?

---

### Post by Kbeginner on 2008-01-24
I ran an fdisk from live cd and got this:

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
 255 heads, 63 sectors/track, 19457 cylinders
 Units = cylinders of 16065 * 512 = 8225280 bytes
 Disk identifier: 0x432e17ee
 
 Device Boot Start End Blocks Id System
 /dev/sda1 * 1 18705 150247881 83 Linux
 /dev/sda2 18706 19457 6040440 5 Extended
 /dev/sda5 18706 19457 6040408+ 82 Linux swap / Solaris
 
 Disk /dev/sdb: 160.0 GB, 160041885696 bytes
 255 heads, 63 sectors/track, 19457 cylinders
 Units = cylinders of 16065 * 512 = 8225280 bytes
 Disk identifier: 0x00000000
 
 Disk /dev/sdb doesn't contain a valid partition table

Obviously my partition is messed up.  

Thoughts?

---

### Post by wolfen69 on 2008-01-24
what is on sdb? is it unallocated? (empty)

---

### Post by wolfen69 on 2008-01-24
just for the heck of it, boot the other drive and see what happens.

---

### Post by Kbeginner on 2008-01-24
Yes, other drive totally empty...I will give it a shot...

---

### Post by Kbeginner on 2008-01-24
One problem I see is that in BIOS, it's not even recognizing the Master or Slave drive -- lists them as "none".

I imagine this would cause a problem in booting.

---

### Post by Kbeginner on 2008-01-25
SOLVED:   I disabled RAID in BIOS and it booted right up.  Obviously BIOS was not recognizing the independent HD.  Thanks to all....

---

