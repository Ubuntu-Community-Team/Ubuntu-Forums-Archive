---
title: "Cannot find Canon All-in-one even though pixma is enable in sane back end list."
date: 2014-01-15
forum: General Help
---

### Post by dyndase on 2014-01-15
Cannot find Canon All-in-one MG3150, even though pixma is enable in sane back end list.

```
sudo sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.
  # Also you need support for SCSI Generic (sg) in your operating system.
  # If using Linux, try "modprobe sg".

  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.


```

According to SANE website, my Canon MG3150 is listed in pixma back end which is not commented in the dll config.

```
lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 012: ID 05e3:0727 Genesys Logic, Inc. microSD Reader/Writer
Bus 001 Device 005: ID 0781:5571 SanDisk Corp. Cruzer Fit
Bus 001 Device 009: ID 0489:e056 Foxconn / Hon Hai 
Bus 001 Device 003: ID 1bcf:2c67 Sunplus Innovation Technology Inc. 
Bus 001 Device 011: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 020: ID 04a9:1752 Canon, Inc. 
Bus 001 Device 008: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 007: ID 04b4:0033 Cypress Semiconductor Corp. Mouse
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

**NOTE: sane-find-scanner cannot check the usb of Printer without sudo**

I am using Xfce + Saucy on Crouton, and I can print via CUPS.
I installed the official scanner driver from Canon too, but it is not automatically working.

I run scangearmp, still the system cannot find the scanner (in the All-in-one Canon).
When I run sudp scangearmp, the system detect the scanner, but the program will always freeze.

Can anyone please help me ? :<

---

