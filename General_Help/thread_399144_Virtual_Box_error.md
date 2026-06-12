---
title: "Virtual Box error"
date: 2007-04-01
forum: General Help
---

### Post by billdotson on 2007-04-01
I make a hard disk image to boot the guest OS off of.  I called it Fedora .vmi or whatever the disk image for Virtual Box is and then I told VB to mount the Fedora Core disc 1 .iso on that hard disk image.  It gave me an error so I then tried to mount the KnoppixDVD .iso on that HDD image.  Same error.  Then I tried the Ubuntu desktop .iso.  Same error.

The error is attached in a screenshot.

I have libxalan110, libxerces27, and libstdc++5 installed.

---

### Post by irwa82 on 2007-04-04
Hi,

Make sure that your user is listed under the vboxusers group:

$ cat /etc/group | grep vboxusers

also make sure that you have the vboxdrv loaded

$ /sbin/lsmod | grep vboxdrv

if it does not show up then do

$ sudo /sbin/modprobe vboxdrv

---

