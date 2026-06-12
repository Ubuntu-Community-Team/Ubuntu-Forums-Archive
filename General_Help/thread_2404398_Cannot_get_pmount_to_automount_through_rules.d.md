---
title: "Cannot get pmount to automount through rules.d"
date: 2018-10-23
forum: General Help
---

### Post by desdan on 2018-10-23
I'm running Ubuntu 18.04. 

Based on advice, I have switched to pmount from usbmount and added an automount.rules into /etc/udev/rules.d

pmount works manually just fine (e.g. pmount -t vfat -umask 000 /dev/sda1), ***however*** - it will not work in the automount rules.

The action line for mounting in automount.rules looks like this:

ACTION=="add", KERNEL=="sd[b-z]*", RUN+="'/usr/bin/pmount -t vfat --umask 000 %k'"

And although I have tried lots of various syntax - it either never mounts or errors out with this

Oct 23 15:35:01 vstreamer systemd-udevd[4689]: Process '/usr/bin/pmount -t vfat --umask 000 sdb' failed with exit code 5.

It does create /media/sdb1 as the mount point, but never mounts the drive.

Below is the output of syslog...
******************************************
Oct 23 18:41:12 vstreamer kernel: [16543.359659] usb 3-9: new high-speed USB device number 38 using xhci_hcd
Oct 23 18:41:13 vstreamer kernel: [16543.508293] usb 3-9: New USB device found, idVendor=0781, idProduct=5406
Oct 23 18:41:13 vstreamer kernel: [16543.508295] usb 3-9: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Oct 23 18:41:13 vstreamer kernel: [16543.508296] usb 3-9: Product: U3 Cruzer Micro
Oct 23 18:41:13 vstreamer kernel: [16543.508297] usb 3-9: Manufacturer: SanDisk
Oct 23 18:41:13 vstreamer kernel: [16543.508298] usb 3-9: SerialNumber: 1738811618C2524A
Oct 23 18:41:13 vstreamer kernel: [16543.508653] usb-storage 3-9:1.0: USB Mass Storage device detected
Oct 23 18:41:13 vstreamer kernel: [16543.508871] scsi host7: usb-storage 3-9:1.0
Oct 23 18:41:14 vstreamer kernel: [16544.512060] scsi 7:0:0:0: Direct-Access     SanDisk  Cruzer           8.02 PQ: 0 ANSI: 0 CCS
Oct 23 18:41:14 vstreamer kernel: [16544.512246] sd 7:0:0:0: Attached scsi generic sg1 type 0
Oct 23 18:41:14 vstreamer kernel: [16544.512684] sd 7:0:0:0: [sdb] Attached SCSI removable disk
Oct 23 18:41:14 vstreamer systemd-udevd[11152]: Process '/usr/bin/pmount -t vfat --umask 000 --noatime sdb' failed with exit code 5.
Oct 23 18:41:14 vstreamer kernel: [16545.276896] sd 7:0:0:0: [sdb] 15704063 512-byte logical blocks: (8.04 GB/7.49 GiB)
Oct 23 18:41:14 vstreamer kernel: [16545.278784]  sdb: sdb1
Oct 23 18:41:36 vstreamer kernel: [16567.348706] FAT-fs (sdb1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.

---

### Post by desdan on 2018-10-24
I've given up on pmount.  There is a new version of USBMount available here: 
[https://github.com/rbrito/usbmount](https://github.com/rbrito/usbmount)[https://github.com/rbrito/usbmount](https://github.com/rbrito/usbmount)
This resolves the issues with USBMount and Ubuntu 18.04.   This is NOT the version you will get when you add universe to your repositories and apt-get it.  You will need to build and install this manually. Instructions are on the github page.

---

