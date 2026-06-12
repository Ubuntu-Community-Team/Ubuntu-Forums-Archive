---
title: "sane-find-scanner reports two USB scanner addresses"
date: 2013-03-21
forum: General Help
---

### Post by afrodeity on 2013-03-21
```

sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x043d, product=0x011d) at libusb:002:003
found USB scanner (vendor=0x0c45, product=0x613b) at libusb:002:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
```

```

scanimage -L
device `Lexmarklxdn:libusb/002/003' is a Lexmark 2600 Series Scanner

```

If I run xsane I get this error message:
```

Failed to open device 'Lexmarklxdn:libusb/002/003' invalid argument

```

Do I have to blacklist one of the addresses? How to solve this issue?

---

### Post by afrodeity on 2013-03-24
reinstalled xsane, must have been a problem with the libsane

---

