---
title: "Trying to get a canoscan N650U  working"
date: 2014-01-24
forum: General Help
---

### Post by pouldney on 2014-01-24
Post to forum

   I am trying to get a canoscan N650U scanner working 
 on a Acer AXC-605  with ubuntu 12.04    3.8.0-35-generic

 sane-find-scanner command finds two scanners
 the one at libusb:003:004  is actualy a Realtek multi card reader
 not a scanner

  My scanner works only occasionally
 Perhaps this is why?
  
Any help appreciated


george@george-Aspire-XC-605:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04a9 [Canon], product=0x2206 [CanoScan]) at libusb:003:007
found USB scanner (vendor=0x0bda, product=0x0129) at libusb:003:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

---

### Post by ibjsb4 on 2014-01-25
This isn't much, but my findings ..

Yes you are right, "vendor=0x04a9 [Canon], product=0x2206" looks to be the one.  Its under "Plustek 0.52" and says to be complete.

[http://www.sane-project.org/cgi-bin/driver.pl?manu=canon&model=CanoScan+n650u&bus=any&v=&p=](http://www.sane-project.org/cgi-bin/driver.pl?manu=canon&model=CanoScan+n650u&bus=any&v=&p=)

I didn't find anything recent on it, but did find a dated install method that may or may not still work.

[http://myubuntublog.wordpress.com/2009/05/27/scanner-support/](http://myubuntublog.wordpress.com/2009/05/27/scanner-support/)

And if all else fails, VueScan.

[http://ubuntuforums.org/showthread.php?t=1649025&p=12079698#post12079698](http://ubuntuforums.org/showthread.php?t=1649025&p=12079698#post12079698)

Not much, but I thought I would share this with you.  Good Luck

---

