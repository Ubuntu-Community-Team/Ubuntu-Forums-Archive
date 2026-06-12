---
title: "Cannot get usbmount to mount my FAT32 stick(s)..."
date: 2018-10-22
forum: General Help
---

### Post by desdan on 2018-10-22
After adding the universe repo with sudo add-apt-repository universe I was able to install usbmount to my Ubuntu 18.04 server.  Unfortunately I am unable to mount my FAT32 sticks (that worked just fine under 14.04).   I get the following in the syslog

Oct 22 18:02:41 vstreamer kernel: [ 2037.396824] usb 1-7: new high-speed USB device number 10 using xhci_hcd
Oct 22 18:02:41 vstreamer kernel: [ 2037.545709] usb 1-7: New USB device found, idVendor=0781, idProduct=5530
Oct 22 18:02:41 vstreamer kernel: [ 2037.545715] usb 1-7: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Oct 22 18:02:41 vstreamer kernel: [ 2037.545719] usb 1-7: Product: Cruzer
Oct 22 18:02:41 vstreamer kernel: [ 2037.545723] usb 1-7: Manufacturer: SanDisk
Oct 22 18:02:41 vstreamer kernel: [ 2037.545727] usb 1-7: SerialNumber: 20044317220F04613918
Oct 22 18:02:41 vstreamer kernel: [ 2037.546308] usb-storage 1-7:1.0: USB Mass Storage device detected
Oct 22 18:02:41 vstreamer kernel: [ 2037.546669] scsi host6: usb-storage 1-7:1.0
Oct 22 18:02:42 vstreamer kernel: [ 2038.565714] scsi 6:0:0:0: Direct-Access     SanDisk  Cruzer           1.00 PQ: 0 ANSI: 2
Oct 22 18:02:42 vstreamer kernel: [ 2038.566361] sd 6:0:0:0: Attached scsi generic sg1 type 0
Oct 22 18:02:42 vstreamer kernel: [ 2038.566978] sd 6:0:0:0: [sdb] 31250432 512-byte logical blocks: (16.0 GB/14.9 GiB)
Oct 22 18:02:42 vstreamer kernel: [ 2038.567909] sd 6:0:0:0: [sdb] Write Protect is off
Oct 22 18:02:42 vstreamer kernel: [ 2038.567914] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
Oct 22 18:02:42 vstreamer kernel: [ 2038.568141] sd 6:0:0:0: [sdb] No Caching mode page found
Oct 22 18:02:42 vstreamer kernel: [ 2038.570186] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Oct 22 18:02:42 vstreamer kernel: [ 2038.577882]  sdb: sdb1
Oct 22 18:02:42 vstreamer kernel: [ 2038.578888] sd 6:0:0:0: [sdb] Attached SCSI removable disk
Oct 22 18:02:42 vstreamer usbmount[3815]: /dev/sdb does not contain a filesystem or disklabel
Oct 22 18:02:42 vstreamer systemd-udevd[3801]: Process '/usr/share/usbmount/usbmount add' failed with exit code 1.
Oct 22 18:02:43 vstreamer usbmount[3840]: executing command: mount -tvfat -osync,noexec,nodev,noatime,nodiratime /dev/sdb1 /media/usb0
Oct 22 18:02:43 vstreamer kernel: [ 2038.973300] FAT-fs (sdb1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
Oct 22 18:02:43 vstreamer usbmount[3840]: executing command: run-parts /etc/usbmount/mount.d

Any advice to resolve this situation would be greatly appreciated! usbmount is an important part of my product distro and we are upgrading to 18.04 for many great reasons...

---

### Post by desdan on 2018-10-23
Looks like no one has any advice - I have tried other things, but to no avail.  I will start a new thread with a different perspective...

---

### Post by desdan on 2018-10-24
I've given up on pmount.  There is a new version of USBMount available here: 
[https://github.com/rbrito/usbmount](https://github.com/rbrito/usbmount)[https://github.com/rbrito/usbmount](https://github.com/rbrito/usbmount)
This resolves the issues with USBMount and Ubuntu 18.04.   This is NOT  the version you will get when you add universe to your repositories and  apt-get it.  You will need to build and install this manually.  Instructions are on the github page.

---

