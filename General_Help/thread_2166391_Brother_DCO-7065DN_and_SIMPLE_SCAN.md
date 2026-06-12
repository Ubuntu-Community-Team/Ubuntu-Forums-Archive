---
title: "Brother DCO-7065DN and SIMPLE SCAN"
date: 2013-08-09
forum: General Help
---

### Post by sureshsaragadam on 2013-08-09
I am able to print and scan with Brother DCP-7065DN

But, each time i use a simple scan app to scan i need to set the preferences of scan source to one of the brother printers, even though i have only one scanner and printer.

output of the following commmand > sane-find-scanner 

[HTML]

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04f9, product=0x024a) at libusb:002:005
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
[/HTML]


> scanimage -L

[HTML] device `brother4:net1;dev0' is a Brother DCP-7065DN DCP-7065DN
device `brother4:bus1;dev1' is a Brother DCP-7065DN USB scanner
[/HTML]

by default the Usb Scanner is not getting selected by 'Simple Scan'

how do i set USB Scanner as a defalut scanner for simple scan application

---

