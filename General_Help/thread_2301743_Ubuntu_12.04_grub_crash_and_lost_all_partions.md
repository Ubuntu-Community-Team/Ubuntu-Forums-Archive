---
title: "Ubuntu 12.04 grub crash and lost all partions"
date: 2015-11-05
forum: General Help
---

### Post by sjz on 2015-11-05
Dear everyone

My computer just crashed last night and I got a grub terminal after I restart my computer this morning. I tried to repair it with the suggestion I found online with no success as the primary drive with the OS is not recognised by the system. I took the hard drive (3TB Seagate drive) out and put it in a different computer. All I can see from the disk utility is the drive is of unknown type with only 4GB size on it. The drive is at /dev/sdc, but there is not /dev/sdc1, dev/sdc2 ... partitions. I previously have about 4 partitions on it, e.g. /home /boot/ /swap ... At the moment I cannot access any data on it. Would you be able to suggest anything to help recovering the data? 

I used "sudo parted -l" and received following message:

Error: /dev/sdc: unrecognised disk label                                  
Warning: Error fsyncing/closing /dev/sdc: Input/output error     

Thanks in advance.

Regards,
Jie

---

