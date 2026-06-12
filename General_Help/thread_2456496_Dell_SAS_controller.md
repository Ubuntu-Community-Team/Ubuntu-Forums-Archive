---
title: "Dell SAS controller"
date: 2021-01-12
forum: General Help
---

### Post by Phil Binner on 2021-01-12
I recently set up a network, with much help from this forum.  Now it is working I need to take it forward, and my next big task is setting up the live system with long term storage.  

I have purchased a couple of second hand 4TB enterprise disks which I intend to set up as a mirrored in a raid 1 cluster.  To connect these I have purchased a second hand Dell raid controller PCI card.  The card is a Serial-Attached SCSI 6/iR Model UCS-61.

Reading the manual for the card there are instructions for installing the drivers for Redhat and OpenSuse, but nothing for Ubuntu or Debian.  The card is fairly old so I hoped the drivers might just appear on installation, but no such luck.  I inserted card and disks and installed XUbunto 20.04 from scratch, but nothing is recognised.

If necessarry I could install OpenSuse instead of XUbuntu, but I am not an expert and OpenSuse would just be one more variable.

Any suggestions please.

---

### Post by SeijiSensei on 2021-01-13
Let's start by making sure the card is recognized. Is it listed if you run "lspci" in a terminal?

I've not used a Dell with an outboard card. I have built servers on Dells with an embedded controller. Usually these either use LSI Logic controllers or ones from Intel. The LSI Logic ("Symbios" or "SAS") devices are supported natively in the Linux kernel. On the server with that device, the RAID1 array appears simply as /dev/sda. My little T30 with an Intel card is not running in RAID mode. I use mdadm for that.

If you have a SAS card, you can try forcing the driver to load with
```
sudo modprobe mptsas
```
"modprobe -v" will produce more verbose output.

---

