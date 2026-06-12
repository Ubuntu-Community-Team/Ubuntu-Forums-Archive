---
title: "USB camera flickers after recent update"
date: 2015-07-23
forum: General Help
---

### Post by wurlyfan on 2015-07-23
Hello All.  Since I updated my 14.04 installation yesterday, with the update offered, a USB camera connected to a USB3 port on my desktop (part of a security system) has been flickering repeatedly and occasionally freezing. Prior to the update the camera worked almost perfectly (only very occasional glitches). I notice large numbers of the lines similar to the following in Syslog:

[25505.836900] xhci_hcd 0000:03:00.0: ERROR Transfer event TRB DMA ptr not part of current TD

Are these likely to be related? Is there anything that can be done?

Many thanks for any help

---

### Post by Vladlenin5000 on 2015-07-23
*xhci_hcd* is the driver or part of the driver for USB3.0 so yes, it's related, apparently.
I assume it only happens in a USB3.0 port?...

---

### Post by wurlyfan on 2015-07-24
You're right, problem goes away when I connect the camera to the  front-panel ports, which aren't USB 3.0. Unfortunately, that's not  desirable aesthetically! I read somewhere that there's an upstream  kernel issue with xhci_hcd dating back to 2014, so maybe that just got  rolled out un-fixed. Maybe there's a way to patch it - I'll have to do  some more research. Thanks for your input, please let me know if you  have any ideas.

---

