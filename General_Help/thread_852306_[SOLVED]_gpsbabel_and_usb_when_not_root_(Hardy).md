---
title: "[SOLVED] gpsbabel and usb when not root (Hardy)"
date: 2008-07-07
forum: General Help
---

### Post by barkerben on 2008-07-07
Hi - I am running ubuntu hardy, and I have a garmin Etrex HCx. I can connect to it over usb using gpsbabel, but only when I run the program as root. 

gpsbabel -i garmin -f usb: -o gpx -F test.gpx

usb_set_configuration failed, probably because kernel driver ''
 is blocking our access to the USB device.
For more information see [http://www.gpsbabel.org/os/Linux_Hotplug.html](http://www.gpsbabel.org/os/Linux_Hotplug.html)

Looking at the suggested site, it would seem the problem lies with trying to access usb while not root, but there is nothing specifically for hardy, and so far nothing I have tried has helped. Any ideas out there?

Cheers,

Ben

---

### Post by barkerben on 2008-07-07
Ah - fixed :-)

I found that while the fix suggested for Gutsy on the gpsbabel pages (see link above) failed, that suggested for Dapper seems to have worked fine. I had initially ignored that, assuming the more recent would be more likely to work.

Cheers,

Ben

---

