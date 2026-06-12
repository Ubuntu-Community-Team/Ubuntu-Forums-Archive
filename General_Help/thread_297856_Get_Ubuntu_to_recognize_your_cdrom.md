---
title: "Get Ubuntu to recognize your cdrom"
date: 2006-11-11
forum: General Help
---

### Post by johnc4510 on 2006-11-11
For all you folks who can't get Ubuntu Edgy to recognize your cdrom, check your /etc/fstab file, and see if the cdrom is listed toward the bottom after your partitions. If not, try this, it worked for me. Open Synaptic and install the proper linux-headers for your kernel. This immediately allowed the system to automount the cdrom, and put the proper lines into the fstab file. Hope it works as good for you.

---

### Post by kweiner on 2006-11-13
I have not been able to get Ubuntu Edgy to install (see [my earlier post]("http://ubuntuforums.org/showthread.php?t=296050")).
Someone advised me to try the alternate CD, and when I did, it couldn't recognize my cdrom.  I can boot off the cdrom just fine, but during installation, it isn't detected.

Do you have any idea how I can get Edgy to detect it during installation?  I have a Dell Dimension 9200c with DVD/CDROM Drive: _NEC DVD+-RW ND-6650A.  The Dapper install CD detects it just fine.  Thanks.

---

### Post by kweiner on 2007-01-30
I finally got things working.  In my BIOS, I changed the value of "SATA Operation" from AHCI (was the default) to ATA.  After that, I could boot from CDs and my Ubuntu installation could recognize my CDROM for the first time!  I have no idea what the "SATA Operation" setting means and whether or not it should have worked set to AHCI, but I'm just glad everything is working now.

---

### Post by KaeseEs on 2007-01-30
kweiner: AHCI is the Advanced Host Controller Interface, SATA is Serial ATA (ATA being a standard drive connecton interface).  In layman's terms, SATA is a standard fast drive interface, AHCI is a competing interface propagated by Intel that apparently we don't yet have drivers for.

---

