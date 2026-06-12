---
title: "silicon labs USB/serial failure--fldigi--ttyUSBx--brltty solved"
date: 2022-05-11
forum: General Help
---

### Post by a_hippie on 2022-05-11
Hello hams and non-hams alike

I REALLY hope to find more hams here on the forums.  Lots of trouble with the ham radio software on 22.04 . .

Anyway, been struggling to learn why my TS-590sg no longer had CAT control. The device would be made on boot (/dev/ttyUSB0) then be removed.  I had noted the brltty also mentioned in the logs (/var/log/syslog). . 

Today, helping another ham, I stumbled onto brltty forking up the serial/usb driver with other devices too, not just the silicon labs devices.

Testing to see if I could remove brltty which is a program for blind people to produce braille functionality:

(sudo apt-get remove -s brltty)  >>    This "simulates" what would happen  using the (-s) and my system reports that it would remove the program and it's companion programs only.  

Removed brltty (sudo apt-get remove --purge brltty) >> which removed brltty and a few of it's helper apps.

Rebooted and FINALLY, CAT control is restored.

This will also restore functionality for pat-winlink, js8call, flrig [etc] that need CAT control.

Hope this helps others who've migrated to Ubuntu 22.04.  I migrated from 21.10.  I'll post next issue separately.

Where are the other hams?  Is there another forum for ham related assistance?

Here's my original post:
[https://ubuntuforums.org/showthread.php?t=2474607&p=14094244#post14094244](https://ubuntuforums.org/showthread.php?t=2474607&p=14094244#post14094244)

Tnx all, 73

Jaye ke6sls

---

