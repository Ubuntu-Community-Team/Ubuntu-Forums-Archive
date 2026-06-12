---
title: "BEST Ubuntu PARTITION MANAGER"
date: 2013-06-08
forum: General Help
---

### Post by vanquish2012 on 2013-06-08
I have WIN 8 on a 2nd partition on my laptop next to Ubuntu 12.04 on another partition and want to re-size my 320 Gb HDD to allow UBUNTU on the HDD ONLY and get rid of WINDOWS 8.

Right now, UBUNTU occupies 200 Gb on one partition and WIN 8 occupies apx 100Gb on a second partition.

Is there an easy and effective way *to allow UBUNTU to occupy my ENTIRE 310 Gb HDD on one partition*?

Thank you.

---

### Post by critin on 2013-06-08
(One way out of others is the way I choose to do it)  Save personal files, pics, etc on flash drive and reinstall ubuntu.  At the point where it asks you where to install, choose 'erase and use entire disk'.

---

### Post by ahallubuntu on 2013-06-08
~

---

### Post by Ron O on 2013-06-08
Get Parted Magic   [http://download.cnet.com/Parted-Magic/3000-2094_4-10663999.html](http://download.cnet.com/Parted-Magic/3000-2094_4-10663999.html)  and create the live CD. 

Now boot from the CD and you can do anything you want, like delete the Windows partition then expand the Ubuntu partition to consume the unallocated space. I have used this partition tool dozens of times to do all kinds of things and never corrupted a single file. It is just GParted runnig from the CD (and memory) so all your HD partitions are unmounted and you can work on them. When you drag partition boundries in the GUI, just remember that the operation is not done until you hit the Apply button.

One MAJOR CAUTION. Make sure the GRUB boot loader was not installed on the Windows partition or you will be locked out of your system when you delete it then reboot. I think you can prevent this by doing an "Install GRUB" from terminal while in Ubuntu before using PartedMagic. There is also a linux boot repair live CD out there you might want to download and have on hand just in case. The GRUB gurus can help you with this- just be sure you know exactly where this boot loader resides before you delete the Windows partition. 

Good luck getting a permanent divorce from Windoze!

---

