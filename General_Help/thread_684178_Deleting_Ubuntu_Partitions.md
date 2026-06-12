---
title: "Deleting Ubuntu Partitions"
date: 2008-01-31
forum: General Help
---

### Post by dtritle on 2008-01-31
I am absolutely clueless when it comes to Linux so I might just being dumb but I have 120GB ide HDD the ubuntu was installed on.  I have since replaced that drive and I am now trying to completely format the drive for uses as a secondary drive in windows.  I can see the drive in windows but it only shows up as a 31GB drive.  

I am assuming that it is not seeing some of the ubuntu partitions so after some searching I tried to run gparted to delete them.  It does not even see the drive, it shows all my sata drive (2X250 raid0 and 1X320 eSata).

How can I make windows see all 120GB of this drive without using Linux?

---

### Post by imtheguru on 2008-01-31
> **dtritle said:**
> ... 120GB ide HDD the ubuntu was installed on.

How can I make windows see all 120GB of this drive without using Linux?Why such limiting conditions? Use the livecd!

Install gparted and use it to remove the partitions from the 120GB drive. Do not touch the drives in your raid or disconnect them from the computer temporarily.

Cheers.

---

### Post by tgrimley on 2008-01-31
How are you approaching this in Windows? If you go to computer management and look under disk management it should show you the whole disk and its partitions even if Windows can't read them.  From there you can delete all partitions and repartition and format.

---

### Post by dtritle on 2008-01-31
OK, so I ran the livecd and installed gparted...it showed the whole drive (120GB) as unallocated, so I formatted the entire drive as fat32 thinking if it is a problem with windows just now seeing it that should fix it.  I restarted into windows and it show the drive as unallocated and as 31GB still.  

I have tried disk management and it also only sees 31GB.  Is it possible there is something wrong with the drive?

---

### Post by tgrimley on 2008-02-01
> **dtritle said:**
> OK, so I ran the livecd and installed gparted...it showed the whole drive (120GB) as unallocated, so I formatted the entire drive as fat32 thinking if it is a problem with windows just now seeing it that should fix it.  I restarted into windows and it show the drive as unallocated and as 31GB still.  

I have tried disk management and it also only sees 31GB.  Is it possible there is something wrong with the drive?

There is a 32GB limit on FAT32 partitions under Windows in some circumstances.  Perhaps a screenshot of your disk management screen would be helpful?

Maybe leave it unformatted and unpartitioned and do the partitioning and formating under windows?

---

