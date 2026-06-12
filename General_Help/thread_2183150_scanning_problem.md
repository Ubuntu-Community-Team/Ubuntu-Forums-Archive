---
title: "scanning problem"
date: 2013-10-23
forum: General Help
---

### Post by dovah on 2013-10-23
Hello!
 I have a problem with my scanner, it used to work on my system (Ubuntu 12.04 LTS), now it isn't responding to scan. 

It's a usb-printer/scanner - Canon MP282 (yes, I've tried different usb ports, to uninstall/reinstall the printer, but some errors appear while trying to scan from GUI (XSane, or Sane-pgtk) and from terminal (running the command scanimage). Apparently, when running the find-scan command, it is there, however I post the code for further informations.

```
dovah@AsusX501A:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04a9, product=0x1746) at libusb:003:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

dovah@AsusX501A:~$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).


```

Thank you in advance for your help.

---

### Post by dovah on 2013-10-23
That's ok, I answered my question by checking the rep ```
sudo add-apt-repository ppa:michael-gruz/canon-trunk
```, then followed the instuctions and found the MP280series-64 package. It seemed that my reps were out of date! 

Sorry for the question.

Have a nice day everyone!

---

