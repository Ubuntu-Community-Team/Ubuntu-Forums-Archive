---
title: "xsane and Epson Perfection 4180 Scanner"
date: 2008-05-31
forum: General Help
---

### Post by hamdev on 2008-05-31
I have an Epson Perfection 4180 Scanner which is not directly supported in Ubuntu, but is included in libsane-extras as part of epkowa. I could find install/configure instructions specific to the 4180, but was able to adapt the instructions Howto: Setup the CX6600 on Ubuntu Edgy at [http://ubuntuforums.org/showthread.php?t=316961&highlight=scanner](http://ubuntuforums.org/showthread.php?t=316961&highlight=scanner).

The file 45-libsane.rules must be replaced with 025_libsane-extras.rules,
usb 0x4b8 0x813 is replaced with usb 0x04b8 0x0118, and epson.conf with epkowa.conf.

Before I made the configuration changes listed above, whenever I started xsane, it could not find a scanner. With these changes, it finds a scanner. However, when I press the Scan or the Acquire Preview button, a message dialog pops up saying Failed to start scanner: Invalid argument.

To me, this is a useless message because I cannot determine what argument they are referring to.

sane-find-scanner returns:
found USB scanner (vendor=0x04b8 [EPSON], product=0x0118 [EPSON Scanner]) at libusb:004:004

scanimage -L returns:
No scanners were identified. If you were expecting something different,...


The syslog file contains the following entries when I start xsane:
May 31 09:45:33 jimpc kernel: [  187.355416] ppdev0: registered pardevice
May 31 09:45:33 jimpc xsane: io/hpmud/pp.c 627: unable to read device-id ret=-1 
May 31 09:45:33 jimpc kernel: [  187.404834] ppdev0: unregistered pardevice
May 31 09:45:34 jimpc kernel: [  187.784474] ppdev0: registered pardevice
May 31 09:45:34 jimpc kernel: [  187.785272] ppdev0: unregistered pardevice

Can someone point me to what is wrong or what I am not doing correctly?

---

### Post by phidia on 2008-05-31
Just a thought-have you tried to issue scanimage -L with sudo to see if your permissions are the problem?

---

### Post by hamdev on 2008-06-02
scanimage -L returns device `epson:libusb:004:004' is a Epson  flatbed scanner

with the scanner turned on, with or without sudo.  xsane still producing invalid argument message, and writing same syslog entries.

---

