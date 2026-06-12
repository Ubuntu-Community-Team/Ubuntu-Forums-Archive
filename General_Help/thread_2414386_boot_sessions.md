---
title: "boot sessions"
date: 2019-03-09
forum: General Help
---

### Post by j3984 on 2019-03-09
If I get the correct wifi driver in a live session via USB thumb drive and then close out...will the driver be there the next time I do a live session?(not installed).

---

### Post by jeremy31 on 2019-03-09
Not on a Normal Live as they are not persistent

---

### Post by grahammechanical on 2019-03-09
Right or wrong, this is my take on this question:

If WiFi works in a Ubuntu live session, then it would be confirmation that an installed Ubuntu would have the correct wireless drivers for the wireless adapter in the machine.

If WiFi worked in one live session then I can see no reason why it should not work in succeeding live sessions. Unless the WiFi driver was downloaded and installed during the live session.

Linux includes drivers for various items of hardware and has done so for many years. These drivers are part of the ISO image of the live session. Installing Ubuntu with an internet connection will make it possible to update the system as part of the install process. If an item of hardware is not recognized during a live session, I do not think that a driver will be downloaded during the install process. This is why older versions of Ubuntu may not work on newer hardware.

 A few years ago I tried an experiment. I tried installing Ubuntu 7.04 in my machine. I did not expect any problems as 7.04 was the first version of Ubuntu that I ran on this machine. I forgot that I had changed the video card. The Ubuntu 7.04 repositories did not have a graphic driver for the video card that was released some years after 2007.

Regards.

---

### Post by j3984 on 2019-03-09
I guess I will find out.

---

### Post by jdeca57 on 2019-03-09
There exists a usb distribution - Knoppix - that allows keeping persistent data on the usb stick. So if he question is of booting and keeping modifications then that would be a good try.

---

