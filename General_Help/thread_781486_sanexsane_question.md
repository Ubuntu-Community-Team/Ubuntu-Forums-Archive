---
title: "sane/xsane question"
date: 2008-05-04
forum: General Help
---

### Post by Damanther on 2008-05-04
I have one of those Epson all in one printer/scanners. I've been printing with it for a while now successfully with the gutenprint drivers. I just recently started trying to get the scanner portion to work. 

When I run sane-find-scanner I see this:
found USB scanner (vendor=0x04b8 [EPSON], product=0x083c [USB2.0 MFP(Hi-Speed)]) at libusb:002:004
found USB scanner (vendor=0x046d, product=0x08b5) at libusb:001:007

When I run 'scanimage -L' I get the following which looks correct:
device `v4l:/dev/video1' is a Noname Hauppauge HVR-1600 virtual device
device `v4l:/dev/video0' is a Noname Logitech QuickCam Orbit virtual device
device `epkowa:libusb:002:004' is a Epson PM-A840 flatbed scanner

But when I run xsane or kooka, the only devices it lists are the two v4l devices which are my tuner and webcam respectively.

Anyone have an idea what is missing to get xsane to work? Or even Kooka?

---

### Post by Damanther on 2008-05-05
FYI for anyone else that runs onto this. This device seems to work fine when the scanimage/sane-find-scanners/kooka/xsane are run as root. I'm still working on why this is the case. It wasn't as simple as the permissions on the /dev/bus/usb files.

---

