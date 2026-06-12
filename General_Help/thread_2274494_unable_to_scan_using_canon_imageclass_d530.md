---
title: "unable to scan using canon imageclass d530"
date: 2015-04-20
forum: General Help
---

### Post by pancho45 on 2015-04-20
manuel@manuel-HP-Pavilion-dv7-Notebook-PC:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

could not open USB device 0x04a9/0x2775 at 002:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 002:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 006:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 005:001: Access denied (insufficient permissions)
could not open USB device 0x0408/0x03f0 at 001:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 001:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 004:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 003:001: Access denied (insufficient permissions)
  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
No
Printing is no problem but when i try to scan using simple scan i get this message:Failed to scan.xsaneNo scanners available.Please connect a scanner.
I tried xsane image and got this message:no device available.Is there a scanner driver i need to install?I tried canon.com but only driver avaiable is for printing.Thanks.

---

### Post by pdc on 2015-04-20
the standard release of sane does not support this device; the good news is the development release does;

to get it, one adds the ppa of sane that the development team looks after; it is the Rolf Bensch ppa

here is a thread about how to do it [http://forums.linuxmint.com/viewtopic.php?f=51&t=194081&p=1006693&hilit=rolf+bensch#p1006693](http://forums.linuxmint.com/viewtopic.php?f=51&t=194081&p=1006693&hilit=rolf+bensch#p1006693)

please let us know how it goes

______________

the person in that thread had a wireless connect; so the config file also needed updating: I am guessing you have usb cable so all should be good there

---

### Post by pancho45 on 2015-04-30
scanningggggggggggggg!!!!!!!!!!!!!!!!!!!!!!!!Thank you very much!!!!!!!!!!!!!!!!!!!!!!

---

