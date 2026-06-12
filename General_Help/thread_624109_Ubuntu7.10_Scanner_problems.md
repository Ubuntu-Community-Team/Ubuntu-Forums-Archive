---
title: "Ubuntu7.10 Scanner problems"
date: 2007-11-26
forum: General Help
---

### Post by oldcdr on 2007-11-26
My Microtek ScanMaker 4800 flat bed scanner worked perfectly on Ubuntu 7.04.  When I upgraded to 7.10 I got the following error message when I accessed XSane:

Fail to open device 'smb3840:libusb:004:002' Access to resource has been denied

Thanks in advance.

---

### Post by alienexplorers on 2008-05-17
The driver is bad for the 4800 scanner.  You need the libsane-sm3840.so.1.0.15 driver to get it to work.

---

