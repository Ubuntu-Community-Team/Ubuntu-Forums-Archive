---
title: "How to allow user using usb device"
date: 2019-03-19
forum: General Help
---

### Post by satimis on 2019-03-19
Hi all,

On running;

&#10219; sane-find-scanner```


  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

could not open USB device 0x1d6b/0x0002 at 003:001: Access denied (insufficient permissions)
......

```

&#10219; cat /etc/group | grep usb
No printout

&#10219; cat /etc/group | grep tty```

tty:x:5:

```

Please advise how to allow satimis using usb device?  Thanks

Regards
satimis

---

### Post by jdeca57 on 2019-03-19
I'm a bit hesitant to write this because of your huge number of beans but why didn't you use sudo if you have a permissions problem? "cat /etc/group | grep usb" gives no output on my system yet I'm certainly using my usb.

---

### Post by satimis on 2019-03-19
> **jdeca57 said:**
> I'm a bit hesitant to write this because of your huge number of beans but why didn't you use sudo if you have a permissions problem? "cat /etc/group | grep usb" gives no output on my system yet I'm certainly using my usb.
Hi,

I have been working for more than an hour and couldn't figure out my problem

My Epson scanner works on Simple Scan scanning photos but it can't work on XSane


&#10219; sudo sane-find-scanner```


  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8 [EPSON], product=0x0122 [EPSON Scanner]) at libusb:001:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

```

&#10219; scanimage -L```

device `snapscan:libusb:001:004' is a EPSON EPSON Scanner1 flatbed scanner

```
Then the device is found.  But if running sane-find-scanner without sudo, scanimage -L is just hanging.

But it is NOT good to run sane-find-scanner as root

I'm now finding a way how to give permission to user("satimis" in my case) to use the USB device

Regards
saimit

---

