---
title: "Pendrive xUbuntu Failure to Mount"
date: 2008-03-17
forum: General Help
---

### Post by BugmenotAccount on 2008-03-17
I managed to install a portable version of xUbuntu on a 2 gig pendrive using the following site: [http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

I'm having a problem with some of the computers I am using it on.  I am unable to mount the hard drive.  When I attempt to do so, it tells me that the device cannot mount because it is already mounted under /media/disk.  I checked the /media folder and nothing's there.

Any help?

---

### Post by DoctorMO on 2008-03-17
sounds like a udev / hal problem, can you report back what is reported in dmesg when you plug it in by running dmesg and copying and pasting what gets logged?

---

