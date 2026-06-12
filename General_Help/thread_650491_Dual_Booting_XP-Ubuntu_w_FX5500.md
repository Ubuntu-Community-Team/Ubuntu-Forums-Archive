---
title: "Dual Booting XP-Ubuntu w/ FX5500"
date: 2007-12-26
forum: General Help
---

### Post by kymagic on 2007-12-26
Hi,
I have a Dell Dimension 2400, which has two drives on it. After getting a new computer for Christmas, the  Dell has been wiped and will be dual booting XP/Ubuntu. I have installed XP on the smaller of the two HDs, and now want to install Ubuntu on the other one. However, after selecting the liveCD/install option from the boot menu, it loads for a bit and complains that it couldn't detect/configure my graphics hardware correctly, and so will be running in low graphics mode (which is understandable; it hasn't got the drivers for it yet). After I click OK, it hangs. The last entry on the loading text list (the name escapes me at the moment) is "Running local boot scripts (/etc/rc.local)". After having a quick google, it turns out that this happens because of a problem with he Nvidia drivers (the case on the net re-installed them to fix the problem). However, I have no Ubuntu to install the drivers on. How am I going to install Ubuntu?

Thanks in Advance.

---

### Post by gilloz on 2007-12-26
Kymagic, I am dual booting with Windows XP Pro and Ubuntu 7.10 and my video card is also an FX-5500.  My set up are two 80GB hard drives (C & D repectively).  My Windows XP is on the C drive with no partitions.  The D drive is partitioned for Ubuntu and my NTFS storage.  40 GB for Ubuntu, 40 GB for storage.  I manually partitioned the D drive 1st 40 GB for Ubuntu during the installation process.  You know, /, /home and swap.  I also manually called out the nvidia driver as fx by selecting System, Administration, Restrictive Drivers Manager, enter root password, then selected the driver.  Have you tried that?

---

### Post by kymagic on 2007-12-26
I can't reach the installation process. It hangs before I even see the desktop of the LiveCD, and so I can't actually start the install wizard. My HD which Ubuntu is on was used for storage recently, so it has a load of rubbish on it. I was going to format it in the installation. My C drive has one partition using all of the space available.

---

### Post by gilloz on 2007-12-26
Try clearing your D drive using Windows Disk Management program in Windows.  That's how I cleared mine prior to installing Ubuntu.  Click on Start, then right click the My Computer icon, then click on Manage and finally click on Disk Management.  You can clear the amount of space needed for your Ubuntu installation.  Be sure that the space is called out as "unallocated space" or "free space".  Don't do anything else, like make an active partition or format this space.  Just leave it as unallocated space.  See if that works for you.

---

### Post by kymagic on 2007-12-27
I cleared the HD. I also selected safe graphics mode from the boot menu instead of letting it do that automatically). It worked! Ubuntu and XP are now happily working side-by-side and I have installed the latest NVidia drivers for the card. Thanks!

---

