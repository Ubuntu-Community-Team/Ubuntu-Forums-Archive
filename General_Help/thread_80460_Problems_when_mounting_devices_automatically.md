---
title: "Problems when mounting devices automatically"
date: 2005-10-22
forum: General Help
---

### Post by vsacramento on 2005-10-22
Hi, I've just installed Ubuntu Breezy in a station in my Network, but I've been having problems to mount floppy, Pen drive (usb memory key) via Nautilus.  I had problems in two scenarios:

First: at my PC at home where I have a local user that belongs to plugdev, floppy, cdrom groups. My usb memory key is mounted automatically in the first time with RW rigths, but after umounting it, I cannot mount It again via Nautilus. The program report this error: given UDI is not a mountable volume

Regarding to the floppy disk, I could not even mount it once. I receive the error message: given UDI is not a mountable volume

Second: My PC at work where my user is authenticated via NIS Server (running SLackware).  In this scenario my groups are those sent by NIS Server, so I do not have the plugdev, floppy, and so on. I had to create these groups and join the local uses to them so that the users can have rigths to execut 'pmount-hal' via Nautilus.

I think It would be very interesting if someone add this second scenario in Ubunto documentation making explicity what a network administrator must do when using  nis client in ubuntu linux.

But, I still have problems to mount the floppy and usb memory key (pen drive). I always get the error message: given UDI is not a mountable volume
What should I do to solve this problem?

thanks in advance.
Vagner

---

### Post by hajk on 2005-10-22
Floppy problem seems to be a recent and known bug -- may be we'll get an update via breezy-updates soon. But it is possible in standard Breezy to mount the floppy as user by issuing the command "mount /media/floppy". Unmounting can then take place by clicking the icon and selecting unmount.

The USB stick problem: this one should mount upon insertion; mounting again (after being unmounted) requires reinsertion. I don't know whether this is a bug or not.

---

