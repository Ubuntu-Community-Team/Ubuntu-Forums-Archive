---
title: "Can't find my Canon MG2550 scanner"
date: 2015-10-20
forum: General Help
---

### Post by Envy123 on 2015-10-20
Hi guys. After a system crash on my mother's laptop and finding Windows 8.1 to be very slow, I switched to Ubuntu and the performance is now great. :D

I am, however, having a problem getting the Canon MG2550 PIXMA scanner to detect. It prints fine, but Xsane and SimpleScan both say that they can't detect any scanners.

I try this command:

```
sane-find-scanner
```

And it says that it can't access the USB device because of insufficient permissions.

Any help would be appreciated. :)

---

### Post by Envy123 on 2015-10-21
OK, I can't get this to work.

```
 lsusb 
```: Detects the Canon PIXMA just fine.

When I try ```
 sudo sane-find-scanner 
```

```
  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program. 
```

When I try to install the drivers by using the tar and install.sh commands, I get:

```
ScanGear MP
Version 2.20
Copyright CANON INC. 2007-2013
All Rights Reserved.

==================================================
Command executed = sudo dpkg -iG ./packages/scangearmp-common_2.20-1_amd64.deb
Selecting previously unselected package scangearmp-common.
(Reading database ... 207645 files and directories currently installed.)
Preparing to unpack .../scangearmp-common_2.20-1_amd64.deb ...
Unpacking scangearmp-common (2.20-1) ...
Replaced by files in installed package scangearmp-common-64 (2.10-33~raring1) ...
dpkg: dependency problems prevent configuration of scangearmp-common:
 scangearmp-mg5200series-64 (2.10-33~raring1) breaks scangearmp-common and is installed.
 scangearmp-common-64 (2.10-33~raring1) breaks scangearmp-common and is installed.
 scangearmp-mg2200series-64 (2.10-33~raring1) breaks scangearmp-common and is installed.

dpkg: error processing package scangearmp-common (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 scangearmp-common
Command executed = sudo dpkg -P scangearmp-common
(Reading database ... 207653 files and directories currently installed.)
Removing scangearmp-common (2.20-1) ...
Purging configuration files for scangearmp-common (2.20-1) ...
```

---

### Post by Envy123 on 2015-10-22
Managed to fix it. Just in case someone else has the same problem as I did, here's what I did after re-installing Ubuntu.

I typed:

```
**[B] sudo add-apt-repository ppa:michael-gruz/canon-trunk**
[/B]**[B]sudo apt-get update **[/B]
```I installed the Synaptics Package Manger from the Ubuntu Software Centre and installed the cnijfilter and scangearmp for the MG2550 series. ScangearMP detected the scanner straight away and scans fine now.

Installing directly from the terminal didn't work for some reason as it couldn't find the mg2500series driver. And Canon's Linux drivers didn't make a difference at all.

---

