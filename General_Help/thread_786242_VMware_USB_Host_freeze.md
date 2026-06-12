---
title: "VMware USB Host freeze"
date: 2008-05-07
forum: General Help
---

### Post by MikeKnoop on 2008-05-07
Hey,

I'm attempting to get a recent VMWare installation (VMWare server 1.05 running WinXP Pro) to recognize a USB device. I followed the USB steps in this post:

[http://ubuntuforums.org/showthread.php?t=779934&highlight=ubuntu+vmware+XP+usb](http://ubuntuforums.org/showthread.php?t=779934&highlight=ubuntu+vmware+XP+usb)

However, whenever I click on the device in the "VM -> removable devices" menu, the host completely locks up.

Specifically, the device I'm trying to add is the Dazzle DVC-80 USB video input adapter. It is recognized under Ubuntu and even halfway works (LED on device lights up when in use) however video is not displayed (I think I have the wrong chipset in the device from what the driver [usbvision] uses) so I thought I'd try VMWare.

Other USB devices, such as an external harddrive add properly without freezing.

I think it might be a sharing issue, since when I load the external harddrive in VMWare it does not show up in Ubuntu, however the DVC-80 device IS showing up in Ubuntu.

Any thoughts?

-Mike

---

